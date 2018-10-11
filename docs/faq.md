### I am new to Linux / Ubuntu / Debian. I do not understand the instructions
Please see [learning linux](/docs/learning_linux.md)

### 1. What type of questions / issues do NOT belong here (this repository)
Currently this is a one-person project. 
Until and unless the community of participants in this repository grows very large, the following types of questions / issues do NOT belong in this repository:
- General questions about Linux / Ubuntu / Debian
- General questions (not specific to packaging asterisk) related to package management on Ubuntu
- Questions about using these scripts on non-Ubuntu operating systems. **Well-phrased** questions about raspbian, Debian or other Debian alternatives should be OK
- General questions about asterisk - not related to using asterisk to connect to Google Voice
- Questions on using FreePBX or other asterisk GUI front-ends - this repository is specifically related to using asterisk **on the command line by editing configuration files directly**
- Questions on FreeSwitch, PBX-In-A-Flash etc
- Questions on securing asterisk. If the question is very well-phrased, and perhaps includes suggestions you have as an expert in securing asterisk, it could be OK

### 2. What information should I provide when opening an issue
On top of, and independent of instructions below, **you, and you alone** are responsible for making sure you protect the security of your Linux and asterisk installation by making sure you do not leak out security-sensitive information as part of reporting your issue.

**Read that previous line again**

NEVER cut-and-paste or reveal your Google Voice OAuth2 credentials (client_id, client secret, access token, refresh token) to **anyone else** INCLUDING on this repository. 
Revealing your Google Voice OAuth2 credentials can have **SERIOUS** consequences, including financial consequences if you have international dialing with an automatic payment method setup.
Abuse of your Google Voice credentials **could** result in your Google Voice service being disrupted or limited or disabled by Google.

The following information should **normally** not contain any security-sensitive information, and should be included with your issue report:
- The EXACT error message you see, if any
- Contents of /var/log/asterisk/messages - **make sure** you review to make sure there is no security-sensitive information
- Output of ```core reload``` with verbosity set to at least 3 (```core set verbose 3```)
- Contents of ```/etc/asterisk/extensions.conf``` AND any files it includes - **make sure you remove any security-sensitive information**. Normally there should NOT be any security-sensitive information in ```/etc/asterisk/extensions.conf``` or files that it includes

The following information WILL contain security-sensitive information. 
**Make sure** you remove / change all security-sensitive information before including this information with your issue report.
- Contents of ```/etc/asterisk/users.conf``` (if applicable) AND any files it includes - **make sure you change** ```secret=XXX``` lines
- Contents of ```/etc/asterisk/pjsip.conf``` AND any files it includes - **make sure you remove / change ALL parts of your Google Voice OAuth2 credentials - see above.