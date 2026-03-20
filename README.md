# link

- 윈도우 패키지 관리자
  - [Choco Install 윈도우 패키지 관리자: chocolatey](https://github.com/YoungHaKim7/PowerShell_pwsh_WinOS#%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%8C%A8%ED%82%A4%EC%A7%80-%EA%B4%80%EB%A6%AC%EC%9E%90-chocolatey)
  - scoop https://scoop.sh/

- VSCode 꼭 설치해야함(PowerShell코딩)
  - https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell

- [윈도우cmd파티션_[Windows] 명령프롬프트(CMD)에서 파티션(Partition) 관리하기 - DiskPart](https://m.blog.naver.com/PostView.naver?blogId=opusk&logNo=220984140291&proxyReferer=https:%2F%2Fwww.google.com%2Furl%3Fq%3Dhttps:%2F%2Fblog.naver.com%2Fopusk%2F220984140291%26sa%3DU%26sqi%3D2%26ved%3D2ahUKEwivprGMlqSLAxX7fPUHHWWPAK0QFnoECCUQAQ%26usg%3DAOvVaw0uPU_gOcKDFJYrH-5nv_Nt&trackingCode=external)
  - [gpt로 변환 방법](https://m.blog.naver.com/ysyoon20/223105430865)

- [wsl 명령어 정리](#wsl-명령어-정리)

- [gcc clang설치](#windowsos에-gcc-와-clang-설치)

- [마소_wsl설명서](https://learn.microsoft.com/ko-kr/windows/wsl/)

- WSL2이제 오픈소스됨 github(250319)
  - The source for the Linux kernel used in Windows Subsystem for Linux 2 (WSL2) 
    - https://github.com/microsoft/WSL2-Linux-Kernel
  - [관련 블로그) May 19, 2025 | The Windows Subsystem for Linux is now open source By Pierre Boulay](https://blogs.windows.com/windowsdeveloper/2025/05/19/the-windows-subsystem-for-linux-is-now-open-source/)

<br>

<hr>

# code

```
```powershell
```

# wsl1은 옛날(버젼) 리눅스 커널이라 쓰레기다. 왠만하면 wsl2쓰도록 하자!! wsl1존나게 구림.
- wsl1에서 wsl2로 업데이트 하기
  - Linux 커널 업데이트 패키지는 Windows 운영 체제 이미지 내에서 WSL을 실행하기 위해 WSL 2 Linux 커널의 최신 버전을 설치합니다. 
    - https://learn.microsoft.com/ko-kr/windows/wsl/install-manual#step-3---enable-virtual-machine-feature

# (문제가 많은 wsl1) Upgrade of a freshly installed WSL1 Ubuntu 24.04 fails
- https://superuser.com/questions/1863713/upgrade-of-a-freshly-installed-wsl1-ubuntu-24-04-fails

- 이걸로 해결Workaround 2: override command
  - Possible if the error has already occurred and the installation is to be completed.
  - The error occurs in the post-install script of systemd (`/var/lib/dpkg/info/systemd.postinst`), more precisely when calling the command systemd-sysusers in this script.
  - You can link the binary systemd-sysusers to echo, for example. This allows the post-install script to be executed, except for the command that is executed via systemd-sysusers, as this only generates an output via echo, but you no longer run into an error.

```
cd /bin && mv -f systemd-sysusers{,.org} && ln -s echo systemd-sysusers && cd -
apt install -f
```

- Source of the 1st command: https://github.com/microsoft/WSL/issues/10397#issuecomment-1780132430
  - Hint: I am not sure about the future effects or problems by "disabling" the systemd-sysusers command.

# MINGW64설정관련[|🔝|](#link)
- https://gauryan.tistory.com/222

- 파워셀에서 이렇게 명령어 넣으면 실행된다.굿
```
C:/msys64/msys2_shell.cmd -defterm -here -no-start -ucrt64
```

- PATH설정
  - https://lazyfoo.net/tutorials/SDL/01_hello_SDL/windows/mingw/index.php

<hr>

![PowerShell_Core_6 0_icon](https://github.com/YoungHaKim7/Cpp_Training/assets/67513038/24eedd6e-b3af-41c9-b56b-f847a3132e20)

# wsl 명령어 정리[|🔝|](#link)
- https://learn.microsoft.com/ko-kr/windows/wsl/basic-commands

# 설치가능 리스트[|🔝|](#link)

```bash
 wsl --install
Linux용 Windows 하위 시스템이 이미 설치되어 있습니다.
다음은 설치할 수 있는 유효한 배포 목록입니다.
'wsl --install -d <배포>'를 사용하여 설치하세요.

NAME                                   FRIENDLY NAME
Ubuntu                                 Ubuntu
Debian                                 Debian GNU/Linux
kali-linux                             Kali Linux Rolling
Ubuntu-18.04                           Ubuntu 18.04 LTS
Ubuntu-20.04                           Ubuntu 20.04 LTS
Ubuntu-22.04                           Ubuntu 22.04 LTS
Ubuntu-24.04                           Ubuntu 24.04 LTS
OracleLinux_7_9                        Oracle Linux 7.9
OracleLinux_8_7                        Oracle Linux 8.7
OracleLinux_9_1                        Oracle Linux 9.1
openSUSE-Leap-15.5                     openSUSE Leap 15.5
SUSE-Linux-Enterprise-Server-15-SP4    SUSE Linux Enterprise Server 15 SP4
SUSE-Linux-Enterprise-15-SP5           SUSE Linux Enterprise 15 SP5
openSUSE-Tumbleweed                    openSUSE Tumbleweed
```

# wsl.exe -d ubuntu-22.04[|🔝|](#link)

- 윈도우 wsl 우분투 22.04 시작하기
```powershell
wsl.exe -d Ubuntu

wsl.exe -d Ubuntu-24.04

wsl.exe -d ubuntu-22.04

wsl.exe -d kali-linux

wsl.exe -d Debian



// 종료
wsl.exe -t Ubuntu-24.04
```

- wsl 우분투 가상 환경 종료 하기
```powershell
wsl.exe --terminate Ubuntu-22.04

or

wsl.exe -t Ubuntu-22.04

wsl.exe -t kali-linux

# 설치 완료 후(arch linux (wsl2)접속)
arch.exe 



// 설치한 우분투삭제
wsl.exe --unregister Ubuntu-22.04

wsl --unregister <distroName>
```

- ```wsl --list --online```
```powershell
wsl --list --online
다음은 설치할 수 있는 유효한 배포판 목록입니다.
'wsl.exe --install <Distro>'를 사용하여 설치합니다.

NAME                                   FRIENDLY NAME
Ubuntu                                 Ubuntu
Debian                                 Debian GNU/Linux
kali-linux                             Kali Linux Rolling
Ubuntu-18.04                           Ubuntu 18.04 LTS
Ubuntu-20.04                           Ubuntu 20.04 LTS
Ubuntu-22.04                           Ubuntu 22.04 LTS
OracleLinux_7_9                        Oracle Linux 7.9
OracleLinux_8_7                        Oracle Linux 8.7
OracleLinux_9_1                        Oracle Linux 9.1
openSUSE-Leap-15.5                     openSUSE Leap 15.5
SUSE-Linux-Enterprise-Server-15-SP4    SUSE Linux Enterprise Server 15 SP4
SUSE-Linux-Enterprise-15-SP5           SUSE Linux Enterprise 15 SP5
openSUSE-Tumbleweed                    openSUSE Tumbleweed
```

- https://learn.microsoft.com/ko-kr/windows/wsl/basic-commands

- 인스톨 우분투 https://www.lainyzine.com/ko/article/how-to-install-wsl2-and-use-linux-on-windows-10/

- 설치한 우분투 삭제
  - https://askubuntu.com/questions/1261664/how-to-uninstall-the-wsl-installation-of-ubuntu-20-04-from-windows-10

# WSL1과 WSL2 환경분리하는 방법
- https://xeppetto.github.io/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4/WSL-and-Docker/05-Dividing-WSL1-and-WSL2/

 # Echo로 README.md에 ( Result ``` ```) 넣기 

```powershell
echo "# Result" "" "``````" >> README.md && echo "``````" >> REAME.md && echo "" "``````" >> README.md
```

- 러스트 프로젝트 기본 셋

```powershell
echo "# Result" "" "``````" >> README.md && echo "``````" >> README.md && echo "" "``````" >> README.md && echo "/target" >> .gitignore && echo "Cargo.lock" >> .gitignore

```

```powershell
echo "# Result" "" "``````" >> README.md && echo "``````" >> README.md && echo "" "``````" >> README.md && echo "/target" >> .gitignore && echo "Cargo.lock" >> .gitignore && echo ".vscode" >> .gitignore
```

# wsl1에서 wsl2로 업데이트 하기
- Linux 커널 업데이트 패키지는 Windows 운영 체제 이미지 내에서 WSL을 실행하기 위해 WSL 2 Linux 커널의 최신 버전을 설치합니다. 
  - https://learn.microsoft.com/ko-kr/windows/wsl/install-manual#step-3---enable-virtual-machine-feature

<hr>

# windows (cmake 설치)

- you can already do this (or should anyhow).

- install cmake like this to have it added to PATH for all users:

```powershell

choco install cmake.install --installargs '"ADD_CMAKE_TO_PATH=System"'

```

- or the following to have it added to PATH for the current user only
```powershell
choco install cmake.install --installargs '"ADD_CMAKE_TO_PATH=User"'

There isn't any intention of adding it by default, as it isn't added by default in the installer.
```

# msys2설치하기

- https://www.msys2.org/

<hr>

# 윈도우 파워셀에서 러스트 target폴더 지우기(pwsh.exe) WindowsOS에서

- 상위 폴더에서 하면 하위 폴더에 있는 target 폴더 다 지워진다. ㅎㅎ 편하네 ㅋㅋ 개꿀!!

```powershell
Get-ChildItem -Filter ./target -Recurse -Force | Remove-Item -Recurse -Force
```

- 상위 폴더에서 하면 하위 폴더에 있는 .DS_Store 파일 다 지워진다. ㅎㅎ 편하다

```powershell
Get-ChildItem -Filter .DS_Store -Recurse -Force | Remove-Item -Recurse -Force
```

# 윈도우 파워셀에서 러스트 target폴더 찾기(pwsh.exe) WindowsOS에서

```powershell
dir .\ -r -i "target"
```


# c드라이브에서 내가 원하는 mongosh.exe 찾기(find), 빠르게 찾자

```powershell
PS C:\> dir c:\ -recurse -filter mongosh.exe 
```

출처 : https://cloudsns.wordpress.com/2012/06/26/powershell%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EC%9E%90%EC%8B%A0%EC%9D%B4-%EC%9B%90%ED%95%98%EB%8A%94-%ED%8C%8C%EC%9D%BC%EC%9D%84-%EB%A7%A4%EC%9A%B0-%EB%B9%A0%EB%A5%B4%EA%B3%A0-%EC%89%BD/


# 윈도우 파웨셀에서 .gitignore 만들기 /target세팅 (pwsh.exe) WindowsOS에서

- WindowsOS윈도우에는 touch가 없으니 echo를 활용하면 된다. 신기한건 Linux나 macOS에서도 되서 신기했다. 무조건 touch로 해야하는줄 알았는데 ㅋㅋ

```powershell

echo /target >> .gitignore


or


echo "/target" >> .gitignore


// >> 파일 뒤에 이어 쓰기
// > 덮어 쓰기라 이전 파일내용 다 날아감.
```

# linux ```time```같은 명령어를 Windows PowerShell에서 쓰는 명령어

```
Measure-Command { <your command here> | Out-Host }

ex)
Measure-Command { ls | Out-Host }
```
https://stackoverflow.com/questions/3513650/timing-a-commands-execution-in-powershell

<br>

<hr>

# Linux ```which``` 같은 명령어  Windows PowerShell에서 쓰는 명령어

- node위치 알아보기

```powershell
 (get-command node).path
C:\Program Files\nodejs\node.exe

PS E:\young_linux> (get-command pwsh).path
C:\Program Files\PowerShell\7\pwsh.exe
```

# choco cleaner 쓸때없는 파일 정리 Good !

https://community.chocolatey.org/packages/choco-cleaner

<hr>



# 윈도우 DiskPart 파티션 cmd로 하기 무적이네 ㅎ

https://www.diskpart.com/windows-10/diskpart-windows-10-1203.html

- https://learn.microsoft.com/ko-kr/windows-server/storage/disk-management/change-a-gpt-disk-into-an-mbr-disk

- convert gpt
  - https://m.blog.naver.com/netianid/222795318452

# An A-Z Index of Windows💻 PowerShell commands

https://ss64.com/ps/


# choco와 비슷한 윈도우 패키지 관리자

https://scoop.sh/

<hr>


# 파워셀 version7.3.3설치

https://github.com/PowerShell/PowerShell/releases/tag/v7.3.3

# PowerShell_pwsh_WinOS

# 윈도우 파웨셀에서 원하는 폴더 강제로 지우기(pwsh.exe) WindowsOS에서

- rm -Force 지우고 싶은 폴더

```powershell

rm -Force .\read_line03

```

<hr />

# `cmd`에서 윈도우 프로그램 모두 업데이트(update & upgrade) 하기
- https://www.tiktok.com/@jjalcut/video/7496418896631565576?_r=1&_t=ZS-8xIkekga4Lg

```powershell
$ winget upgrade --all
```

<hr>

# 파워셀 Install (Windows OS)

https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows

# 파워셀 Update[|🔝|](#link)

```powershell
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```

# 파워셀 버젼확인하는 방법[|🔝|](#link)

```powershell
$PSVersionTable.PSVersion
```

https://jae04099.tistory.com/entry/Console-PowerShell-%EC%97%B0%EC%82%B0%EC%9E%90

# powershell 명령어 다 나옴[|🔝|](#link)

```powershell
// powershell 에서 해보자 alias 명령어 다 보여줌

alias
```

# 파워셀 커맨드 설명 Command[|🔝|](#link)

- How do you use the Command line? PowerShell, cmd, bash? - Computer Stuff They Didn't Teach You #13

  - https://youtu.be/QKBcHuA3VJE

# PowerShell 공식 문서 Documentation[|🔝|](#link)

https://learn.microsoft.com/en-us/powershell/?view=powershell-7.3

<hr>


# How to set up PowerShell prompt with Oh My Posh on Windows 11(외국사람의 파워셀 활용법 진짜 중에 진짜 ㅋㅋ)[|🔝|](#link)

https://youtu.be/5-aK2_WwrmM

# 윈도우 패키지 관리자: chocolatey[|🔝|](#link)

# 패키지 설치

https://chocolatey.org/packages

```powershell
C:\> choco install 이름
```

- 로컬 패키지 리스트

```
C:\> choco list -l
```

- 패키지 제거

```powershell
C:\> choco uninstall 이름
```

# about_Redirection(PowerShell)[|🔝|](#link)
https://learn.microsoft.com/ko-kr/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.3


# Wsl에서 화면 나오게 세팅하기(Can't open display:)[|🔝|](#link)
- https://stackoverflow.com/questions/61860208/running-graphical-linux-desktop-applications-from-wsl-2-error-e233-cannot-op

# ChatGPT. Powershell 생성해줘. 근데 난 아무것도 몰라.[|🔝|](#link)

https://youtu.be/bcgjjLXWaNU

# 윈도우 11 마우스 우클릭 옛날처럼 돌리기[|🔝|](#link)

- (임시로 1회용) SHIFT를 누른 채로 우클릭을 하면 윈도우10과 같은 느낌의 바탕화면 메뉴를 확인할 수 있을 거에요. 
  - https://blog.naver.com/chaosily/223486145411 [출처] 윈도우11 바탕화면 우클릭 메뉴 윈도우10처럼 사용|작성자 호수

- 영구설정 powershell에서 세팅
```powershell
reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve

taskkill /f /im explorer.exe

explorer.exe
```
https://playcraft.tistory.com/472


# SHA256 해쉬값을 확인하는 방법[|🔝|](#link)

```powershell
certutil -hashfile C:\Users\doomed\Downloads\Miniconda3-latest-Windows-x86_64.exe sha256

```
출처: https://doomed-lab.tistory.com/104 [둠선생 연구실:티스토리]

- Get-FileHash
  - https://learn.microsoft.com/ko-kr/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.5

```powershell
 Get-FileHash .\text.txt

Algorithm       Hash
---------       ----
SHA256          A95E8459B541791DAC5AF1F72E108EFDB73A3
```


# windowsOS에 gcc 와 clang 설치[|🔝|](#link)

- gcc 설치는 choco 로
  - https://community.chocolatey.org/packages/mingw

```bash
choco install mingw
```

- clang은 다운로드 받고 압축 풀고 패스 설정.
  - clang download https://releases.llvm.org/
    - https://github.com/llvm/llvm-project/releases/tag/llvmorg-20.1.0
    - `Assets` 클릭하면 다운로드 가능함.
      - https://github.com/llvm/llvm-project/releases/
  ```bash
  # Intel CPU(x86_64) WindowsOS 사용자는 이 파일 받으면 됨.
  clang+llvm-20.1.7-x86_64-pc-windows-msvc.tar.xz 
  ```

  - windows 패스(PATH) 설정
    - https://www.java.com/en/download/help/path.html

- (한글 WindowsOS 11 환경 변수로 PATH 설정하는 방법)
  - https://ye5ni.tistory.com/157
  - 설정 방법 - [Windows 설정] - [시스템] - [정보] - [고급 시스템 설정] - [고급] - [환경 변수] - [시스템 변수] - [Path] 눌러서 설정하고 싶은 경로를 입력하면 된다
- [(영문 path 설정) Windows 10 and Windows 8](https://www.java.com/en/download/help/path.html)
  - In Search, search for and then select: System (`Control Panel`)
  - Click the `Advanced system settings` link.
  - Click Environment Variables. In the section `System Variables` find the PATH environment variable and select it. Click Edit. If the PATH environment variable does not exist, click New.
  - In the Edit System Variable (or New System Variable) window, specify the value of the PATH environment variable. Click OK. Close all remaining windows by clicking OK.
  -  Reopen Command prompt window, and run your java code.


