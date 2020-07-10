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
Invoke-WebRequest https://raw.githubusercontent.com/FiskDk/discord-security-exploiting/master/windows_preload.js -OutFile mainScreenPreload.js
cd C:\Users\f1sk\AppData\Roaming\discord\0.0.*\modules\discord_desktop_core
if (test-path "core.asar") { rename-item "core.asar" "core.old" }
npx asar pack rd core.asar
Remove-Item -Recurse -Force "rd"
echo "You can now launch Discord - Thanks for installing Disco-RD <3 - if you need help - contact me f1sk#3621 on Discord"
<3 - you can close this now
```
