## 버전 관리 도구란?

- [x] git log
  - 커밋 내역 확인 가능
  - git log --oneline
    - 한 줄로 커밋 내역을 확인한다.
  - git log -n 2 --oneline
    - 커밋 내역 중 가장 최근 2개만 확인한다.
  - git log [오래된 커밋의 주소 7자리]..[최근 커밋의 주소 7자리] --oneline
  
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
  - 
  
- [x] git reset
  - 과거 커밋 버전으로 돌아간다.
  - 돌아간 버전 이후로는 삭제된다.
