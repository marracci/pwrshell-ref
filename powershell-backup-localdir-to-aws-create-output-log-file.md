# this script will backup files to s3 using awscli and delete s3 objects which do not exist on local directory
# and write a log file detailing all file additions, deletions occurring in the s3 bucket
# awscli must be installed with IAM credentials giving read, write, list, put, delete access to destination bucket
# replace DEVICENAME with your computer name - only for logging purpose
# rename to .ps1



Write-Host "my local to s3 backup script"
Write-Host "second line if you wan tto provide more detail in log output"

# generate filenaming convention for log file
$enddate = (Get-Date).tostring("yyyyMMdd-hh-mm-ss")
$filename = 'MYDEVICENAME_' + $enddate + '_-backup-log'

# will sync local dir to s3 bucket and prefix while deleting any files no longer in local dir from s3 location and write logfile output
aws s3 sync D:\my-local-directory\ s3://bucket/prefix/prefix/ --delete > D:\my-local-directory\log-directory\$filename.txt

# pause command for 5 seconds
Start-Sleep -Seconds 5


Write-Host "Backup script complete"
# pause command for 10 seconds
Start-Sleep -Seconds 10