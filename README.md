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

# 파워셀 Install (Windows OS)

https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3
