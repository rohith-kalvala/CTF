To open dir buster in GUI format ran below command
```
┌──(kali㉿kali)-[~]
└─$ dirbuster&
[1] 117179

```

Performing directory brute-force scan using DirBuster tool 
![[Pasted image 20260322204344.png|601]]
As the webserver is running apache : I added php extension we can also add txt, docx, pdf or any other files it is going to take time for processing. 


**Results** 
```
DirBuster 1.0-RC1 - Report
http://www.owasp.org/index.php/Category:OWASP_DirBuster_Project
Report produced on Sun Mar 22 11:47:05 EDT 2026
--------------------------------

http://192.168.232.129:80
--------------------------------
Directories found during testing:

Dirs found with a 200 response:

/
/icons/
/manual/
/manual/mod/
/usage/
/icons/small/
/mrtg/
/manual/mod/mod_perl/
/manual/mod/mod_ssl/

Dirs found with a 403 response:

/doc/
/cgi-bin/


--------------------------------
Files found during testing:

Files found with a 200 responce:

/test.php
/usage/usage_202603.html
/usage/usage_200909.html
/mrtg/mrtg.html
/mrtg/unix-guide.html
/mrtg/nt-guide.html
/mrtg/indexmaker.html
/mrtg/cfgmaker.html
/mrtg/forum.html
/mrtg/contrib.html
/mrtg/mrtg-rrd.html
/mrtg/logfile.html
/mrtg/mibhelp.html
/mrtg/squid.html
/mrtg/webserver.html
/mrtg/faq.html
/mrtg/reference.html
/manual/mod/mod_ssl/ssl_overview.html
/manual/mod/mod_ssl/index.html
/manual/mod/mod_ssl/ssl_howto.html
/manual/mod/mod_ssl/ssl_compat.html
/manual/mod/mod_ssl/ssl_intro.html
/manual/mod/mod_ssl/ssl_glossary.html
/manual/mod/mod_ssl/ssl_faq.html
/manual/mod/mod_ssl/ssl_reference.html


--------------------------------

```
