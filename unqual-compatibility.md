**Note**: If something is not listed here, that just means it hasn't been tested. It doesn't mean anything else. You assume all risks and responsibilities by following any of the workarounds listed here. The workarounds and URLs posted are **NOT** thoroughly tested and should **NOT** be trusted.

# Product Installer + ML

## Windows XP (32 and 64 bit)
- **R11.1**: Works, no additional steps needed.
- **R2015b and newer**: Does not work, no known workaround.

## Windows 7 (64-bit)
- **R11.1**: Works, no additional steps needed.
- **R12.1-R14SP3**: Same as Windows 8.1 and newer.
- **R2022a & R2022b**: Works, no additional steps needed.
- **R2023a Prerelease & R2023a**: You must use MPM for installation. To make MPM work, you must use the same instructions described for this release in the Windows 8.1 section. Note that if you only have some of the Windows 7 updates needed, but not all of them, you still won't be able to launch MATLAB. Looking for a download link? Use this URL: [Windows6.1-KB2533623-x64.zip](https://thecomputerguy.co/wp-content/uploads/2019/12/Windows6.1-KB2533623-x64.zip)
- **R2024a Prerelease**: Installer runs fine, but MATLAB seems to only run with no desktop/Java enabled. Some error about `mwlogin_startup_plugin.dll` shows up and I'm unaware of any workarounds.

## Windows 8.1 (64-bit)
- **R11.1-R2022b**: Same as Windows 10 (64-bit) & 11.
- **R2023a Prerelease-R2023b**: TL;DR: It works, with additional content needed and you must update your OS to the latest updates available.
  - **Full answer**: You may receive an error message about `api-ms-win-crt-runtime-l1-1.0.dll` missing. Update Windows 8.1 and then Update for Universal C Runtime in Windows ([KB2999226](https://support.microsoft.com/en-us/kb/2999226)). This will allow the installer to run, but MATLAB may not launch. You may receive one of the two following errors:
    - An exception error message saying that webui is an unregistered feature. This is a CEF-related issue.
      - Installing all Windows 8.1 updates and then restarting the machine will resolve this (you didn't fully update in the previous step).
    - A classpath issue followed by Java errors.
      - Changing the JRE to JRE 1.8.0_351, JDK-19, or R2022b's JRE will not resolve the issue. You need to reinstall R2023a and delete the installation folder between uninstalling and installing again.
- **R2024a**: "lmgrimpl\libmwlmgrimpl.dlfailed" error. Does not work, no known workaround at the moment.
- **R2024b and newer**: Does not work, no known workaround at the moment.

## Windows 10 (64-bit) & 11
- **R11.1**: Does not work, no known workaround.
- **R12.1**: Works, no additional steps needed. May need to run as administrator, in some cases.
- **R13SP1**: **PROCEED WITH CAUTION!** - Installer works without additional configuration. For startup, you need to obtain a file called “wtsapi32.dll” from a Windows XP machine and then place it in `\MATLAB6p5p1\bin\win32` to launch MATLAB.
- **R13SP2**: Same as R13SP1.
- **R14SP1**: Installer works without additional configurations. Java errors will be displayed when launching MATLAB and can be circumvented by running the program in compatibility mode with Vista and admin rights.
- **R14SP2**: Same as R14SP1.
- **R14SP3**: Same as R14SP1.
- **R2006a (32-bit)**: Works, no additional steps needed.
- **R2006a (64-bit)**: Works, no additional steps needed.
- **R2006b (32-bit)**: Run the `setup.exe` in Windows Vista mode with admin rights. Same for the program or else it will give Java errors.
- **R2006b (64-bit)**: Cannot press next after typing in a PLP. Use the 32-bit release. Otherwise, no known workaround.
  - Have tried the following: silent install, running in every compatibility mode available (Vista-Windows 8), with and without admin rights.
- **R2007a (32-bit)**: Works, no additional steps needed.
- **R2007a (64-bit)**: Same as R2006b. The 32-bit version needs to be used in Windows Vista mode with admin rights.
- **R2007b (32-bit)**: Untested.
- **R2007b (64-bit)**: Works, no additional steps needed.
- **R2008a-R2009a (32 & 64-bit)**: The activation client when you first open the installer is broken, meaning you'll need to download the license file manually and use a FIK. The ISO is not needed because you can download the product files as ZIPs from our website.
- **R2009b (64-bit)-R2023a Prerelease**: Works, no additional steps needed. Yes, really. If there's an issue, it's not an OS compatibility issue.

## Windows Server 2016
- **R2023a Prerelease**: Works, no additional steps needed.
- **R2023b Update 3 and older**: Supposedly works.
- **R2023b Update 4 and newer**: Receives an error mentioning that loading “libmwlmgrimpl.dll” failed. So far, I haven't found any workarounds that aren't horribly invasive.
- **R2024a and newer**: Same as R2023b Update 4 and newer.

## Windows Subsystem for Linux 2 (WSL2)
- **Any release**: There is no definitive workflow. Install the libraries that MathWorks lists as necessary ([MATLAB dependencies](https://github.com/mathworks-ref-arch/container-images/tree/main/matlab-deps)).

## macOS Monterey (12) (Apple Silicon)
- **R2014a**: The installer appears distorted, but works. Probably a font-related issue. After installation, Java errors will appear upon launching MATLAB and can be fixed by downloading this patch: [Bug Report 1098655](https://www.mathworks.com/support/bugreports/1098655). Afterwards, the font will still appear distorted, but seems to work.
- **R2013b and older**: Will not work. Maybe it’s possible to overcome this with having the installer point to older JREs, but I haven’t tried this nor do I consider it worth trying. I imagine using JREs from around 2013 is a big security concern.

## macOS Ventura (13) (Apple Silicon)
- **R2014b**: Works, no additional steps needed.
- **R2017b**: Does not work, no known workaround.

## macOS Sequoia (15) (Apple Silicon)
- **R2020a and older**: System architecture cannot be detected and therefore, will not run. It will seemingly do nothing when attempting to launch MATLAB.

## Ubuntu 22.04
- **R2010bSP2**: Library errors that are only going to ever be resolved by installing older libraries on the OS and therefore highly unrecommended since it’s dangerous (just use a supported version of Linux in a VM.)
- **R2012a-R2013b**: Activation module does not work and downloading a license file manually will not work since it will say your MAC address is 0000000000. Only a network license works.
  - It seems like this is addressed in this article: [MathWorks Answer](https://www.mathworks.com/matlabcentral/answers/100235-why-can-t-i-activate-matlab-or-start-the-network-license-manager-in-a-newer-linux-environment)
  - But none of the suggestions seemed to work on the OS I’m testing on.
  - This seems to be less of an issue for Virtual Machines, but is not a guarantee the MAC address will be successfully pulled if it is on a Virtual Machine.

## Ubuntu 22.10 STS
- **R2016a**: Works, no additional steps needed.

## Debian 13 Beta as of 1-31-2025
- **R2024b**: Some libraries need to be installed. However, the MSH does not work and therefore, any licenses requiring it or using LNU will not work.

## CentOS Stream 10
- **R2025a Prerelease and older**: libXt needs to be installed. This worked one time, but not another, I swear.

## RedHat EL/CentOS/etc 7.9
- **R2024b and newer**: Requires GLIBC 2.18, but this distro only comes with 2.17. While it's technically possible to upgrade to 2.18, it'll likely break something else. Don't try this.

## RedHat EL 8.5
- **R2010a**: Probably the same as R2010bSP2 on Ubuntu 22.04. TL;DR: No, and there is no reasonable workaround.

## RedHat EL 8.10
- **R2018b**: Crashes on splash screen. Can't seem to find a reasonable workaround for any mode other than -nodesktop.

## Fedora 38
- **R2023a**: After installation, remove/rename `libfreetype.so.6` and `libfreetype.so.6.16` from `/usr/local/MATLAB/R2023a/bin/glnxa64/`

## Arch
- **Any release**: Use the Arch Wiki + `./MATLABWindow` + Linux library dependencies page to determine what you need (yes, I know, there is no Arch section. You're using Arch, help yourself a bit.) [MATLAB dependencies](https://github.com/mathworks-ref-arch/container-images/tree/main/matlab-deps)

## Clear Linux
- No idea.

# NLM

## RHEL/CentOS/Scientific Linux/etc 7.9
- **v11.18.1.0**: Install LSB. Use the command: `sudo yum install lsb`
- **v11.19.5.0**: Works, no additional steps needed.
- **v11.19.6.2**: Works, no additional steps needed.

## RHEL/CentOS Stream/Scientific Linux/etc 9+ & Ubuntu 24.04+
- **v11.18.1.0**: You will need to manually download the LSB installation package from Oracle Linux's website and install it.

# RR

## Ubuntu 20.04 LTS
- **R2022a**: Rename the following libraries in `/usr/local/RoadRunner_R2022a/bin/glnxa64/` so they have an `.old` extension at the end of them:
  - `libdrm.so.2`
  - `libXi.so.6`
  - `libX11.so.6`
  - `libXau.so.6`
  - `libXext.so.6`
  - `libXdmcp.so.6`
  - `libXfixes.so.3`
  - `libXdamage.so.1`
  - `libXrender.so.1`
  - `libXxf86vm.so.1`
  - `libxshmfence.so.1`
  - `libcurl.so.4`

## Ubuntu 22.04 LTS
- **R2022a**: **PROCEED WITH CAUTION!** This is the first version of Ubuntu that does not ship with `libidn.so.11` and instead comes with 12. Installing older libraries is strongly discouraged because it’ll break other things surrounding the OS. Ubuntu 21.04 was the last version of Ubuntu to have `libidn.so.11`. We have an internal video that suggests creating symbolic links will fix this, but I’m not convinced that won’t break something else in the OS.
  - If you don’t care about potentially causing issues, run these commands:
    - `sudo ln -s /usr/lib/x86_64-linux-gnu/libidn.so.12 /usr/lib64/libidn.so.11`
    - `export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib64/libidn.so.11` (you'll probably want to add this to your `.bashrc` file.)

## Debian 11
- **R2022b**: No additional steps needed (figures).

## CentOS, RedHat, Fedora, Rocky Linux, openSUSE, Mandrake Linux, & any RPM-based distro
- RoadRunner will not work. It installs with a deb file that has too many dependencies on Debian-based distros to **reasonably** work on RPM-based distros.

# PolA

## Windows Subsystem for Linux 2 (WSL2)
- **R2022b**: Officially listed as unsupported with no known workaround for any installation issues.

# Nautilus

## Something Debian-based
- If you can't enable hidden files, use `sudo apt install dbus-x11`
