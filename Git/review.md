## 버전 관리 도구란?

- [x] git log
  - 커밋 내역 확인 가능
  - git log --oneline
    - 한 줄로 커밋 내역을 확인한다.
  - git log -n 2 --oneline
    - 커밋 내역 중 가장 최근 2개만 확인한다.
  - git log [오래된 커밋의 주소 7자리]..[최근 커밋의 주소 7자리] --oneline
  - git log --graph --oneline
    - 현재 있는 브랜치의 커밋 내역 그래프를 확인할 수 있다
  - got log --graph --oneline --all
    - 모든 브랜치의 커밋 내역 그래프를 확인할 수 있다.
- [x] git diff
  - add를 하기전에 확인 가능
  - stage에 올라간 상태에서는 diff를 확인할 수 없다.
  - 그래서 stage에 올린 후에 git diff --staged 옵션을 주면 확인가능하다.
    
- [x] git show
  - commit된 내용들을 꺼내서 볼 수 있다.
    
- [x] git restore
  - commit된 적이 없었던 파일을 stage영역에서 unstage영역으로 되돌릴 때
    - git restore --staged "file명"   
  - modify한 내용(commit한 적이 있는 내용)을 stage영역에서 unstage영역으로 되돌릴 때
    - git restore "file명"
    - 단, 수정했던(편집했던) 내용조차 사라진다.
    - 이럴 때는 어떻게 해야할까?
    
- [x] git revert 
  - ''''
  
- [x] git reset
  - 과거 커밋 버전으로 돌아가고 돌아간 버전 이후로는 삭제된다.
    - Soft(HEAD only)
      - 버전은 지워도 stage(인덱스)에 올려둔다.(변경 상태를 다 지우진 않는다)
      - 실수로 reset했던 것을 다시 커밋할 수 있다.
    - Mixed(HEAD and Index)
      - 커밋된 내용도 지워지고 인덱스도 지워진다.
      - 수정된 내용은 남아있어서 실수를 했다면 인덱스에 추가하고 다시 커밋하면 복구할 수는 있다.
    - Hard(HEAD, Index, and Working Tree)
      - 이거는 완전 복구 불가능
  
- [x] git branch
  -  git branch -c main ver2
    - main 브랜치를 복사하여 ver2 브랜치를 만든다.
    - 무조건 main 브랜치를 커밋한 이후에 브랜치를 만들어야 한다.
    
- [x] git checkout
  - git checkout ver2
    - ver2 브랜치로 이동한다.
  - git checkout -b ver2
    - ver2 브랜치를 만들고 이동까지 한다.
  - 브랜치를 왔다갔다 할 수 있다. 하지만 그러한 용도로 쓰는게 아니라 버전을 왔다갔다 하면서 과거 커밋으로 돌아가거나 돌아오는 등의 역할을 한다.
  - git checkout HEAD~2
    - HEAD로부터 2개 뒤에 있는 커밋 버전으로 이동
  - git checkout master
    - 과거 버전에서 다시 원래 버전으로 돌아갈 때 사용하는 명령어
  
- [x] git switch
  - 브랜치를 왔다갔다 하는 용도
    
- [x] 과거의 커밋내용으로 돌아가는 방법 및 되돌아오는 방법
  - **git checkout [7자리주소]**
    - 7자리 주소가 커밋됐을 당시로 되돌아간다.
  - git checkout master
    - 과거에서 다시 현재로 돌아온다.
  - git checkout [7자리주소] <파일명>
    - 7자리 주소가 커밋됐을 당시로 지정한 '파일'만 돌아간다.
    - 이후 git status를 modifyed 되었다고 표시된다. 그래서 커밋만 하면 된다.
    
- [x] 브랜치 이름 바꾸기
  - git branch -m <브랜치명> <새로운 브랜치명>
    
- [x] git swtich
  - 브랜치를 이동한다.

- [x] 가장 바람직하게 브랜치를 병합하는 방법
  - master, dev 브랜치가 있다고 가정하자(dev는 master보다 커밋을 3번 더 한 상태)
  - master 브랜치에서 dev를 병합할 때는 주의할 점이 있다.
    1. dev 브랜치가 생성된 이후 master는 추가적인 커밋 기록이 있으면 안된다. 즉, dev 브랜치 생성됐을 당시에 그대로 남아 있어야 한다.
    2. dev 입장에서 master 브랜치를 병합하는 것이 아니라 master 브랜치에서 dev 브랜치를 병합하는 것.
  - master에서 dev 브랜치를 병합하면 HEAD가 동일한 부분을 가리킨다. dev의 끝부분을.
    - 이를 Fast-Forward 방식으로 병합했다고 한다.
