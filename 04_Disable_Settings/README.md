# link

<hr />

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


# 윈도우키 눌렀을때 웹 검색 안되게 x[|🔝|](#link)

```bash
# 실행 win + r
regedit


HKEY_CURRENT_USER
 -> Software -> Policies -> Microsoft -> Windows
  # 우클릭 누르고 키(K) 만들기
    -> Explorer 폴더 만들기
      # 빈 공간에서 우클릭 -> 새로 만들기 -> DWORD(32비트) 값 -> 
       -> DisableSearchBoxSuggestions
          # 값 데이터 숫자를 1로 설정(단위 16진수)
          -> 1   

# 재부팅하면 설정완료
```

- [윈도우 웹 자동 서치 기능 없애기| 쓰레기 윈도우](https://youtu.be/00on6uI4gMg?si=3uxAMrjqVsx0AVdg)
