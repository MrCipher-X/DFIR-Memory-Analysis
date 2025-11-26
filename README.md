\# 🧠 Windows Memory Forensics: Cridex Malware Analysis



\### 🔍 Objective

To perform memory forensics on a compromised Windows XP machine using \*\*Volatility 3\*\*, identifying malicious processes and code injection techniques. This simulates a Tier 2 SOC Analyst investigation into an endpoint compromise.



\### 🛠️ Tools Used

\* \*\*Volatility 3:\*\* Memory extraction and analysis framework.

\* \*\*Command Line:\*\* PowerShell for execution.



\### 📊 Key Findings

1\.  \*\*Suspicious Process:\*\* Identified `reader\_sl.exe` (PID 1640).

2\.  \*\*Parent Process Analysis:\*\* Launched by `explorer.exe` (PID 1484), indicating user interaction (not a background update).

3\.  \*\*Code Injection Confirmed:\*\*

&nbsp;   \* Used `windows.malfind` to analyze memory sections.

&nbsp;   \* \*\*Finding:\*\* PID 1640 contained a memory region with \*\*PAGE\_EXECUTE\_READWRITE (RWX)\*\* permissions.

&nbsp;   \* \*\*Artifact:\*\* The region started with the \*\*MZ header\*\* (4D 5A), confirming a hidden PE executable was injected into the process memory.



\### 📸 Evidence

\*\*Malfind Output showing RWX permissions and MZ Header:\*\*

!\[Malfind Evidence](malfind\_evidence.png)



\### 🛡️ Conclusion

The process `reader\_sl.exe` is compromised. It is likely a hollowed process hosting the "Cridex" banking trojan. Immediate containment (Network isolation) would be the recommended response.



