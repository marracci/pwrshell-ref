# use this to determine all files in a specific directory that have fully qalified pathnames larger than 260 characters
# works recursively through subdirectories, even those with spaces in directory name
# outputs to a text file in chosen location
# sourced from https://powershell.org/forums/topic/script-to-find-long-path-names/



C:\Users\Username\"directoryName with Spaces" -Recurse -Force -ErrorAction SilentlyContinue |  Where-Object {$_.FullName.Length -gt 260} > 'C:\directoryWhereYouWantOutputText\file-paths-too-long.txt'
