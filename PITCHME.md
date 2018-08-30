---?image=assets/images/gitpitch-audience.jpg
@title[UEFI_Driver_Wizard_Win_Lab]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI Driver Wizard Lab - Windows

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Driver Wizard Win Lab

  Copyright (c) 2018, Intel Corporation. All rights reserved.<BR>

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



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Setup the UEFI Driver Wizard</span></li><br>
 <li>@fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Create a UEFI Driver Template</span> </li>
</ul>


---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Driver Wizard Section ]
<br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Driver Wizard</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Creating a Template UEFI Driver with the </span><br>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Driver Wizard</span>



---?image=/assets/images/slides/Slide4.JPG
@title[UEFI Driver Wizard  Overview]
<br>
<p align="left"><span class="gold" ><b>UEFI Driver Wizard  Overview</b></span></p>
<br>
<div class="left1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><font color="cyan">&check;&nbsp;&nbsp;Open source tool  </font> </span>  </li>
  <li><span style="font-size:0.8em" ><font color="white">&check;&nbsp;&nbsp;Based on Driver Writer’s Guide for UEFI 2.3.1 content</font> </span>  </li>
  <li><span style="font-size:0.8em" ><font color="cyan">&check;&nbsp;&nbsp;Intel engineers contributed   </font> </span>  </li>
  <li><span style="font-size:0.8em" ><font color="white">&check;&nbsp;&nbsp;Located on <a href="http://www.tianocore.org">www.TianoCore.org</a>  </font> </span>  </li>
</ul>
</div>
<div class="right1">
  <span style="font-size:0.8em" > &nbsp;&nbsp;</span> 
</div>

Note:

---?image=/assets/images/slides/Slide5.JPG
@title[Installing UEFI Driver Wizard]
<p align="right"><span class="gold" ><b>Installing UEFI Driver Wizard</b></span></p>
<span style="font-size:01.0em" ><font color="#92D050">Requirements and Options </font></span><br>
<br>
<ul style="list-style-type:disc">
  <li><span style="font-size:0.8em" >Work space  must contain BaseTools, MdePkg & MdeModulePkg Packages from <a href="https://github.com/tianocore/tianocore.github.io/wiki/Driver-Developer">UDK2018</a> for Driver development on Tianocore.org </span> </li>
  <li><span style="font-size:0.8em" >Uses previous lab’s setup w/ Windows  `C:/FW/src/edk2`   </span> </li>
  <li><span style="font-size:0.8em" >For Linux, Python scripts from  <a href="https://github.com/tianocore/edk2-share/tree/master/DriverDeveloper/UefiDriverWizard">Github Link </a> then use instructions from README for Python and wxPython versions to install then run</span> </li>
  <ul style="list-style-type:none">
    <li><span style="font-size:0.6em" >&nbsp;&nbsp;<span style="background-color: #101010">`bash$ python launch.py`</span> </span></li>
  </ul>
</ul>

Note:

Same as slide


---?image=/assets/images/slides/Slide6.JPG
@title[Requirements for Your Driver ]
<br>
<p align="center"><span class="gold" ><b>Requirements for Your Driver </b></span></p>
<span style="font-size:0.9em" >Using UEFI Driver Wizard</span>
<ul>
   <li><span style="font-size:0.7em" >UEFI Device Driver </span></li>
   <li><span style="font-size:0.7em" >UEFI Version 2.7 (0x00020046) </span><br><span style="font-size:0.6em" >`#define EFI_2_70_SYSTEM_TABLE_REVISION ((2<<16) | (70DEC))` </span></li>
   <li><span style="font-size:0.7em" >Unloadable driver </span></li>
   <li><span style="font-size:0.7em" >Support IA32 & x64 CPUs </span></li>
   <li><span style="font-size:0.7em" >Returns component name information </span></li>
   <li><span style="font-size:0.7em" >Test console device </span></li>
   <li><span style="font-size:0.7em" >Option to produce strings & forms for setup  </span></li>
</ul>

Note:


---?image=/assets/images/slides/Slide7.JPG
<!-- .slide: data-transition="none" -->
@title[Template File Contents]
<p align="right"><span class="gold" ><b>Template File Contents </b></span></p>

Note:
- Establishes a proper UEFI Driver Entry Point
- References to basic driver libraries/headers based on Driver Wizard form input
- Inserted in .INF, .H and .C files
- Skeletons for common driver functions
- Includes comments based on information from the Driver Writer’s Guide for UEFI 2.3.1
- Functions may return error values until ported : (EFI_UNSUPPORTED, EFI_DEVICE_ERROR)



+++?image=/assets/images/slides/Slide8.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Template File Contents 02]
<p align="right"><span class="gold" ><b>Template File Contents </b></span></p>

Note:
- Establishes a proper UEFI Driver Entry Point
- References to basic driver libraries/headers based on Driver Wizard form input
- Inserted in .INF, .H and .C files
- Skeletons for common driver functions
- Includes comments based on information from the Driver Writer’s Guide for UEFI 2.3.1
- Functions may return error values until ported : (EFI_UNSUPPORTED, EFI_DEVICE_ERROR)


+++?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Template File Contents 03]
<p align="right"><span class="gold" ><b>Template File Contents </b></span></p>

Note:
- Establishes a proper UEFI Driver Entry Point
- References to basic driver libraries/headers based on Driver Wizard form input
- Inserted in .INF, .H and .C files
- Skeletons for common driver functions
- Includes comments based on information from the Driver Writer’s Guide for UEFI 2.3.1
- Functions may return error values until ported : (EFI_UNSUPPORTED, EFI_DEVICE_ERROR)


+++?image=/assets/images/slides/Slide10.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Template File Contents 04]
<p align="right"><span class="gold" ><b>Template File Contents </b></span></p>

Note:
- Establishes a proper UEFI Driver Entry Point
- References to basic driver libraries/headers based on Driver Wizard form input
- Inserted in .INF, .H and .C files
- Skeletons for common driver functions
- Includes comments based on information from the Driver Writer’s Guide for UEFI 2.3.1
- Functions may return error values until ported : (EFI_UNSUPPORTED, EFI_DEVICE_ERROR)


---?image=/assets/images/slides/Slide11.JPG
@title[Lab 1: Create a UEFI Driver section]
<br>
<br>
<p align="Left"><span class="gold" ><b>Lab 1: Create a UEFI Driver with the UEFI Driver Wizard </b></span></p>
<br>
<div class="left1">
<ul>
  <li><span style="font-size:0.8em" >In this lab, you'll create a new UEFI driver using the UEFI Driver Wizard.</span></li>
  <li><span style="font-size:0.8em" >This will create a set of "c" code files to be used as a template UEFI Driver used in the subsequent driver labs</span></li>

</ul>
</div>
<div class="right1">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
 
Note:


---?image=/assets/images/slides/Slide12.JPG
@title[Lab 1: Install UEFI Driver Wizard ]
<p align="right"><span class="gold" ><b>Lab 1: Install UEFI Driver Wizard</b></span></p>
<span style="font-size:0.8em" >First setup for building EDK II for Nt32, See <a href="https://gitpitch.com/Laurie0131/Platform_Build_LAB/master#/2">Lab Setup</a>  </span></li>
<div class="left1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" >Install UEFI Driver Wizard</span></li><br>
  <li><span style="font-size:0.7em" >1. <b>Open</b> and <b>Run</b><br>&nbsp;&nbsp;&nbsp;</span><span style="font-size:0.5em" >`/FW/DriverWizard/UefiDriverWizard.msi`</span></li>
  <li><span style="font-size:0.7em" >2. <b>Click </b> through "Next" until install finishes</span></li><br><br>
  <li><span style="font-size:0.8em" ><b>Open</b> the UEFI Driver Wizard</span></li>
</ul>
</div>
<div class="right1">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
Note:

same as slide


---?image=/assets/images/slides/Slide13.JPG
@title[Lab 1: UefiDriverWizard -Select Work Space]
<p align="right"><span class="gold" ><b>Lab 1: UEFI Driver Wizard -Select Work Space</b></span></p>
<div class="left2">
<ul style="list-style-type:none" style="line-height:0.7;">
   <li><span style="font-size:0.7em" >Click on <b>File</b> and Select <br>“Open WORKSPACE” </span></li>
   <li><span style="font-size:0.7em" >&nbsp;&nbsp;&nbsp;&nbsp;OR</span></li>
   <li><span style="font-size:0.7em" >Control+<u>O</u><br><br></span></li>
   <li><span style="font-size:0.7em" ><b>Browse</b> to `C:/FW/edk2`</span></li>
   <li><span style="font-size:0.7em" ><b>Select</b> "`OK`"</span></li>
   <li><span style="font-size:0.7em" >Should say</span><span style="font-size:0.5em" > "`WORKSPACE C:/FW/edk2 selected`"</span></li><br><br>
</ul>
<p style="line-height:80%"><span style="font-size:0.5em" ><b>Note:</b> the environment for EDK II must be setup with `edksetup.bat` </span></p>
</div>
<div class="right1">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>


Note:


- Click on File and Select 
- “Open WORKSPACE”
-    Or 
- Control+O  

- Browse to C:/FW/edk2 
- Select  “OK”
- Should say “WORKSPACE C:\FW\edk2 selected

- another note, the environment for EDK II must be setup with edksetup.bat 


---?image=/assets/images/slides/Slide14.JPG
@title[Lab 1: -Create a New UEFI Driver]
<p align="center"><span class="gold" ><b>Lab 1: Create a <u>N</u>ew UEFI Driver</b></span></p>
<br>
<span style="font-size:0.8em" >Control+<u>N</u> - to Open Menu</span>
Note:
- Control+N – to Open Menu 


---?image=/assets/images/slides/Slide15.JPG
@title[Lab 1: New UEFI Driver Menu]
<p align="left"><span class="gold" ><b>&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp; &nbsp;Lab 1:</b></span></p>
<p align="left"><span class="gold" ><b>New UEFI Driver Menu</b></span></p>
<div class="left1">
<ul style="list-style-type:disc">
  <li><span style="font-size:0.7em" >“UEFI Driver Path” – Type: <b>“MyWizardDriver”</b></span>  </li>
    <ul style="list-style-type:none">
     <li><span style="font-size:0.5em" >&nbsp;&nbsp;<i>Note:</i> “UEFI Driver Name” is filled in </span>  </li>
  </ul>
 <li><span style="font-size:0.7em" ><b>Ensure</b> all the forms, radio buttons, and boxes are filled in and <b>selected exactly</b> like the image to the right.</span>  </li>
 <br>
 <li><span style="font-size:0.65em" ><i>Note:</i>A new, specific driver GUID will populate, so it will be different than this image</span>  </li>
   <br>
  <ul style="list-style-type:none">
       <li><span style="font-size:0.8em" >&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp; &nbsp; <b>Click</b>  </li>
  </ul>
</ul>
</div>
<div class="right1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" >&nbsp;  </li>
</ul>
</div>

Note:
- “UEFI Driver Version” – Type: “1.0”
- “UEFI Driver Type” – Select: “UEFI Driver Model Device Driver”
- “Opetional Features …” – Select:
  - 	Unloadable
  - 	Driver Supporte EFI Version Protocol
  - 	HII Packages for Strings, Fonts, or images
- “CPU Architecture” – Select: “IA32” and “X64”





---?image=/assets/images/slides/Slide16.JPG
@title[Lab 1: UEFI Driver Model Optional Features]
<p align="right"><span class="gold" ><b>Lab 1: UEFI Driver Model Optional Features</b></span></p>
<div class="left1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><b>Ensure</b> all the forms, radio buttons, and boxes are filled in and <b>selected exactly</b> like the image to the right.</span>  </li>
  <br>
  <li><span style="font-size:0.6em" >&check;&nbsp;&nbsp;"Componnt Name 2 Prorocol”  </span>  </li>
  <li><span style="font-size:0.6em" >&check;&nbsp;&nbsp;"Componnt Name Prorocol”   </span>  </li>
  <li><span style="font-size:0.6em" >&check;&nbsp;&nbsp;"HII Packages for Forms . . .”  </span>  </li>
  <br>
  <br>
  <br>
  <br>
  <li><span style="font-size:0.8em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp;&nbsp;&nbsp; &nbsp; &nbsp; <b>Click</b>  </li>
 </ul>
</div>
<div class="right1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" >&nbsp;  </li>
</ul>
</div>

Note:

- UEFI Driver Model Opetional Features  – Select:
  -	Componnt Name 2 Prorocol
  -	Componnt Name 2 Prorocol
  -	HII Packages for Forms and HII based configuruation





---?image=/assets/images/slides/Slide17.JPG
@title[Lab 1: UEFI Driver Consumed Protocol]
<br>
<p align="left"><span class="gold" ><b>Lab 1: UEFI Driver Consumed Protocol</b></span></p>
<span style="font-size:0.8em" ><b>Select</b></span> <br>
<span style="font-size:0.7em" >&check;&nbsp;&nbsp;"PCI Driver that consumes the PCI I/O Protocol”  </span>  
<div class="left1">
<ul style="list-style-type:none">
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <li><span style="font-size:0.8em" >&nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; <b>Click</b>  </li>
</ul>
</div>
<div class="right1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" >&nbsp;  </li>
</ul>
</div>

Note:

Same as slide





---?image=/assets/images/slides/Slide18.JPG
@title[Lab 1: UEFI Driver Produced Protocols]
<p align="right"><span class="gold" ><b>Lab 1: UEFI Driver Produced Protocols</b></span></p>
<br>
<div class="left1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" ><b>Select</b></span>  </li>
  <li><span style="font-size:0.7em" >&check;&nbsp;&nbsp;"Byte stream device (i.e.UART) &nbsp; <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; producing Serial I/O Protocol”  </span>  </li>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <li><span style="font-size:0.8em" >&nbsp;&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp;&nbsp;&nbsp; &nbsp; &nbsp; <b>Click</b>  </li>
</ul>
</div>
<div class="right1">
<ul style="list-style-type:none">
  <li><span style="font-size:0.8em" >&nbsp;  </li>
</ul>
</div>

Note:

Same as slide



---?image=/assets/images/slides/Slide19.JPG
@title[Lab 1: UEFI Driver Created]
<br>
<p align="left"><span class="gold" ><b>Lab 1: UEFI Driver Created</b></span></p>
<span style="font-size:0.8em" > UEFI Driver template created</span>

Note:

Same as slide

---  
@title[Summary]
<BR>
### <p align="center"><span class="gold"   >Summary </span></p><br>
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Setup the UEFI Driver Wizard</span></li><br>
 <li>@fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Create a UEFI Driver Template</span> </li>
</ul>


 

---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
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

Copyright (c) 2018, Intel Corporation. All rights reserved.
**/

```
