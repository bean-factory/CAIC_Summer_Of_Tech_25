## Classic Caesar 
Decrypted the ciphertext `gfFWI{FDHVDU_QHYHU_GLHV}` using Caesar cipher with a shift of 3 to get the flag `dcCTF{CAESAR_NEVER_DIES}`..

## Oui Oui Secret 
Used [https://www.dcode.fr/vigenere-cipher](https://www.dcode.fr/vigenere-cipher)  to bruteforce the Vigenere cipher first using `dcCTF` as a known plaintext word then used partial key to get the flag `dcCTF{how_did_you_bruteforce_this}`.

## Fair Enough
Used [https://www.dcode.fr/playfair-cipher](https://www.dcode.fr/playfair-cipher) to decode the playfair cipher to get `BUTAREYOUPLAYINGFAIR` leading to the flag `dcCTF{BUTAREYOUPLAYINGFAIR}`.

## Weak RSA
Used [https://www.dcode.fr/prime-factors-decomposition](https://www.dcode.fr/prime-factors-decomposition) to decompose `n` into its prime factors `219920443573698782845930677192261022747` and `262725443219511029142449525203053232189`, then used [https://www.dcode.fr/rsa-cipher](https://www.dcode.fr/rsa-cipher) to get the flag `dcCTF{W34k_RSA_1s_N0_G00D}`.

## Hidden in Plain Sight
Ran `stegseek miku.jpg` to get the `flag.txt` as `miku.jpg.out`, ran `cat miku.jpg.out` to get the flag `dcCTF{h1d1ng_1n_y0ur_w1f1}`.

## Chameleon Image
Opened `mystery_file.jpg` in a hex editor, found out that it is a polyglot file and is valid as a zip. Changed the extension and got the flag `dcCTF{POLYGLOT_FILES_ARE_SNEAKY` from flag.txt. The flag is also directly visible in the hex editor although i dont think this is intended xd.

## Sound of Secrets
Opened `mysterious_audio.wav` in Sonic Visualizer and generated a spectogram, found two sets of morse code with the more visible one being a decoy, ran the actual morse code through a decoder and got the flag `dcCTF{R34LFL4G}`.

## Cropped Antics
Opened `i_won.pdf` in a pdf editor and moved the image down to get the flag `dcCTF{Cr0p3d_pDF}`.

## Evidence Disk
Mounted `disk_image.dd` by running `sudo mount -o loop disk_image.dd ./mnt`, then used photorec to recover files. Opened `f0000066.png` to get the flag `dcCTF{FILE_RECOVERY_SUCCESS}`.

## Network Intrusion 
Opened `network_capture.pcap` in Wireshark, noticed a request to 0.0.0.0 saw a suspicious string `exfiltrate-ZGNDVEZ7TDBDNExIMFNUX0RONV8zWEYxTFRSNFQxME59.evil.com` decrypted `ZGNDVEZ7TDBDNExIMFNUX0RONV8zWEYxTFRSNFQxME59` using base64 to get the flag `dcCTF{L0C4LH0ST_DN5_3XF1LTR4T10N}`.

## Lots of Notes
Ran `stegseek notes.jpg` to get `20250609_231659.mp3`, converted to wav by `ffmpeg -i 20250609_231659.mp3 ntoes.wav`, changed the sample rate to 48k by `sox notes.wav -r 48k output.wav`. Ran the audio through QSSTV to get the image with the flag `dcCTF{B33P_B00P}`.
