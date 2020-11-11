# 😎 git_basic 😎

## 버전? 버전 관리 시스템  
= 유의미한 변화가 결과물로 나온 것  

버전 관리? 하나의 버전이 관리되는 과정에서 __되돌리는 과정__ 이 필요합니다.  
백업 필수!! 하나의 버전이 관리되는 과정에서 __효율적인 백업__ 이 필요합니다.  
하나의 버전이 관리되는 과정에서 __효율적인 협업__ 이 필요합니다.  
버전이 만들어지는 두 개의 단계  

## 버전이 되기까지 거쳐가는 세 개의 공간  

Working directory : 내가 코드작업을 하는 공간  

Working directory <= 변경사항들 중 다음 버전이 될 파일들을 선별에서 사용해야 합니다.

Staging Area : 버젼이 될 후보들이 올라오는 공간  

Repository : 저장고 , 버젼들의 내역이 저장되는 공간  

명령어 : git <명령어>

Working directory -> Staging Area : git add   
Staging Area -> Repository : git commit  
Staging Area -> Repository to file upload : git push  

# git 실습

git init : 버젼이 시작됩니다.  
ls -al : (숨김 파일 / 폴더까지 포함한) 모든 파일 / 폴더 목록 보기    
.<파일명> : 숨김 파일이라는 의미입니다.  
status : 버젼 관리되는 폴더의 상태를 보여줍니다.  
git rm --cached <파일명> : Staging Area에 있던 파일을 내려줍니다.    
git log : commit log응 확인할 수 있습니다. commit(버젼)을 식별할 수 있습니다.    
git commit -m "commit message" : 빠르게 commit을 남기는 방법  
git commit : 길고 자세하게 작성하는 방법    
=> 작성후, ESC 누른후, :wq -> w는 저장 q는 편집기 종료를 의미합니다.    

# github

어떻게 다른 사람과 원경으로 협업을 할 수가 있는거죠?    
Github : 각자의 컴퓨터에만 존재하는 버전을 저장/관리해주는 서비스    
git commit -am "commit message" (단, 한 번이라도 commit한 대상에 대해서만 가능합니다.)  
git remote add origin < Repository주소 > : 어떤 Repository에 저장할 것인지   정해줍니다.  
git push -u origin master : Staging Area에 있던 버젼들을 Repository로 올려줍니다.    

# Git - 되돌리기

git reset --hard HEAD^ : 수정한 것까지 통째로 되돌리자  
git reset --mixed HEAD^ : add한 것까지 적당히 되돌리자(옵션이 생략된 경우) <= default값입니다.  
git reset --soft HEAD^ : commit 한 것만 되돌리자   
HEAD : 가장 최근 버전에서  
^ : 하나만!  

git diff : 변경된 사항 확인하기  
git revert  
git log : commit된 버젼 기록 확인하기  
git checkout : Staging Area에 add된 파일/폴더를 unstaging 상태로 바꿉니다.    
*github의 화살표가 있는 폴더는 그 폴더 안에 .git이 들어있는 경우입니다.  

# git Branch

협업을 하고 올바른 병합을 위해서 Branch를 알아야 합니다.   
작업 단위로 나눈다 -> 각자 작업한다 -> 합친다  

git branch : 현재 branch 상태를 알 수 있습니다. 또한 , 위치도 알 수 있습니다.  
git branch < branch 이름 > : 해당 branch 이름으로 branch를 생성합니다.  
git checkout < branch 이름 > : 해당 branch 이름으로 이동합니다.  

어떤 branch를 어디로 합칠 것인가? 병합의 대상을 명확히 해야 합니다.  
1. '병합의 결과'가 되는 대상에 checkout  
2. git merge < 합치려는 branch >

원격저장소는 그저 또 다른 repository(저장소)일 뿐입니다.  
협업은 repository끼리의 상호작용일 뿐입니다.  

* Repository끼리의 상호작용 종류:

1. 원격저장소 조회(추가)하기 $git remote(-v)
내 로컬 repsitory와 상호작용하고 있는(혹은 할 수 있는) 원격 저장소들의 목록을 조회하기 -v 옵션 : 단축 이름과 URL 같이 보기  

git remote add origin < url > : < url >에 있는 원격저장소를 origin이라는 이름으로 추가하기  
git remote add < 단축이름 > < url > : 기존 워킹 디렉토리에 새 원격저장소를 추가하는 명령어  

2. 원격저장소에 밀어넣기 $git push  
git push -u origin master : 내 repository의 master branch를 origin의 master branch로 push해라 (-u : 디폴트 설정)

3. 원격저장소 갖고 와서 합치기 $git pull
git pull (origin master) : origin을 내 repository의 master branch로 갖고 와라(merge)  __덮어쓴다__ 

4. 원격저장소 일단 갖고만 오기 $git fetch
git fetch (origin master) : 동기화시키지는 말고(merge하지 말고)origin을 내 repository의 master branch로 갖고 와라

git fetch < 원격저장소 이름 >  한 후,  
git checkout < 원격저장소 이름 >/master  
git checkout FETCH_HEAD  에서 확인할 수 있습니다.  

5. 원격저장소 복사하기 $git clone
git clone < url > : < url >에 있는 원격 저장소 내용을 현재 디렉토리에 복사해오기  

원격 저장소 삭제하는 명령어 : git remote rm < 원격저장소 이름 >
rmdir /s < 폴더 삭제 > : 안에 있는 모든 내용과 폴더를 지우는 명령어  

# 원격 저장소로 협업 시나리오 확인하기 

1. 내 로컬 저장소는 변했는데 원격 저장소는 변함이 없는 경우
git push를 합니다.

2. 내 로컬 저장소는 변함이 없는데 원격 저장소는 변하는 경우
git pull을 한 후, 작성을 시작합니다.

3. 내 로컬 저장소는 변했는데 원격 저장소는 변하는 경우

3.1. rebase

3.2. pull request(->merge)

1. 협업 대상 repository fork하기
2. fork 해온 곳에서 clone하기  
3. branch를 만들고 작성하고자 하는 코드(commit)작성하기
=> git checkout -b newbranch2 : newbranch2를 만들고 변경해줍니다.  
4. 코드 작업을 수행한 그 branch에 push하기
5. pull request 날리기
6. pull request 날린 branch 지우기  

# Git rebase 

1. merge
1.1 fast-forward merge  
$ git checkout master  
$ git merge branch1  

1.2 3-way merge를 통한 merge : merge의 결과인 merge commit이 생깁니다.    
$ git checkout master  
$ git merge branch1  
Merge commit이 많아진다면?  
Commit history 관리가 어려워짐  

2. rebase

현재 내가 작업하고 있는 branch의 base를 옮긴다.
* base = 현재 내가 작업하고 있는 branch와 합치려는 branch의 공통 조상  
즉, rebase는 합치고자 하는 branch의 최신 commit으로 base를 옮긴다는 것입니다.  
쓸데 없는 commit이 생기지 않습니다.(history 관리 용이)

* 순서
1. git checkout branch1 : rebase를 해야 하는 branch로 이동합니다.
2. git rebase master : master를 base로 rebase해줍니다.   

$ git log --all --graph --oneline : 한줄로 commit 기록 확인하기  
$ git checkout -b branch1 : branch1 브렌치를 생성하고 위치를 변경합니다.  
$ git merge <remote-name> <branch-name> --allow-unrelated-histories : commit 기록이 다른 두 리퍼지토리를 합칩니다.
# Git 심화?

심화 컨텐츠를 원한다면?

1. https://git-scm.com/doc
2. help option 사용하기 Ex) git add --help
3. http://try.github.io/  몇가지가 안 될수도 있습니다.

* 심화 자료
1. 오픈소스를 쓰려는자, 리베이스의 무게를 견뎌라
2. Rebase의 충돌관리  
생활코딩 -> 지옥에서 온 Git - Rebase의 충돌 관리  
