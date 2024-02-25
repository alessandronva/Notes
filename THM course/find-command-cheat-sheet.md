# "find" Command Cheat Sheet

This cheat sheet provides basics for using the `find` command in Linux, particularly useful for ethical hacking purposes.

### Finding Files by Name

find /path/to/search -name filename

### Finding Files by Extension

find /path/to/search -name "\*.extension"

### Finding Files by Type

find /path/to/search -type f

### Finding Directories

find /path/to/search -type d

### Finding Files Based on Modification Time

find /path/to/search -mtime +7

### Finding Files Based on Size

find /path/to/search -size +1M

### Finding Files Owned by a Specific User

find /path/to/search -user username

### Finding Files with Specific Permissions

find /path/to/search -perm 644

### Combining Multiple Criteria

find /path/to/search -name "\*.conf" -user root

### Executing Commands on Found Files

find /path/to/search -name "\*.txt" -exec grep "keyword" {} ;

### Excluding Certain Directories

find /path/to/search -name "_.log" -not -path "./excluded\_dir/_"

### Finding SUID/SGID Files

find /path/to/search -type f -perm /6000

### Finding Files with Specific Content

find /path/to/search -type f -exec grep -l "pattern" {} +
