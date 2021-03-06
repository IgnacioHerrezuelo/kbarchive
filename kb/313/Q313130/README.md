---
layout: page
title: "Q313130: HOWTO: Retrieve @@IDENTITY Value Using JDBC"
permalink: /kb/313/Q313130/
---

## Q313130: HOWTO: Retrieve @@IDENTITY Value Using JDBC

{% raw %}

	Article: Q313130
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 
	Operating System(s): 
	Keyword(s): kbJDBC kbDSupport kbSQLServ2000 kbSQLServSearch kbAudDeveloper kbHOWTOmaster kbSystemDa
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SQL Server 2000 Driver for JDBC 
	- Microsoft SQL Server 2000 (all editions) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When connected to a Microsoft SQL Server database, you can use the @@IDENTITY
	value to return the last-inserted identity value. This article contains a code
	sample that demonstrates how to retrieve this value in a Java application that
	uses the Microsoft SQL Server 2000 Driver for JDBC.
	
	MORE INFORMATION
	================
	
	The code sample in this article illustrates two different methods to retrieve
	the @@IDENTITY value with JDBC.
	
	- 
	
	  Method 1:
	
	  Use a stored procedure that performs an INSERT into a table, and then returns
	  the @@IDENTITY value as an output parameter. Output parameters from a stored
	  procedure are not available until all of the resultsets have been processed.
	  As soon as the resultset from the stored procedure has been fetched, the
	  output value of this procedure will contain the @@IDENTITY value.
	
	- 
	
	  Method 2:
	
	  Submit a batch query that contains a SELECT @@IDENTITY statement to retrieve
	  the @@IDENTITY value. As the resultsets from the batch are processed, the
	  @@IDENTITY values are available as a column of a resultset.
	
	NOTE: The code in this article is set up to use a stored procedure by default.
	See the comments in the code for the lines that have to be uncommented to use
	the batch statement instead.
	
	Steps to Run the Sample Code
	----------------------------
	
	1. Use the following SQL code to create the sample table and stored procedure in
	  your SQL Server database:
	
	  CREATE TABLE myIdentTable (col1 int NOT NULL IDENTITY(1,1), col2 varchar(20))
	  GO
	
	  CREATE PROCEDURE myIdentProc (@ident INT OUTPUT, @cvalue varchar(20))
	  AS
	  INSERT INTO myIdentTable (col2) VALUES (@cvalue)
	  SELECT @ident = @@IDENTITY
	  GO
	
	2. Copy the following sample code into a new Java source file:
	
	  import java.sql.*; 
	  import java.io.*; 
	
	  public class IdentitySample
	  {
	  	public static void main(String args[])
	  	{
	  		try
	  		{
	  			String URL = "jdbc:microsoft:sqlserver://yourServer:1433;databasename=pubs";
	  			String userName = "yourUser";
	  			String password = "yourPassword";
	  		
	  			System.out.println( "Trying to connect to: " + URL); 
	
	  			//Register JDBC Driver
	  			Class.forName("com.microsoft.jdbc.sqlserver.SQLServerDriver").newInstance();
	
	  			//Connect to SQL Server
	  			Connection con = null;
	  			con = DriverManager.getConnection(URL,userName,password);
	  			System.out.println("Successfully connected to server"); 
	  			
	  			//Create statement and Execute using either a stored procecure or batch statement
	  			CallableStatement callstmt = null;
	  			
	  			//Using a stored procedure
	  			callstmt = con.prepareCall("{call myIdentProc(?,?)}");
	  			callstmt.registerOutParameter(1, java.sql.Types.INTEGER);
	  			callstmt.setString(2, "testInputProc");
	  			System.out.println("Stored procedure successfully executed");
	  			callstmt.execute();
	  			
	  			//OR 
	  			
	  			//Using a batch statement directly
	  			/*
	  			callstmt = con.prepareCall("INSERT INTO myIdentTable (col2) VALUES (?);SELECT @@IDENTITY");
	  			callstmt.setString(1, "testInputBatch");
	  			System.out.println("Batch statement successfully executed"); 
	  			callstmt.execute();
	  			*/ 
	  					
	  			int iUpdCount = callstmt.getUpdateCount();
	  			boolean bMoreResults = true;
	  			ResultSet rs = null;
	  			int myIdentVal = -1; //to store the @@IDENTITY
	  			
	  			//While there are still more results or update counts
	  			//available, continue processing resultsets
	  			while (bMoreResults || iUpdCount!=-1)
	  			{			
	  				//NOTE: in order for output parameters to be available,
	  				//all resultsets must be processed
	  				
	  				rs = callstmt.getResultSet();
	  				
	  				//Use the following if using the batch statement instead of the stored procedure
	  				//if rs is not null, we know we can get the results from the SELECT @@IDENTITY
	  				/*
	  				if (rs != null)
	  				{
	  					rs.next();
	  					myIdentVal = rs.getInt(1);
	  				}
	  				*/ 
	  				
	  				
	  				//Do something with the results here (not shown)
	
	  				//get the next resultset, if there is one
	  				//this call also implicitly closes the previously obtained ResultSet
	  				bMoreResults = callstmt.getMoreResults();
	  				iUpdCount = callstmt.getUpdateCount();
	  			}
	  			//Use the following if using the stored procedure
	  			//retrieve the @@IDENTITY here because we know all results have been processed,
	  			//comment out when using batch
	  			myIdentVal = callstmt.getInt(1);
	  			
	  			System.out.println( "@@IDENTITY is: " + myIdentVal);		
	  			
	  			//Close statement and connection 
	  			callstmt.close();
	  			con.close();
	  		}
	  		catch (Exception ex)
	  		{
	  			ex.printStackTrace();
	  		}
	  		
	  		try
	  		{
	  			System.out.println("Press any key to quit...");
	  			System.in.read();
	  		}
	  		catch (Exception e)
	  		{
	  		}
	  	}
	  }
	
	3. Change the URL, the username, and the password variables to reference
	  appropriate connection information for your SQL Server.
	
	4. Compile and run the sample.
	
	5. The output should look similar to the following:
	
	  Trying to connect to:
	  jdbc:microsoft:sqlserver://yourServer:1433;databasename=pubs
	  Successfully connected to server
	  Stored procedure successfully executed
	  @@IDENTITY is: 1
	  Press any key to quit..
	
	On subsequent executions, the identity value increments by one each time the
	program runs.
	
	REFERENCES
	==========
	
	For more information about the @@IDENTITY value, see SQL Server Books Online.
	
	Additional query words: autonumber autoincrement
	
	======================================================================
	Keywords          : kbJDBC kbDSupport kbSQLServ2000 kbSQLServSearch kbAudDeveloper kbHOWTOmaster kbSystemData 
	Technology        : kbSQLServSearch kbAudDeveloper kbSQLServ2000Search kbSQLServ2000 kbSQLServJDBC
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
