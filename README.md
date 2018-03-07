# shibbopy
A py simple page to be installed in ISS to catch and display the SAML Token returned by an IDP <br />
1. Install the correction version of shibboleth sp (x86 or x64) from here https://shibboleth.net/downloads/service-provider/2.6.1/ <br />
2. On the Default website of IIS, add Handler Mappings -> Script Map : Request Path = *.sso, Executable = <path to isapi_shib.dll>. Uncheck the "Invoke handler..." <br />
3. Create an application under the default website of IIS and point to the *.py page. <br />
4. On the application created at step 3, add Handler Mappings -> Module Mapping : Request Path = *, Module = FastCgiModule, Executable = C:\Python3\python.exe|c:\inetpub\wwwroot\flaskshib\wfastcgi.py. Uncheck the "Invoke handler..." <br />
5. Go to this page to register your SP with Shibboleth IDP test server : https://www.testshib.org/register.html. On Windows, the metadata can be found in C:\opt\shibboleth-sp\etc\shibboleth <br />
6. Browse the application in IIS, you should be invited to type in your authentication on Shibbo login page and get redirect to the py page which should show the token content.