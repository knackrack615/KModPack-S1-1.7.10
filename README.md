# KModPack-S1-1.7.10
Knackrack's Modded Survival Season 1 [1.7.10]

This is my modded survival pack for minecraft version 1.7.10

It's intended to be used in my private modded server

Its here so i can keep track of mod updates

# Forge Details

Ver: forge-1.7.10-10.13.4.1614-1.7.10

Short: http://tinyurl.com/os9n6cv

Long: http://files.minecraftforge.net/maven/net/minecraftforge/forge/1.7.10-10.13.4.1614-1.7.10/forge-1.7.10-10.13.4.1614-1.7.10-installer.jar

#Installation Instructions
1) Install Forge

2) Download the ModPack Installer from here: https://hgcommunity.net/modpacks/KModPack_S1_1.7.bat

3) Run It


#Batch Script
'''batch
@ECHO off
 ECHO "----------------------"
 ECHO " Knackrack's Mod Pack "
 ECHO "----------------------"
 ECHO.
 ECHO "Updating KMODPACK..."

 SET minecraft_location=C:\Users\%username%\AppData\Roaming\.minecraft
 CD %minecraft_location%
 
 git --version >nul 2>&1 &&(
  ECHO Git found!
 ) || (
  ECHO Error: Could not find GIT!
  ECHO Please download git and try again.
  PAUSE
  EXIT
 )
 

 IF EXIST mods (
  ECHO Mods folder found!
  CD mods
  IF EXIST .git (
   git pull
   ECHO Done!
   GOTO:update_config
  ) ELSE (
   ECHO The mods folder found however its not synced with git. Please delete it and run the update again!
   PAUSE
   EXIT
  )
 ) ELSE (
  ECHO Could not find mods folder. Creating...
  MKDIR mods
  CD mods 
  git clone https://github.com/knackrack615/KModPack-S1-1.7.10.git .
  GOTO:update_config
 )

 :update_config
  ECHO Updating configs...
  CD MOD_CONFIGS
  COPY *.* "%minecraft_location%/config" /Y
  ECHO All configs have been updated!
 
PAUSE
EXIT
'''
