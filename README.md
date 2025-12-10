# Advanced Static Malware Analysis – IDA Pro (CY3002 Project)

This repository contains the complete static analysis of multiple malware samples using **IDA Pro** as part of the course **Vulnerability Assessment & Reverse Engineering (CY 3002)** at FAST NUCES.  
The analysis was performed by **Sumera Malik (I21-1579)**.

The project includes detailed inspection of binary structure, imports, exports, functions, DLL dependencies, suspicious API usage, and behavioral insights for each malware sample.

---

## 📌 Malware Samples Analyzed

This project includes deep static analysis of the following malware families:

1. **Gen: Heur.PonyStealer.4**  
2. **Trojan.GenericKD.3652107 26**  
3. **Password-Stealer (003bbfec1)**  
4. **W32.SecretKAN.Trojan**

Each sample is examined with respect to:

- PE file segments/sections  
- Imported API functions  
- Exported functions  
- Control flow graphs  
- Language constructs  
- DLL dependencies  
- Suspicious functionality  
- Behavioral insights  
- Potential malicious actions

---

## 🧩 1. Gen: Heur.PonyStealer.4

### 🔹 Segments & Sections  
The malware includes typical `.text`, `.rdata`, `.data` sections analyzed through IDA.

### 🔹 Imports  
The binary imports standard Windows library functions, used to perform data theft and credential harvesting.

### 🔹 Exports  
Minimal or no exports, typical for malware loaders and stealers.

### 🔹 Functions  
Multiple functions were identified related to credential access, system queries, and environment enumeration.

### 🔹 Language Constructs & Control Flow  
IDA’s graph view revealed branching logic and routines associated with credential-stealing behavior.

### 🔹 Suspicious Functionality  
Malware used DLLs such as:  
- **VBA6.dll** – to execute VBA macros  
- **msvbvm60.dll** – support for Visual Basic 6 code  

These indicate the malware is likely written in **VB6** and focuses on credential exfiltration.

---

## 🧩 2. Trojan.GenericKD.3652107 26

### 🔹 Segments  
Executable sections showed typical trojan-like structure.

### 🔹 Imports  
Included functions from:  
- `KERNEL32.dll`  
- `USER32.dll`  
- `SHELL32.dll`  
Used commonly for persistence, UI manipulation, or execution.

### 🔹 Functions  
Functions observed included cookie checks, timezone info extraction, and thread synchronization.

### 🔹 Suspicious Behavior  
- Extracting **TimeZoneInformation**  
- Using **EnterCriticalSection**  
- Bypassing security checks  
These behaviors match trojan persistence and anti-analysis techniques.

---

## 🧩 3. Password-Stealer (003bbfec1)

### 🔹 Imports & Functions  
Malware imports networking, file system, and credential-related APIs.

### 🔹 Notable Behavior  
- Connects to C2 server:  
  `http://reninparwil[.]com/zapoy/gate[.]php`
- Uses **GetTickCount** for anti-debugging, timing, and polymorphism.
- Searches for stored login information.

### 🔹 DLL Dependencies  
Highlighted libraries include:  
- `wininet.dll` – HTTP communication  
- `netapi32.dll` – network operations  
- `userenv.dll` – user profile access  

This confirms password-stealing behavior and remote data exfiltration.

---

## 🧩 4. W32.SecretKAN.Trojan

### 🔹 Imports  
Uses APIs such as:  
- `GetCommandLineW`  
- `CommandLineToArgW`  
Used for parsing execution arguments (common for trojans).

### 🔹 DLL Usage  
Includes:  
- `shell32.dll` – executes shell commands  
- `kernel32.dll` – low-level functions  
- `OLE32.dll` – object manipulation, possible RCE vectors  

### 🔹 Suspicious Actions  
Manipulates processes, executes commands, interacts with UI, and may escalate privileges.

---

## 🛠 Tools Used

- **IDA Pro**  
- **Windows PE Analysis**  
- **Control Flow Graphing (CFG)**  
- **Static Reverse Engineering Techniques**  

---

## 🧾 Documentation Included

The project includes a **27-page PDF** detailing:

- Screenshots from IDA  
- Section-level analysis  
- Flow of functions  
- Suspicious API details  
- DLL dependency breakdown  
- Behavioral analysis  
- Malware family comparison  

---

## ⚠️ Ethical Disclaimer

This analysis was performed strictly for **academic and research purposes** on controlled malware samples.  
Handling malware outside a sandbox or secure lab environment is dangerous and illegal.

---

## 👩‍💻 Author

**Sumera Malik**  
Roll No: **I21-1579**  
Course: Vulnerability Assessment & Reverse Engineering (CY3002)

