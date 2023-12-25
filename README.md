# Introduction

Having GIT installed is assumed and implied.<br/>
To install any modules from the terminal, run the preferred version as an administrator. <br/>
This terminal setup is built using my own preferences and includes all the modules I personally use, to achieve my day-to-day terminal experience. <br/><br/>
To find the Windows JSON settings file, navigate to:

```
%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\
```

# Accesing the `$profile`

To add any modules and modifications to the Windows terminal, the `$profile` file must be located first. By typing in `notepad $profile`, the `$profile` file should open automatically. If the `$profile` file does not exist, a prompt will be shown to create the file. This usually happens when the file is accessed for the first time.

## Troubleshooting `$profile`
Sometimes, the operating system will not be able to find the `$profile` file, nor be able to create it on the fist prompt automatically.
In that case, navigate to the `Documents` folder:
```
C:\Users\{USER}\Documents
``` 
There, create the folder named 
```
WindowsPowerShell
```
Inside the folder, create the `$profile` file manually, by adding the file named:
```
Microsoft.PowerShell_profile.ps1
```
After completing this the `notepad $profile` command should work as expected and navigate and open the newly created `$profile` file.


# Powerline setup
This is a `powerline` setup based on `Posh` modules. Installation, fonts and preferences can be found below. <br/>

## Powerline font
My desired powerline fonts will be provided inside the repos `powerlineFonts` folder.
Add a powerline font to the OS `fonts` folder, then default the font from inside the Windows terminal settings:
  - start => run => fonts => paste font file (.ttf)
  - open JSON settings for the Windows terminal => defaults => font => paste the font name

## Posh
From the terminal, install the following Posh-based module:
```
Install-Module posh-git -Scope CurrentUser
```

Run `notepad $profile` from the terminal and add the following line to the end of the file:
```
Import-Module posh-git
```

Next, install the `oh-my-posh` application module from the official <a href="https://apps.microsoft.com/detail/XP8K0HKJFRXGCK?hl=en-US&gl=US" style="text-decoration: none" target="_blank">Microsoft store.</a>

After the installation, a new `POSH_THEMES_PATH` environment variable should be added to the operating systems environment variables, pointing to the `oh-my-posh` themes folder. Check if the variable exists by typing `$env:POSH_THEMES_PATH` inside the terminal. If the variable does not exist, add it by typing the following command inside the terminal:
```
$env:POSH_THEMES_PATH = "C:\Users\{USER}\AppData\Local\Programs\oh-my-posh\themes"
```
This step can also be done by navigating to the Windows environment variables settings and adding the variable manually. Double check the exitance of the themes folder as well.

All `oh-my-posh` themes for this integration can be found <a href="https://ohmyposh.dev/docs/themes" style="text-decoration: none" target="_blank">here.</a><br/>
As of the last commit date, my desired theme is `star` (star.omp.json).

To apply a desired theme to the terminal, run `notepad $profile` from the terminal and add the following line to the end of the file:
```
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\{THEME_NAME}.omp.json" | Invoke-Expression
```

## Powerline theme modifications
Locate the `oh-my-posh` themes directory for any powerline-specific JSON theme changes. Find the JSON file of the desired theme, and start modifying. For any of my desired themes, view the JSON theme settings provided in the repos `powerlineThemeSetups` folder.

The themes folder should be located at the created `$env:POSH_THEMES_PATH` location, being:
```
C:\Users\{USER}\AppData\Local\Programs\oh-my-posh\themes
```

# Get-ChildItemColor
Credit and more details <a style="text-decoration: none" href = "https://github.com/joonro/Get-ChildItemColor" target="_blank">here.</a>

From the terminal, install the following module:
```
Install-Module -AllowClobber Get-ChildItemColor
```

Run `notepad $profile` from the terminal and add the following lines to the end of the file:
```
Import-Module Get-ChildItemColor
$GetChildItemColorTable.File['Directory'] = "DarkBlue"
$Global:GetChildItemColorVerticalSpace = 0
```
Modifications to the directory colors, new lines via vertical space etc, can be done with the last two lines of code above.<br/>
To find all available colors, view the Windows `Console.ForegroundColor` property and its `System.ConsoleColor` attribute. More details are provided here.</a>

# PSReadLine

Credit and more details <a style="text-decoration: none" href = "https://github.com/PowerShell/PSReadLine" target="_blank">here.</a>

From the terminal, install the following module (the `-Force` flag will override the default Windows `ReadLine` behavior):
```
Install-Module PSReadLine -Force
```

Run `notepad $profile` from the terminal and add the following lines to the end of the file:
```
Import-Module PSReadLine
Set-PSReadLineOption -Colors @{ InlinePrediction = '#6d778c'}
Set-PSReadLineOption -PredictionSource History
```
Modifications to the prediction line colors and source can be done with the last two lines of code above.

# Terminal setup
Open the Windows terminal JSON settings, and paste the attached `windowsTerminalSettings/settigns.json` configuration. All explanations will be provided inside the JSON file.

