# Introduction

Having GIT installed is asummed and implied.<br/>
To install any modules from the terminal, run the preferred version as an administrator. <br/>
This terminal setup is built using my own preferences and includes all the modules I personally use, to achieve my day to day terminal experience. <br/><br/>
To find the Windows JSON settings file, navigate to:

```
%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\
```

# Powerline setup
Credit and more details <a style="text-decoration: none" href = "https://www.hanselman.com/blog/how-to-make-a-pretty-prompt-in-windows-terminal-with-powerline-nerd-fonts-cascadia-code-wsl-and-ohmyposh" target="_blank">here.</a>
This is a `powerline` setup based on `Posh` modules. Instalation, fonts and preferences can be found below. <br/>

## Posh
From the terminal, install the following two Posh based modules:
```
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```

Run `notepad $profile` from the terminal and add the following lines to the end of the file (the first time, allow the notepad prompt to create the file):
```
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt -Theme {DESIRED THEME}
```
All `oh-my-posh` themes for this integration can be found <a href="https://ohmyposh.dev/docs/themes" style="text-decoration: none" target="_blank">here.</a><br/>
As of the last commit date, my desired theme is `star` (star.omp.json).

## Powerline font
My desired powerline fonts will be provided inside the repos `powerlineFonts` folder.
Add a powerline font to the OS `fonts` folder, then default the font from inside the Windows terimal settings:
  - start => run => fonts => paste font file (.ttf)
  - open JSON settings for the Windows terminal => defaults => font => paste the font name

## Powerline theme modifications
Type just `$profile` inside the terminal to view the `oh-my-posh` directory for any powerline specific JSON theme changes. Find the JSON file of the desired theme, and start modifying. For any of my desired themes, view the JSON theme settings provided in the repos `powerlineThemeSetups` folder.

For me, as of the last commit date, the themes folder is at:<br/>
```
C:\Users\Samir\Documents\WindowsPowerShell\Modules\oh-my-posh\3.144.0\themes
```

# Get-ChildItemColor
Credit and more details <a style="text-decoration: none" href = "https://github.com/joonro/Get-ChildItemColor" target="_blank">here.</a>

From the terminal, install the following module:
```
Install-Module -AllowClobber Get-ChildItemColor
```

Run `notepad $profile` from the terminal and add the following lines to the end of the file (the first time, allow the notepad prompt to create the file):
```
Import-Module Get-ChildItemColor
$GetChildItemColorTable.File['Directory'] = "DarkBlue"
$Global:GetChildItemColorVerticalSpace = 0
```
Modifications to the directory colors, new lines via vertical space etc, can be done with the last two lines of code above.<br/>
To find all available colors, view the Windows `Console.ForegroundColor` property and its `System.ConsoleColor` attribute. More details provided <a style="text-decoration: none" href = "https://docs.microsoft.com/en-us/dotnet/api/system.console.foregroundcolor?view=net-6.0" target="_blank">here.</a>

# PSReadLine

Credit and more details <a style="text-decoration: none" href = "https://github.com/PowerShell/PSReadLine" target="_blank">here.</a>

From the terminal, install the following module:
```
Install-Module PSReadLine
```

Run `notepad $profile` from the terminal and add the following lines to the end of the file (the first time, allow the notepad prompt to create the file):
```
Import-Module PSReadLine
Set-PSReadLineOption -Colors @{ InlinePrediction = '#6d778c'}
Set-PSReadLineOption -PredictionSource History
```
Modifications to the prediction line colors and source can be done with the last two lines of code above.

# Terminal setup
Open the Windows terminal JSON settings, and paste the attached `windowsTerminalSettings/settigns.json` configuration. All explanations will be provided inside the JSON file.