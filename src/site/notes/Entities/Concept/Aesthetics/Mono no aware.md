---
{"dg-publish":true,"dg-path":"Entities/Concepts/Aesthetics/Mono no aware.md","permalink":"/entities/concepts/aesthetics/mono-no-aware/","title":"Mono no aware","tags":["concept","concept/aesthetics","concept/literature","concept/art"]}
---


test note 101
  
Last Command Executed :

- NTUSER.DAT/Software/Microsoft/Windows/CurrentVersion/Explorer/RunMRU
- Commands typed into the RUN box

RecentApps Key - GUI Program Execution :

- NTUSER.DAT/Software/Microsoft/Windows/CurrentVersion/Search/RecentApps
- Track GUI-based program execution launched in win10
- RecentItems ( subkey of RecentApps ) : track most recently opened files by that application
- APPID : name of the app
- LastAccessTime : Last Execution time in UTC
- LaunchCount : Number of Times executed

UserAssist Key :

- NTUSER.DAT/Software/Microsoft/Windows/CurrentVersion/Explorer/UserAssist/{GUID}/Count :
    
- GUID for XP/Vista :
    
- 5e6ab780 : Internet Tollbar
    
- 75048700 : Active Desktop
    
- GUID for WIN7 and Higher :
    
- CEBFF5CD : Executable File Execution
    
- F4E57C4B : Shortcut File Execution
    

Application Compatibility Cache ShimCache :

- XP : System/CurrentControlSet/Control/SessionManager/Appcompatibility/AppcompatCache
    
- Srv 2003/2008/2012 - win7/10 : System/CurrentControlSet/Control/SessionManager/AppcompatCache/AppcompatCache
    
- Check if application need to be 'shimmed' to run application on currentOS or via older OS parameters .
    
- Track the exe file's last modif date , file path , and if it was executed.
    
- If file content was updated/renamed -> app is shimmed again ( new entry in reg )
    
- Insertflag :
    
- True : executed
    
- False : not executed
    

Amcache.hve :

- C:\windows\appcompact\Programs\Amcache.hve (win7/8/10 and srv 2012/2016 )
- Keys : amcache.hve\Root\File{Volume GUID} #####
- Entry for every executable run
- First run time = last modification time of key
- SHA1 hash of executable also contained in the key
- Note : Unlike UserAssit we can't attribut execution to a specific user ( to be researched more)

BAM : Background/desktop activity moderator :

- Used for "connected standby' application throttling and utilization to save battery power
- SYSTEM/CurrentControlSet/Services/bam/UserSettings/{SID}
- SYSTEM/CurrentControlSet/Services/dam/UserSettings/{SID}
- Win10 only
- Provide Full path of the Exe
- Last execution date

Powershell execution ( History ) :

Users > 'username' > AppData > Roaming > Microsoft > Windows > PowerShell > PSReadLine > ConsoleHost_history.txt

MS Defender Detection History :

- Program Data > Microsoft > Windows Defender > Scans > History > Service > DetectionHistory >