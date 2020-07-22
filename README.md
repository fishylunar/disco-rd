# Disco-RD 
<img src="https://github.com/FiskDk/disco-rd-client/raw/master/disco-rd.png" width="128">
Multi-platform Discord modification

<details>


  

### Changelog

  

#### Script V2.0

- Fixed errors in the messageEdit module

- added defaultOverlay

- prep work for custom CSS

  

### Features

  

- Custom Dark Discord theme

- Multi platform - (Windows, Web, iPadOS)

- Developer Tools (Disco-RD Studio) (Comming Soon)

- Compatible with BetterDiscord / BandagedBD (Known bugs : exiting setting causes a soft-crash)
  
  

### Screenshots
<details>
	

##### Disco-RD for web - Edge - Disco-RD Script V2

![](https://github.com/FiskDk/disco-rd/blob/master/img/Web-Edge-Disco-RD-Script-2.png)

  

##### Disco-RD for Windows - Core V1.9 - Disco-RD Script V2

![](https://github.com/FiskDk/disco-rd/blob/master/img/Windows-Core-1-9-Disco-RD-Script-2.png)

  

##### Disco-RD for iPadOS - iPadOS 13.4.1 (iPad Air 2) - Disco-RD Script V1.8.2

![](https://github.com/FiskDk/disco-rd/blob/master/img/iPadOS-13-4-1-Disco-RD-Script-1-8-2.png)

  
</details>
  

### Known bugs

- In Server Settings the following things are broken : Members, Invites, Bans

  

## Get Disco-RD

###### Disco-RD is currently still in development. Bugs are to be expected.

### Windows tutorial

* Open a PowerShell CLI by pressing the Windows key + R on your keyboard - then type "powershell" and press enter

* Copy the code below and paste it in the PowerShell window (Windows 10 users can just right click the terminal window after the code is copied.)

* When it says its done, you can go and close the window and launch Discord

If it instantly closes when you run the code, then check if you have NodeJS installed

[NodeJS](https://nodejs.org/en/)

[Install NodeJS without admin permissions](http://abdelraoof.com/blog/2014/11/11/install-nodejs-without-admin-rights/)
  
```powershell
$nodeV = (node -v) | Out-String
if ($nodeV.StartsWith("v")) { echo NodeJS Version : $nodeV } else {exit}
Stop-process -Name discord
cd C:\Users\$env:UserName\AppData\Roaming\discord\0.0.*\modules\discord_desktop_core
if (Test-Path "core.old") { remove-item "core.old" }
if (Test-Path "rd") { remove-item "rd" }
npx asar extract core.asar rd
cd rd\app
remove-item "mainScreenPreload.js"
Invoke-WebRequest https://raw.githubusercontent.com/FiskDk/disco-rd-client/master/windows_preload.js -OutFile mainScreenPreload.js
cd C:\Users\$env:UserName\AppData\Roaming\discord\0.0.*\modules\discord_desktop_core
if (test-path "core.asar") { rename-item "core.asar" "core.old" }
npx asar pack rd core.asar
Remove-Item -Recurse -Force "rd"
echo "You can now launch Discord - Thanks for installing Disco-RD <3 - if you need help - contact me f1sk#3621 on Discord"
<3 - you can close this now
```
### iPadOS Tutorial

  

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

  

[Disco-RD For Web](https://raw.githubusercontent.com/FiskDk/disco-rd-client/master/Disco-RD%20For%20Web.zip)

  

Save the file somewhere and extract it

  

You should now have have a folder structure like this :

  

Dir where you extracted |

- web.zip

- Disco-RD Web

  

If not - make sure you dont extract into another folder (example : dir where you extracted\web\Disco-RD Web

  

Now open your browser again - navigate to "about://extensions" (without the quotes) if you werent there already

  

Now click the "Load unpacked" button and navigate to the folder "Disco-RD Web" - then click select folder

  

Now when you go to Discord in your browser you should see Disco-RD

</details>

# [RDWrapper](https://github.com/FiskDk/RDWrapper)

<img src="https://github.com/FiskDk/RDWrapper/raw/master/RDWrapper.png" width="128">

 Make your own custom Discord client!
 <details>

## How to use : 
Download the RDWrapper folder, then look in the "How To.txt" file - or read it here

### Contents of "How To.txt"
How to use RDWrapper

It's simple
Make a GitHub repo
in your repo you'll need to create 2 files, a JS file, and a CSS file
Write your custom client code in the JS file, and your custom theme/css in the CSS file
Now get your direct links

https://raw.githubusercontent.com/GitHubUserName/RepoName/master/filename

Example :

https://raw.githubusercontent.com/FiskDk/RDWrapper/master/ExampleScript/main.css

Now open RDWrapper.cmd and follow the instructions

# Example Showcase
https://drive.google.com/file/d/1NlfrEdETX1lH1it6IWX2FiSdH2AW4-Ag/view?usp=sharing
</details>

> Disco-RD, RDWrapper, And anything else with the "a part of Disco-RD" branding is not affiliated with Discord.