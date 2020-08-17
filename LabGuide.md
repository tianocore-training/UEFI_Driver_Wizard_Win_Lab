## Slide 1
# UEFI & EDK II Training

## UEFI Driver Wizard Lab - Windows
<br>
<a href='http://www.tianocore.org'>tianocore.org</a>

<!---
 Lab_Guide.md for UEFI Driver Wizard Win Lab

  Copyright (c) 2020, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

-->


---  
## Slide 2 @title[Lesson Objective]

### Lesson Objective 

- Setup the UEFI Driver Wizard
- Create a UEFI Driver Template


---
## Slide 3 @title[UEFI Driver Wizard Section]

### UEFI Driver Wizard

Creating a Template UEFI Driver with the UEFI Driver Wizard

---

## Slide 4 @title[UEFI Driver Wizard Overview]

### UEFI Driver Wizard Overview

- Open source tool
- Based on Driver Writer’s Guide for UEFI 2.3.1 content
- Intel SSG engineers contributed
- Located on http://www.TianoCore.org 


---

## Slide 5 @title[Installing UEFI Driver Wizard]

### Installing UEFI Driver Wizard

#### Requirements and Options

- info - Work space  must contain BaseTools, MdePkg & MdeModulePkg Packages from latest stable tag from https://github.com/tianocore/edk2 for Driver development on Tianocore.org 

- For this lab use previous lab’s setup w/ Windows C:\FW\edk2-ws\

- info - Python* scripts from  [Github Link](https://github.com/tianocore/edk2-share/tree/master/DriverDeveloper/UefiDriverWizard) then use instructions from README for Python and wxPython versions to install then run
```
	 bash$ python launch.py
```

---

## Slide 6 @title[Requirements for Your Driver]

### Requirements for Your Driver

Using UEFI Driver Wizard

- UEFI Device Driver
- UEFI Version 2.7 (0x00020046)  
```
	#define EFI_2_70_SYSTEM_TABLE_REVISION ((2<<16) | (70DEC)) 
```
- Unloadable driver
- Support IA32 & x64 CPUs
- Returns component name information
- Byte stream device (i.e.UART / Serial I/O)
- Option to produce HII strings & forms for setup


---

## Slide 7 @title[Template File Contents]

### Template File Contents

#####  Proper UEFI driver entry point

##### Basic driver libraries/headers


##### Skeletons for common driver functions


##### Error values until portedEFI_UNSUPPORTED, EFI_DEVICE_ERROR

Note:

The driver wizard will create all the c and .h files for a template UEFI driver


- Establishes a proper UEFI Driver Entry Point
- References to basic driver libraries/headers based on Driver Wizard form input
- Inserted in .INF, .H and .C files
- Skeletons for common driver functions
- Includes comments based on information from the Driver Writer’s Guide for UEFI 2.3.1
- Functions may return error values until ported (EFI_UNSUPPORTED, EFI_DEVICE_ERROR)

---

## Slide 8 @title[Lab 1: Create a UEFI Driver with the UEFI Driver Wizard]

### Lab 1: Create a UEFI Driver with the UEFI Driver Wizard

- In this lab, you'll create a new UEFI driver using the UEFI Driver Wizard.
- This will create a set of "c" code files to be used as a template UEFI Driver used in the subsequent driver labs


---

## Slide 9 @title[Lab 1: Install UEFI Driver Wizard]

### Lab 1: Install UEFI Driver Wizard

First setup for Building EDK II for Emulator, See [Lab Setup](https://gitpitch.com/tianocore-training/Platform_Build_Win_Emulator_Lab/master#/9)

Install UEFI Driver Wizard from the downloaded lab material
Open and Run  `/FW/DriverWizard/UefiDriverWizard.msi`
Click through “Next” until install finishes

Open the UEFI Driver Wizard


---

## Slide 10 @title[Lab 1: UefiDriverWizard -Select Work Space]

### Lab 1: UefiDriverWizard -Select Work Space

- Open source tool
- Based on Driver Writer’s Guide for UEFI 2.3.1 content
- Intel SSG engineers contributed
- Located on http://www.TianoCore.org 


Click on File and Select 

“Open WORKSPACE”

  Or 

Control+<u>O</u>  

- Browse to `C:/FW/edk2-ws/edk2` 
- Select  “OK”
- Should say 
“`WORKSPACE C:\FW\edk2-ws\edk2 selected`”


Note: the environment for EDK II must be setup with edksetup.bat 

---

## Slide 11 @title[Lab 1: Create a New UEFI Driver]

### Lab 1: Create a <u>N</u>ew UEFI Driver

Control+<u>N</u> – to Open Menu 

---

## Slide 12 @title[Lab 1:New UEFI Driver Menu]

### Lab 1:New UEFI Driver Menu

- UEFI Driver Path” – Type: “MyWizardDriver” <br>
   - Note:  “UEFI Driver Name” is filled in. 
   - Also if the "UEFI Driver path" is not filled in, an error will occur.
- Ensure all the forms, radio buttons, and boxes are filled in and selected exactly like the image to the right (except GUID) from slide 12 of the PDF for this lab
   - Fill in "UEFI Driver Version
   - Select "UEFI Driver Model Device Driver"
   - Fill in "Driver Binding Version" with the value 0x0000000A
   - Select the following "Optional Features Commmon to all UEFI Driver Types"
      - "Unloadable"
      - "Driver Supported EFI version Protocol"
      - "HII Packages for String, Fonts, or Images"
   - Fill in "UEFI Specification Version" with the value of 0x00020046
   - Select the following for "CPU Architectures":
      - IA32
      - X64



Note:  A new, specific driver GUID will populate, so it will be different than this image


Click on the `Next>>` button

---

## Slide 13 @title[Lab 1: UEFI Driver Model Optional Features]

### Lab 1: UEFI Driver Model Optional Features

Ensure all the forms, radio buttons, and boxes are filled in and selected exactly like the image to the right from slide 13 of the PDF for this lab

Select the following on the "UEFI Driver Optional Features" menu
-  "Component Name 2 Protocol”
-  "Component Name Protocol”
-  "HII Packages for Forms . . .”

Click on the `Next>>` button

---

## Slide 14 @title[Lab 1: UEFI Driver Consumed Protocol]

### Lab 1: UEFI Driver Consumed Protocol

Select  
-  “PCI Driver that consumes the PCI I/O Protocol”

Click on the `Next>>` button

---

## Slide 15 @title[Lab 1: UEFI Driver Produced Protocol]

### Lab 1: UEFI Driver Produced Protocol

Select  
-  "Byte stream device (i.e.UART)   
      producing Serial I/O Protocol"


Click on the `Finish` button

---

## Slide 16 @title[Lab 1: UEFI Driver Created]

### Lab 1: UEFI Driver Created

UEFI Driver template created

The UEFI Driver Wizard will show several files that it created in the dialog window.

Note: if an error occurs, make sure you have given it a file path from Slide 12

---
---  
## Slide 17 @title[Lesson Summary]

### Lesson Summary

- Setup the UEFI Driver Wizard
- Create a UEFI Driver Template


---
## SLide 18 @title[Questions]

![Questions](/assets/images/questions.JPG) 

---
## Slide 19


Return to Training Table of contents for next presentation link: https://github.com/tianocore-training/Tianocore_Training_Contents/wiki



---
## Slide 20 @title[Logo Slide]
<br><br><br>



---
## SLide 21 @title[Acknowledgements]
### Acknowledgements


```
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2020, Intel Corporation. All rights reserved.
**/

```
