# Parallels Guest Tools Fix for Debian 5.18 Kernel

## Steps

**This assumes you have already mounted parallels tools to `/media/cdrom0` and have failed to install the guest tools.**

First you can copy the Parallels guest tools into your `/tmp` directory.
```bash
cp -rp /media/cdrom0 /tmp
```
Then you can change over to the `/tmp/cdrom0/kmods` directory, download the patch file and unarchive the `prl_mod.tar.gz` file. 
```bash
wget https://raw.githubusercontent.com/whois-sin/parallels-guest-tools-deb-5.18-fix/main/parallels-tools-17.1.4.51567.fixes.txt; tar -zxvf prl_mod.tar.gz
```
Next, once you've confirmed the `parallels-tools-17.1.4.51567.fixes.txt` file is in the current directory, you can apply the patch by using the following command:
```bash
patch -p1 < parallels-tools-17.1.4.51567.fixes.txt
```
Press **enter** twice and then remove bothe the `parallels-tools-17.1.4.51567.fixes.txt` and the `prl_mod.tar.gz` before archiving the files again. 
```bash
rm parallels-tools-17.1.4.51567.fixes.txt prl_mod.tar.gz
```
Now that the files have been removed we can create a new tar file with the patched file and install the guest tools. 
```bash
tar -zcvf prl_mod.tar.gz .; ../install
```
