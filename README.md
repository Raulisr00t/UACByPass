# UACByPass
## Overview
This project demonstrates a UAC (User Account Control) bypass technique on Windows systems using COM interfaces and Process Environment Block (PEB) masquerading. The code exploits the ICMLuaUtil interface for privilege elevation by invoking a hidden COM method to run executables with administrative rights without triggering UAC prompts. The project includes the use of undocumented Windows internals, specifically the MasqueradePEB() function, which alters the process's identity to deceive the operating system into treating it as a trusted process.

## Components
ucmAllocateElevatedObject: Uses the CoGetObject function to create an elevated COM object. This object uses the ICMLuaUtil interface to request elevated permissions.
ucmCMLuaUtilShellExecMethod: Executes an application with elevated privileges by calling the ShellExec method within the ICMLuaUtil interface.
MasqueradePEB: Modifies the Process Environment Block (PEB) to change the process's identity, making it appear as explorer.exe to bypass UAC. This is achieved by altering various Unicode strings within the process's memory, mimicking the appearance of explorer.exe.

## Usage
Clone this repository and open the project in Visual Studio or another C++ IDE.
Compile the project to produce the executable.
Run the compiled executable to trigger the UAC bypass, launching a cmd.exe instance with administrative privileges.

### Functions and Methodology
PEB Masquerading: MasqueradePEB() emulates the PEB structure of explorer.exe to make the COM object treat it as a trusted Windows process.
COM Elevation: The project leverages COM to create an elevated ICMLuaUtil instance, which allows it to run executables as Administrator.

### Note: This project is for educational purposes only. Unauthorized usage or redistribution could be illegal and violate software policies. Always seek permission before testing this code on any system other than your own.

## References
This implementation is inspired by:

Bypass-UAC.ps1 from FuzzySecurity
UACME by hFireF0X
