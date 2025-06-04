Unfortunately, I had a commitment at 8 PM and could only attempt the CTF for around 45 minutes, these are the problems I was able to attempt and solve.

# Binary Directory
## Observations
Directory contained paths that resembled binary encoded text, at the end of each nested directory, a text file with a single character was present. Most files contained the character 0 but some appeared to be different. I figured that the paths of the different files would have the code in binary encoding.

## Solution
Wrote a python script to loop through the directory structure and print the path of the tof files containing `1` sorted alphabetically.

```python
import os
L= []
def list_files_recursive(path='.'):
    for entry in os.listdir(path):
        full_path = os.path.join(path, entry)
        if os.path.isdir(full_path):
            list_files_recursive(full_path)
        else:
            with open(full_path) as t:
                if t.read() != "0" and "py" not in full_path:
#                    print(full_path[4:].replace("/",""))
#                    print(full_path)
                    L.append(full_path)
#            print(full_path)

# Specify the directory path you want to start from
directory_path = './'
list_files_recursive(directory_path)
L.sort()
for i in L:
    print(i[4:].replace("/","")[:-3:],end=" ")
print()
```
Which gives the binary text `01100100 01100011 01000011 01010100 01000110 01111011 01110011 01100011 01110010 00110001 01110000 00110111 00110001 01101110 01100111 01011111 00110001 01110011 01011111 01100011 00110000 00110000 01101100 01111101` which decodes to `dcCTF{scr1p71ng_1s_c00l}`.

# Dumpster Diver

## Observations
Obviously the code was somewhere in the programs memory, maybe using a debugging tool like gdb would help? Tried using gdb to debug the file and look into variables etc but was not able to find anything. Was not familiar with memory dumps and was not able to solve the problem without the hint.

# Hidden in the crowd

## Observations
The directory seemed to conatin a lot of files with random names, given the name of the challenge they seemed like a red herring and I felt that the flag would probably be in a hidden file.

## Solution
Ran `ls -lah` to list all files to reveal the hidden `.flag` file, ran `cat .flag` to get the flag `dcCTF{h1dd3n_f1l3s_4r3_n07_s0_h1dd3n}`

# LockedVault

## Solution
Used `chmod` with `+r` and `+x` to fix permissions, got the keys, decrypted with base64, got the flag `dcCTF{y0u_4r3_4_p3rm1ss10n_h4ck3r_n0w}`

# Log Explore

## Observations
The generated log file is quite large, obviously opening in gui text editor or even a terminal text editor seems impractical, maybe `grep` will work?

## Solution
Ran `cat log.txt | grep -a dcCTF`, took some time but got the flag `dcCTF{b1G_L0g}`

# Process Hunter

## Solution
Ran `top -c` to run the top command with command line flags enabled, looked for the flag in the list and found `--flag=dcCTF{ps_aux_r3v34l5_4ll}`

# Welcome Agent

## Solution
Ran `cat flag.txt` to get the flag `dcCTF{w3lc0me_t0_7h3_m4tr1x}`
