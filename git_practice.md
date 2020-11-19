# 💪 git pratice

## Whitespace Error

__error 설명 :__ warning: CRLF will be replaced by LF in some/file.file.  
The file will have its original line endings in your working directory.  

유닉스 시스템에서는 한 줄의 끝이 LF(Line Feed)로 이루어집니다.  
윈도우에서는 줄 하나가 CR(Carriage Return)와 LF(Line Feed), 즉 CRLF로 이루어지기 때문입니다.   

__윈도우일 경우 :__ git config core.autocrlf true  
__리눅스나 맥인 경우 :__ git config core.autocrlf true input (input이라는 명령어를 추가해줌으로써 단방향으로만 변환이 이루어지도록 설정합니다.)  
__직접 설정하고 싶은 경우 :__ git config core.safecrlf false
