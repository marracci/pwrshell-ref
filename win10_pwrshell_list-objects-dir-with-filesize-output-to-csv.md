# this will itemize all files within a directory and subdirs
# get size in kilobytes
# and write full pathname for each file with filesize
# output to a csv


$size = @{label="Size(KB)";expression={$_.length/1KB}}
get-childitem C:\folder -rec | where {!$_.PSIsContainer} |
select-object FullName, $size | export-csv -notypeinformation -path file.csv