If something is not listed here, that just means it hasn't been tested. It doesn't mean anything else.
You assume all risks and responsibilities by following any of the workarounds listed here. The workarounds and URLs posted are NOT thoroughly tested and should NOT be trusted.

#Product Installer + ML

Windows XP (32 and 64 bit)
- R11.1: Works, no additional steps needed.
- R2015b and newer: Does not work, no known workaround.

Windows 7 (64-bit)
- R11.1: Works, no additional steps needed.
- R12.1-R14SP3: Same as Windows 8.1 and newer.
- R2022a & R2022b: Works, no additional steps needed.
- R2023a Prerelease & R2023a: You must use MPM for installation. To make MPM work, you must use the same instructions used described for this release in the Windows 8.1 section. Note that if you only have some of the Windows 7 updates needed, but not all of them, you still won't be able to launch MATLAB. Looking for a download link? Use this URL: https://thecomputerguy.co/wp-content/uploads/2019/12/Windows6.1-KB2533623-x64.zip
- R2024a Prerelease: Installer runs fine, but MATLAB seems to only run with no desktop/Java enabled. Some error about mwlogin_startup_plugin.dll shows up and I'm unaware of any workarounds.

Windows 8.1 (64-bit)
- R11.1-R2022b: Same as Windows 10 (64-bit) & 11.
- R2023a Prerelease-R2023b: TL; DR: It works, with additional content needed and you must update your OS to latest updates available. 
    - Full answer: You may receive an error message about api-ms-win-crt-runtime-l1-1.0.dll missing. Update Windows 8.1 and then Update for Universal C Runtime in Windows (https://support.microsoft.com/en-us/kb/2999226). This will allow the installer to run, but MATLAB may not launch. You may receive of the two following errors:
       - An exception error message saying that webui is an unregistered feature. This is a CEF-related issue. 
            - Installing all Windows 8.1 updates and then restarting the machine will resolve this (you didn't fully update in the previous step.)
	    - A classpath issue followed by Java errors.
            - Changing the JRE to JRE 1.8.0_351, JDK-19, or R2022b's JRE will not resolve the issue. You need to reinstall R2023a and delete the installation folder between uninstalling and installing again.

Windows 10 (64-bit) & 11
- R11.1: Does not work, no known workaround.
- R12.1: Works, no additional steps needed. May need to run as administrator, in some cases.
- R13SP1: PROCEED WITH CAUTION! - Installer works without additional configuration. For startup, you need to obtain a file called “wtsapi32.dll” from a Windows XP machine and then placed it in \MATLAB6p5p1\bin\win32 to launch MATLAB.
- R13SP2: Same as R13SP1
- R14SP1: Installer works without additional configurations. Java errors will be displayed when launching MATLAB and can be circumvented by running the program in compatibility mode with Vista and admin rights.
- R14SP2: Same as R14SP1
- R14SP3: Same as R14SP1
- R2006a (32-bit): Works, no additional steps needed.
- R2006a (64-bit): Works, no additional steps needed.
- R2006b (32-bit): Run the setup.exe in Windows Vista mode with admin rights. Same for the program or else it will give Java errors.
- R2006b (64-bit): Cannot press next after typing in a PLP. Use the 32-bit release. Otherwise, no known workaround.
    - Have tried the following: silent install, running in every compatibility mode available (Vista-Windows 8), with and without admin rights.
- R2007a (32-bit): Works, no additional steps needed.
- R2007a (64-bit): Same as R2006b. The 32-bit version needs to be used in Windows Vista mode with admin rights.
- R2007b (32-bit): Untested.
- R2007b (64-bit): Works, no additional steps needed.
- R2008a-R2009a (32 & 64-bit): The activation client when you first open the installer is broken, meaning you'll need to download the license file manually and use a FIK. The ISO is not needed because you can download the product files as ZIPs from our website.
- R2009b (64-bit)-R2023a Prerelease: Works, no additional steps needed. Yes, really. If there's an issue, it's not an OS compatibility issue.

Windows Server 2016
- R2023a Prerelease: Works, no additional steps needed.
- R2023b Update 3 and older: Supposedly works.
- R2023b Update 4: Receives an error mentioning that loading “libmwlmgrimpl.dll” failed. So far, I haven't found any workarounds that aren't horribly invasive.

Windows Subsystem for Linux 2 (WSL2)
- Any release: There is no definitive workflow. Install the libraries that MathWorks lists as necessary (since they now do this because it concerns them.)
#NLM

#RR

#PolA

#Nautilus
