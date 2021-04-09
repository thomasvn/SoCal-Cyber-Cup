Some resources to help guide you in your SoCal Cyber Cup Challenge


## 1. Cryptography in CTFs (Capture the Flags)
Below are some writeups from previous years' picoCTF.
- https://blog.kuhi.to/picoctf_2019_crypto_writeup
- https://tcode2k16.github.io/blog/posts/picoctf-2018-writeup/cryptography/


## 2. Port Scanning
Use the popular tool `nmap` (https://nmap.org/download.html). USE WITH CAUTION. Do not scan any machine you have not been authorized to scan.

Below is how I would run a scan using the command line tool available in Kali Linux.
```bash
# NMAP FLAGS
# -Pn:          skip pings and assume all hosts are "live"
# --open:       show only hosts and corresponding ports
# -n:           skip DNS resolving
# -vvv:         verbose
# --top-ports:  choose a specific number of high-ratio ports
# -T4:          set timing templates {paranoid|sneaky|polite|normal|aggressive|insane}
# -oA:          outputs in (Normal, XML, greppable)
# -iL:          input file
# -p-:          scan all 65,535 ports
# -A:           Aggressive scan. Enables OS detection, version scanning, script scanning, and traceroute. Good for one-off host scanning

# Discovery Scan (identify hosts within authorized IP range)
echo "10.20.160.20-160" >> scope.txt
nmap -Pn --open -n -vvv --top-ports 15 -T4 -oA discovery -iL scope.txt

# Aggressive Scan (based off the hosts found in the discovery scan)
grep "Status: Up" discovery.gnmap | cut -d " " -f2 > livehosts.txt
nmap -Pn --open -n -vvv -p- -A -T4 -oA aggressive -iL livehosts.txt
```


## 3. Identifying file paths
Understanding your current file path
```bash
# Linux
pwd

# Windows (Command Prompt)
dir

# Windows (Powershell)
pwd
```

Searching for files
```bash
# Linux (across the entire filesystem)
#   Replace `/` with `.` to search current directory
#   filename can be a regular expression (REGEX). For example, *.pdf will find all PDFs.
find / -name filename

# Windows (command prompt) (these commands were found in RFTM)
#   Search for all PDFs
#   Search for all patches
#   Search for files for password
#   Directory listing of C:
dir /a /s /b c:\*.pdf*
dir /a /b c:\windows\kb*
findstr /si password *.txt | *.xml | *.xls
tree /F /A c:\ tree.txt

# Windows (powershell)
#   https://devblogs.microsoft.com/scripting/use-windows-powershell-to-search-for-files/
```


## 4. Command line tips/tricks
RTFM: Red Team Field Manual (https://doc.lagout.org/rtfm-red-team-field-manual.pdf)


## Misc Resources
Learning
- https://ctflearn.com

Tools
- https://gchq.github.io/CyberChef/
- https://www.kali.org/blog/official-kali-linux-docker-images/
