# OpenSSL windows build guide

### Preparation

  - ActivePerl http://www.activestate.com/activeperl/downloads
  - or Strawberry Perl (Portable) http://strawberryperl.com/releases.html
  - nasm http://www.nasm.us/

### Build

```sh
portableshell.bat #Strawberry Perl portable environment variables
"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" #register environment variables
cd openssl-1.0.2j #change to the source directory
perl Configure VC-WIN32 --prefix=../build #32bit
ms\do_nasm.bat #use nasm, don't use MASM
nmake -f ms\nt.mak #build
nmake -f ms\nt.mak install #install
```  

### Notes

```
perl Configure VC-WIN64A #64bit
ms\do_nt.bat #no asm
ms\do_win64a.bat #64bit, nasm or ml64
nmake -f ms\ntdll.mak #shared lib
```
  
### Possible issues

sha1-586.asm : error A2070:invalid instruction operands (asm not support)

  - ml.exe is not supported, use nasm instead

nasm is not recognized as an internal or external command (PATH problem)
  
  - put nasm.exe in C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin
  
### References

  - https://www.openssl.org/
  