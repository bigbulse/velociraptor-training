# ℹ Mespinoza/Pysa Ransomware Intell

The Mespinoza ransomware was first used around October 2018. The first versions of Mespinoza encrypted files and used the ".locked" extension for the encrypted files (common to most ransomwares). However, since around December of 2019 a new version of Mespinoza became documented in open sources called Pysa. This version locks encrypted files behind the ".pysa" extension.

### Analysis of the Different Versions

There are two versions of the Mespinoza/Pysa ransomware attack. One is deployed by a **Windows executable file** named "svchost.exe". There are many .bat scripts that come with this executable file which would copy the executable to "C:\windows\temp", which is not a legitimate location for that executable (the real one) to be ran. The second version is a **Python archive** called "17535.pyz" which contains the Python source code of the ransomware.

| Filename    | SHA-1                                    | Size (in Bytes) |
| ----------- | ---------------------------------------- | --------------- |
| svchost.exe | 52b2fc13ec0dbf8a0250c066cd3486b635a27827 | 516608          |
| 17535.pyz   | c74378a93806628b62276195f9657487310a96fd | 279590          |

The **Windows Executable** version of this ransomware variant drops and runs a script called "update.bat" which purpose is to delete the executable file after it executes. The ransomware will also generate many different system artifacts. First it will create a Mutex (Mutual Exclusion Object) named "Pysa". Then, registry key "SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" is modified by the ransomware so the following entries are added.

```powershell
legalnoticetext = [Ransom demand message]

legalnoticecaption = PYSA
```

Lastly, the encryption list contains targeted file extensions along with another list to be avoided for encryption like crucial OS files (":\Windows" for example). The files that are encrypted by this version of Mespinoza/Pysa will carry the ".pysa" extension.

The **Python Archive** version of this ransomware works a bit differently as it is made of a "run.py" file which contains the ransomware configuration such as the RSA public key for encryption, demand message, and variable that allows choice of the extension of the encrypted files. The current version has the variable contained the value ".pysa". Python libraries "pyaes" and "rsa" are also in this archive which are in charge of the encryption function of the ransomware. The "run.py" Python script also contains the instructions to delete the ransomware files after execution and encryption.

There is also a third version of the ransomware consisting of two **PowerShell scripts**, "step1.ps1" and "step2.ps1". "step1.ps1" gets a list of files of the system it is ran on minus the critical directories and files. These files are then base-64 encoded separated by a "|" character to be given as a parameter for the "step2.ps1" script.

For the "step2.ps1" to run, the "step1.ps1" script must create a copy of powershell.exe called "EnNoB-**X**.exe" where **X** is a random integer between 1000-9876. In the "step1.ps1" script, the path of "step2.ps1" on the victim's machine is contained which is why the hash is always different for the first PowerShell script.

The "step2.ps1" PowerShell script encrypts files passed in its parameter. It uses a public RSA key that it has and uses the AES-CBC algorithm to encrypt the files. A list of file extensions are once again used so that the script avoids encrypting any crucial files needed for the OS to run. In this version of Mespinoza/Pysa ransomware, encrypted files by default hold the ".newversion" extension which can be modified in the script that is ran. Lastly, the "step2.ps1" script is also responsible for deleting the copy of "powershell.exe" that was used to execute the scripts.

| Filename  | SHA-1                                    | Size (in Bytes) |
| --------- | ---------------------------------------- | --------------- |
| step1.ps1 | N/A                                      | 12066           |
| step2.ps1 | 24c592ad9b21df380cb4f39a85d4375b6a8a6175 | 4869            |

### Ransom Demand Messages

Although there is no proof that the versions of this ransomware are leveraged by the same intrusion set, similarities can be found in their ransom demand files. All versions of this ransomware create the same ransom demand file which is in the form of a pop-up window with a "Readme.README" file for the first, and "RECOVER_\__YOUR\_DATA.txt" for the second.

The ransomware's demand messages are written in English, but do contain grammatical mistakes. All messages contain the identical "To get all your data back contact us:" string. One of the messages contains an offer to decrypt up to two files for proof of good faith.

Lastly, all the ransom messages contain **ProtonMail** email addresses that are generated from randomly chosen names. Note that all versions of the ransom messages contain the same email addresses.&#x20;

### Possible Features of this Ransomware

One of the ".bat" scripts that was dedicated to executing the PowerShell scripts name "p.ps1" on machines before executing and spreading the ransomware on the network had caused these following affects to machines.

* Stopping antivirus services, uninstalling **Windows Defender**
* Deleting all restore points or shadow copies
* Modified "README" files to allow for double-click opening
* Broadcasting the MAC address of the machine over port 7
* Local account passwords modified

The script was most likely used to improve the stealth of the execution of the ransomware.

This following binary was found on several of the compromised machines.

| SHA-1                                    | Size (in Bytes) |   |
| ---------------------------------------- | --------------- | - |
| f2dda8720a5549d4666269b8ca9d629ea8b76bdf | 5207040         |   |

This file was found under multiple different legitimate file names like "explorer.exe". The binary is a remote access tool written in the "Go" language. A characteristic of this is the logging in plaintext in the file "%TEMP%\hlog.log"

**Source:** ["Attacks Involving the Mespinoza/Pysa Ransomware" by ANSII](https://www.cert.ssi.gouv.fr/uploads/CERTFR-2020-CTI-003.pdf)
