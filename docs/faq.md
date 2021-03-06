### 1. I am new to Linux / Ubuntu / Debian. I do not understand the instructions
Please see [learning linux](/docs/learning_linux.md)

### 2. I am new to asterisk. I do not understand the instructions / advice
Please see [learning asterisk](/docs/learning_asterisk.md)

### 3. I am new to git or I want to learn more about git
Please see [learning git](/docs/learning_git.md)

### 4. What type of questions / issues do NOT belong here (this repository)
The following types of questions / issues do **NOT** belong in this repository:
- General questions about Linux / Ubuntu / Debian
- General questions (not specific to packaging asterisk) related to package management on Ubuntu
- Questions on using FreePBX or other asterisk GUI front-ends - this repository is specifically related to using asterisk **on the command line by editing configuration files directly**
- Questions on FreeSwitch, PBX-In-A-Flash etc
- Questions on securing asterisk. If the question is very well-phrased, and perhaps includes suggestions you have as an expert in securing asterisk, it could be OK
- Using this repository and / or installing and using asterisk on operating systems other than Linux - including Windows, MacOS. The scripts in this repository most certainly will **NOT** work on BSD systems, but well-phrased uestions on asterisk on BSD systems are welcome
- Questions about connecting to Google Voice using an Obihai device - for this go to [Obitalk forums](https://www.obitalk.com/forum/) or Google is your friend.
- Questions about how to use github - see [connecting to github with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/) and [cloning with SSH URLs](https://help.github.com/articles/which-remote-url-should-i-use/#cloning-with-ssh-urls)
- General questions about using git.

Currently this is a one-person project. 
Until and unless the community of participants in this repository grows very large, the following types of questions / issues do **NOT** belong in this repository:
- Questions about using these scripts on non-Ubuntu operating systems. **Well-phrased** questions about raspbian, Debian or other Debian alternatives should be OK
- General questions about asterisk - not related to using asterisk to connect to Google Voice
- Questions on codecs - which codec to use, which is the best codec for a situation, codec translation tables etc
- Questions on migrating from chan_sip to chan_pjsip - I provide some links from the asterisk wiki in [links.md](/docs/links.md). That is the extent of my knowledge.
- Questions on using SIP (chan_sip or chan_pjsip) over TLS with SRTP / ZRTP etc (other than Google Voice). I provide some links in [links.md](/docs/links.md). That is the extent of my knowledge.
- Using features such as conference rooms, MeetMe, FollowMe, agents, IVR in asterisk. I have not used these features and will probably not be able to help.
- SIP clients on operating systems other than Linux / Android. This does not mean that SIP clients on such operating systems, such as Windows / MacOS will not work - it is just that I use only Linux and do not have any knowledge about these other operating systems.
- Which SIP / IAX client should I use. I provide some links in [links.md](/docs/links.md)
- Questions about using a Dahdi card and / or Mobile (GSM) Dongle - I do not have much experience with this.
- Using ACL with asterisk - I do not know much about this, but if there are other participants in this repository, you are welcome to ask

## 5. How do I create an issue on github?
See [creating an issue](https://help.github.com/articles/creating-an-issue/)

## 6. How do I create a pull request on github?
See [create a pull request](https://services.github.com/on-demand/github-cli/open-pull-request-github)

### 7. What information should I provide when opening an issue
On top of, and independent of instructions below, **you, and you alone** are responsible for making sure you protect the security of your Linux and asterisk installation by making sure you do not leak out security-sensitive information as part of reporting your issue.

**Read that previous line again**

**NEVER** cut-and-paste or reveal your Google Voice OAuth2 credentials (client_id, client secret, access token, refresh token) to **anyone else** INCLUDING on this repository. 
Revealing your Google Voice OAuth2 credentials can have **SERIOUS** consequences, including financial consequences if you have international dialing with an automatic payment method setup.
Abuse of your Google Voice credentials **could** result in your Google Voice service being disrupted or limited or disabled by Google.

The following information should **normally** not contain any security-sensitive information, and should be included with your issue report:
- The **EXACT** error message you see, if any
- Output of ```pjsip show registrations``` if relevant
- Output of ```iax2 show peers``` if relevant
- Output of ```module show``` if relevant
- Contents of /var/log/asterisk/messages - **make sure** you review to make sure there is no security-sensitive information
- Output of ```core reload``` with verbosity set to at least 3 (```core set verbose 3```)
- Contents of ```/etc/asterisk/extensions.conf``` AND any files it includes - **make sure you remove any security-sensitive information**. Normally there should NOT be any security-sensitive information in ```/etc/asterisk/extensions.conf``` or files that it includes
- Public keys (certificates) can be shared if relevant - these usually do not contain any security-sensitive information

The following information **WILL** contain security-sensitive information that you **MUST** remove / change. 
**Make sure** you remove / change all security-sensitive information before including this information with your issue report.
- Contents of ```/etc/asterisk/users.conf``` (if applicable) AND any files it includes - **make sure you change** ```secret=XXX``` lines
- Contents of ```/etc/asterisk/pjsip.conf``` AND any files it includes - **make sure you remove / change ALL parts of your Google Voice OAuth2 credentials - see above.

The following information should **NEVER** be shared with your issue report:
- Any private keys, including:
    - CA private key - even if encrypted
    - Host private key - even if encrypted
    - Client private key - even if encrypted
- Contents of ```/etc/manager.conf``` or any file it includes - without removing ```secret```
- Contents of ```/etc/asterisk/acl.conf``` or any file it includes

## 8. Can I submit a pull request containing external links to books, guides, HOWTOs, courses etc to help people learn about asterisk, Linux, github etc?
Such pull requests are welcome. For my policies on external links, see [external links](/docs/external_links.md)

## 9. Why doesn't your repository contain a pre-compiled DEB file?
- github does not support or encourage uploading of large / binary artifacts
- If you use a DEB file, you will not have a ready-made way to upgrade to future saterisk versions, unless I keep providing DEBs of future asterisk vesions. That makes you perpetually dependent on this repository and my DEBs
- Using binary compiled DEB files from providers you do not know is a very risky activity
- Once you have compiled asterisk from source once - using my scripts - the DEB file will be automatically created. You can download this DEB file and add it to your cloned repo, and it will be used if you use the scripts in your cloned repo again - e.g. for another asterisk instance. You can also maintain TWO SD cards - one with the asterisk source and one with asterisk installed from DEB. You can (if you porefer) run asterisk normally using the SD card with asterisk installed from DEB. When you want to download / install future asterisk versions (from naf419's repository), you can put in the other SD card, compile, build and test asterisk, and the new DEB would have been automatically created. No dependence on me or this repo ! My scripts also allow you to download your production asterisk configuration files which will be automatically installed into /etc/asterisk when you compile and install a new asterisk version or install asterisk from DEB. This is my setup - you may have other preferences.
