# 파워셀 version7.3.3설치

https://github.com/PowerShell/PowerShell/releases/tag/v7.3.3

# PowerShell_pwsh_WinOS

# 윈도우 파웨셀에서 원하는 폴더 강제로 지우기(pwsh.exe) WindowsOS에서

- rm -Force 지우고 싶은 폴더

```

rm -Force .\read_line03

```

# 윈도우 파웨셀에서 .gitignore 만들기 /target세팅 (pwsh.exe) WindowsOS에서

- WindowsOS윈도우에는 touch가 없으니 echo를 활용하면 된다. 신기한건 Linux나 macOS에서도 되서 신기했다. 무조건 touch로 해야하는줄 알았는데 ㅋㅋ

```

echo /target >> .gitignore


or


echo "/target" >> .gitignore

```

# 윈도우 파워셀에서 러스트 target폴더 지우기(pwsh.exe) WindowsOS에서

- 상위 폴더에서 하면 하위 폴더에 있는 target 폴더 다 지워진다. ㅎㅎ 편하네 ㅋㅋ 개꿀!!

```
Get-ChildItem -Filter ./target -Recurse -Force | Remove-Item -Recurse -Force
```

# 윈도우 파워셀에서 러스트 target폴더 찾기(pwsh.exe) WindowsOS에서

```
dir .\ -r -i "target"
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
