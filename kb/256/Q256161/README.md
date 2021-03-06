---
layout: page
title: "Q256161: HOWTO: Get PCMCIA Socket Information"
permalink: /kb/256/Q256161/
---

## Q256161: HOWTO: Get PCMCIA Socket Information

{% raw %}

	Article: Q256161
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): kbDDK kbOSWin2000 kbPlugPlay kbDSupport kbGrpDSNTDDK kbWDM
	Last Modified: 13-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows XP Driver Development Kit (DDK) 
	- Microsoft Windows 2000 Driver Development Kit (DDK) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to get PCMCIA socket information, such as the number
	of slots on the reader or the slot number of the currently inserted card device.
	
	MORE INFORMATION
	================
	
	The following sample code uses the PCMCIA_SOCKET_INFORMATION structure that is
	defined in the Ntddpcm.h header file:
	
	  typedef struct _PCMCIA_SOCKET_INFORMATION {
	     USHORT  Socket;
	     USHORT  TupleCrc;
	     UCHAR   Manufacturer[MANUFACTURER_NAME_LENGTH];
	     UCHAR   Identifier[DEVICE_IDENTIFIER_LENGTH];
	     UCHAR   DriverName[DRIVER_NAME_LENGTH];
	     UCHAR   DeviceFunctionId;
	     UCHAR   Reserved;
	     UCHAR   CardInSocket;
	     UCHAR   CardEnabled;
	     ULONG   ControllerType;
	  } PCMCIA_SOCKET_INFORMATION, *PPCMCIA_SOCKET_INFORMATION;
	
	The sample code performs the following steps:
	
	1. Uses the IoGetDeviceObjectPointer function to obtain the device object and
	  corresponding file object.
	
	2. Initializes the PCMCIA_SOCKET_INFORMATION structure for the socket for which
	  the information is sought.
	
	3. Uses the IoBuildDeviceIoControlRequest function to allocate and set up an I/O
	  request packet (IRP) for a device control request (the
	  IOCTL_SOCKET_INFORMATION structure). This request should be sent at
	  PASSIVE_LEVEL to the PCMCIA bus driver.
	
	4. Passes the IRP down and waits for the result.
	
	If the return status is success, the information in the PCMCIA_SOCKET_INFORMATION
	structure is valid and can be used in your driver. Repeat steps 1 to 4 for all
	the controllers present on your computer.
	
	Here is the sample code:
	
	  {
	      ANSI_STRING ntString;
	      UNICODE_STRING ntUnicodeString;
	      KEVENT event;
	      PDEVICE_OBJECT PcmciaDeviceObject = NULL;
	      NTSTATUS istatus = 0;
	      PFILE_OBJECT fileObject = NULL;
	      PIRP irp = NULL;
	      LONG SktNo = 0;
	      LONG ValidSkts = 0;
	      PCMCIA_SOCKET_INFORMATION PcmciaSkt;
	      IO_STATUS_BLOCK ioStatusBlock;
	      CCHAR deviceNameBuffer[64];
	      LONG portNumber = 0;
	      LONG MorePorts = TRUE;
	      LONG MoreSkts = TRUE;
	
	      //Loop for all the controllers.
	      do{
	          sprintf(deviceNameBuffer,"\\Device\\Pcmcia%d",portNumber);
	  	RtlInitAnsiString(
	                            &ntString,
	                            deviceNameBuffer
	                           ); //Initialize the string
	          istatus = RtlAnsiStringToUnicodeString(
	                                               &ntUnicodeString,
	                                               &ntString,
	                                               TRUE
	                                              );
	          if (!NT_SUCCESS(istatus)){
	              //Handle this error properly.
	              return STATUS_UNSUCCESSFUL; //Error
	          }//ENDIF
	          status = IoGetDeviceObjectPointer(
	                                            &ntUnicodeString,
	                                            FILE_READ_ATTRIBUTES,
	                                            &fileObject,
	                                            &PcmciaDeviceObject
	                                           );
	          if (!NT_SUCCESS(istatus)){
	              return STATUS_UNSUCCESSFUL; //Error
	          }//ENDIF
	          do{
	              RtlZeroMemory(
	                            &PcmciaSkt,
	                            sizeof(PCMCIA_SOCKET_INFORMATION)
	                           );
	              PcmciaSkt.Socket = (USHORT) SktNo;
	              KeInitializeEvent(&event, NotificationEvent, FALSE);
	              irp = IoBuildDeviceIoControlRequest
	                          (
	                           IOCTL_SOCKET_INFORMATION,
	                           PcmciaDeviceObject,
	                           &PcmciaSkt,
	                           sizeof(PCMCIA_SOCKET_INFORMATION),
	                           &PcmciaSkt,
	                           sizeof (PCMCIA_SOCKET_INFORMATION),
	                           FALSE,
	                           &event,
	                           &ioStatusBlock
	                          );
	
	              if (!irp){
	                  //Handle the error properly.
	                  MoreSkts = FALSE;
	                  break; //Error
	              }//ENDIF
	
	              ioStatusBlock.Status = STATUS_NOT_SUPPORTED;
	              ioStatusBlock.Information = 0;
	
	              // Send the request down.
	              istatus = IoCallDriver(
	                                    PcmciaDeviceObject,
	                                    irp
	                                   );
	              if (istatus == STATUS_PENDING){
	              // If pending then wait for done.
	                  KeWaitForSingleObject(
	                                        &event,
	                                        Executive,
	                                        KernelMode,
	                                        FALSE,
	                                        NULL
	                                       );
	                  istatus = ioStatusBlock.Status;
	              }//ENDIF
	              if (!NT_SUCCESS(istatus)){
	                  //The error can occur for many reasons including the
	                  //STATUS_INVALID_PARAMETER,STATUS_BUFFER_TOO_SMALL 
	                  //if the parameters in the IoBuildDevice.... function
	                  //are not valid.
	
	                  //If the error is because of invalid parameter then, 
	                  //it could be because there may not be more valid socket 
	                  //on this controller. In this case just break see if 
	                  //any other controller exists.
	                  //Otherwise handle the error carefully.    
	
	                  MoreSkts = FALSE;
	                  break;
	              }//ENDIF
	              //You have the socket information now to handle in your driver.
	              SktNo++;
	          }while (MoreSkts)//END FOR
	          //Dereference the file object on this controller.
	          ObDereferenceObject(fileObject);
	          portNumber++;
	          //Here before reinitializing the flag you can insert your code.
	          MoreSkts = TRUE;
	      }while(MorePorts)//END WHILE
	      MorePorts = TRUE;
	  }
	
	The PcmciaSkt.CardInSocket value is TRUE when a card is present in the socket,
	and the PcmciaSkt.Socket value provides the socket number. For all invalid
	parameters, including SktNo, the underlying driver returns
	STATUS_INVALID_PARAMETER.
	
	REFERENCES
	==========
	
	The Ntddpcm.h file is located under the Ddk\Inc folder.
	
	Additional query words: Pcmcia
	
	======================================================================
	Keywords          : kbDDK kbOSWin2000 kbPlugPlay kbDSupport kbGrpDSNTDDK kbWDM 
	Technology        : kbwin2000Search kbwin2000DDK kbAudDeveloper kbWinDDKSearch kbWinDDK kbWinXPDDKSearch
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
