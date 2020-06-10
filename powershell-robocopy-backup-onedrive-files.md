# this script launches robocopy and allows you to backup OneDrive files to an external hard drive
# can set to run automatically via Task scheduler, for instance
# MIR command will delete anything in the desination which does not match source, and write new files
# save this file as a .ps1 to run in powershell


# all of these locations, including Google Drive can be backed up using robocopy directly
# start powershell in your users folder
robocopy ".\Downloads\\" "D:\backup\Downloads\\" /Z /MIR /R:5 /W:5
robocopy ".\Dropbox\\" "D:\backup\Dropbox\\" /Z /MIR /R:5 /W:5
robocopy ".\Google Drive\\" "D:\backup\GoogleDrive\\" /Z /MIR /R:5 /W:5

# however, OneDrive cannot be running while robocopy is attempting to access. 
# shutdown OneDrive to enable robocopy access
C:\Users\USERNAME\AppData\Local\Microsoft\OneDrive\OneDrive.exe /shutdown

# pause command for 30 seconds, giving onedrive enough time to shut down
Start-Sleep -Seconds 30

# use robocopy to backup OneDrive files to your external
robocopy ".\OneDrive\\" "D:\backup\OneDrive\\" /Z /MIR /R:5 /W:5

# after backup completes, you want to re-start OneDrive so you can keep syncing and not forget
# startup OneDrive application
C:\Users\Administrator\AppData\Local\Microsoft\OneDrive\OneDrive.exe


# write yourself a nice message, you ahve completed the backup
Write-Host "Congratulations! Your script executed successfully"
Write-Host "You're a badassmofo."

# pause command for 1 minutes so you can read the oputput
Start-Sleep -Seconds 60
