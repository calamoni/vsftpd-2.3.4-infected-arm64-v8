# vsftpd-2.3.4-infected-arm64-v8

A repository for the infected version of VSFTPD 2.3.4 with purposes of containerized educational testing. \
The motivation for compiling this binary for arm64 architecture was to be able to use it with a Raspberry Pi :) 

# Instructions

 **Manual build**
```
git clone https://github.com/calamoni/vsftpd-2.3.4-infected-arm64-v8.git
cd vsftpd-2.3.4-infected-arm64-v8.git
cd vsftpd-2.3.4
docker build -t backdoored-vsftpd-2.3.4 .
docker run -it --rm -p 21:21 -p 6200:6200 backdoored-vsftpd-2.3.4
```
**From Docker Hub**
```
docker run -it --rm -p 21:21 -p 6200:6200 calamoni/vsftpd-2.3.4-infected-arm64-v8:vsftpd-2.3.4
```
