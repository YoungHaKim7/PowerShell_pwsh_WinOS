# Contents

[Choco Install 윈도우 패키지 관리자: chocolatey](https://github.com/YoungHaKim7/PowerShell_pwsh_WinOS#%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%8C%A8%ED%82%A4%EC%A7%80-%EA%B4%80%EB%A6%AC%EC%9E%90-chocolatey)

<br>

<hr>

 # Echo로 README.md에 ( Result ``` ```) 넣기 

```
echo "# Result" "" "``````" >> README.md && echo "``````" >> REAME.md && echo "" "``````" >> README.md
```

- 러스트 프로젝트 기본 셋

```
echo "# Result" "" "``````" >> README.md && echo "``````" >> README.md && echo "" "``````" >> README.md && echo "/target" >> .gitignore && echo "Cargo.lock" >> .gitignore
echo "# Result" "" "``````" >> README.md && echo "``````" >> README.md && echo "" "``````" >> README.md && echo "/target" >> .gitignore && echo "Cargo.lock" >> .gitignore && echo ".vscode" >> .gitignore
```

# 윈도우 파워셀에서 러스트 target폴더 지우기(pwsh.exe) WindowsOS에서

- 상위 폴더에서 하면 하위 폴더에 있는 target 폴더 다 지워진다. ㅎㅎ 편하네 ㅋㅋ 개꿀!!

```
Get-ChildItem -Filter ./target -Recurse -Force | Remove-Item -Recurse -Force
```

- 상위 폴더에서 하면 하위 폴더에 있는 .DS_Store 파일 다 지워진다. ㅎㅎ 편하다

```
Get-ChildItem -Filter .DS_Store -Recurse -Force | Remove-Item -Recurse -Force
```

# 윈도우 파워셀에서 러스트 target폴더 찾기(pwsh.exe) WindowsOS에서

```
dir .\ -r -i "target"
```


# c드라이브에서 내가 원하는 mongosh.exe 찾기, 빠르게 찾자

```
PS C:\> dir c:\ -recurse -filter mongosh.exe 
```

출처 : https://cloudsns.wordpress.com/2012/06/26/powershell%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EC%9E%90%EC%8B%A0%EC%9D%B4-%EC%9B%90%ED%95%98%EB%8A%94-%ED%8C%8C%EC%9D%BC%EC%9D%84-%EB%A7%A4%EC%9A%B0-%EB%B9%A0%EB%A5%B4%EA%B3%A0-%EC%89%BD/


# 윈도우 파웨셀에서 .gitignore 만들기 /target세팅 (pwsh.exe) WindowsOS에서

- WindowsOS윈도우에는 touch가 없으니 echo를 활용하면 된다. 신기한건 Linux나 macOS에서도 되서 신기했다. 무조건 touch로 해야하는줄 알았는데 ㅋㅋ

```

echo /target >> .gitignore


or


echo "/target" >> .gitignore


// >> 파일 뒤에 이어 쓰기
// > 덮어 쓰기라 이전 파일내용 다 날아감.
```

# choco cleaner 쓸때없는 파일 정리 Good !

https://community.chocolatey.org/packages/choco-cleaner

<hr>



# 윈도우 DiskPart 파티션 cmd로 하기 무적이네 ㅎ

https://www.diskpart.com/windows-10/diskpart-windows-10-1203.html

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

```

rm -Force .\read_line03

```


<hr>

# 파워셀 Install (Windows OS)

https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3

# 파워셀 Update

```
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```

# 파워셀 버젼확인하는 방법

```
$PSVersionTable.PSVersion
```

https://jae04099.tistory.com/entry/Console-PowerShell-%EC%97%B0%EC%82%B0%EC%9E%90

# powershell 명령어 다 나옴

```
// powershell 에서 해보자 alias 명령어 다 보여줌

alias
```

# 파워셀 커맨드 설명 Command

- How do you use the Command line? PowerShell, cmd, bash? - Computer Stuff They Didn't Teach You #13

  - https://youtu.be/QKBcHuA3VJE

# PowerShell 공식 문서 Documentation

https://learn.microsoft.com/en-us/powershell/?view=powershell-7.3

<hr>


# How to set up PowerShell prompt with Oh My Posh on Windows 11(외국사람의 파워셀 활용법 진짜 중에 진짜 ㅋㅋ)

https://youtu.be/5-aK2_WwrmM

# 윈도우 패키지 관리자: chocolatey

# 패키지 설치

https://chocolatey.org/packages

```
C:\> choco install 이름
```

- 로컬 패키지 리스트

```
C:\> choco list -l
```

- 패키지 제거

```
C:\> choco uninstall 이름
```

# about_Redirection(PowerShell)
https://learn.microsoft.com/ko-kr/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.3

# ChatGPT. Powershell 생성해줘. 근데 난 아무것도 몰라.

https://youtu.be/bcgjjLXWaNU
