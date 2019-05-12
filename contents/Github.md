# Github
- [Fork된 Git 레파지토리에 원본 레파지토리 업데이트하기](#fork된-git-레파지토리에-원본-레파지토리-업데이트하기)


## Fork된 Git 레파지토리에 원본 레파지토리 업데이트하기
[참고사이트](http://taewan.kim/post/updating_fork/)  
특정 레파지토리를 fork해서 변경하다가, 원본 레파지토리의 변경사항을 반영해야 할 때가 있다. 구체적인 방법을 알아본다.
![image](https://taewanmerepo.github.io/2017/09/updating_fork/img040.png)
- 로컬 git 레파지토리에 원본 레파지토리를 remote repository로 등록합니다. 원본 리파지토리는 **upstream**으로 하는것이 관례.
  - git remote add upstream {GIT_URL}
- 로컬 git 레파지토리에 forked 된 레파지토리는 git clone을 할때 자동으로 등록된다 -> remote repository 명: **origin**
- 위 그림처럼, git pull 명령을 이용하여 원본 git 레파지토리로 부터 로컬 레파지토리로 변경 사항을 받을 수 있습니다. 명령은 다음과 같습니다.
  - git pull {remote repository 이름} {remote repository 브랜치 이름}
  - **-> git pull upstream master**
- 원본 repository의 변경사항을 forked된 리파지토리에 반영하기
  - git push {forked된 repository 이름} {forked 된 repository에서 반영할 브랜치}
  - **-> git push origin master**
  

