I was trying to keep things small as possible so I deleted the graphical version, only the text version is included.

How this binary was made:

1. Download the latest pre-compiled installer binaries from here:
http://links.twibright.com/download/binaries/win32/

2. Extract all files from the installer using 7-zip or extractor of your choice.

3. Delete all but the following:

cygbrotlicommon-1.dll
cygbrotlidec-1.dll
cygbz2-1.dll
cygcrypto-1.1.dll
cyglzma-5.dll
cygssl-1.1.dll
cygwin1.dll
cygz.dll
cygzstd-1.dll
links.crt
links.exe

4. Create new file linkbat.cmd in the same directory as the others with the following contents:

rem Bypass "Terminate Batch Job" prompt.
if "%~1"=="-FIXED_CTRL_C" (
   REM Remove the -FIXED_CTRL_C parameter
   SHIFT
) ELSE (
   REM Run the batch with <NUL and -FIXED_CTRL_C
   CALL <NUL %0 -FIXED_CTRL_C %*
   GOTO :EOF
)

START "" /WAIT CMD /c .\links.exe 



5. run IEXPRESS and select the following options
  A. Extract files and run an installation command.
  B. Package tite: "Links"
  C. No Prompt.
  D. Do not display a license.
  E. Packaged Files (Add all from above including linkbat.cmd
  F. Install Program linkbat.cmd / Post Install Command <None>
  G. Hidden
  H. No message.
  I. Browse > LinksPortable.EXE / Check 'Hide file Extracting Progress' / Check 'Store files using Long File Name'
  J. No Restart
  K. Don't save sed.
  L. Create Package.

6. After IEXPRESS finishes creating the EXE package, replace the icon using Resource Hacker:
http://angusj.com/resourcehacker/

-Tyler
