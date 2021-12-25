# Git

source: `{{ page.path }}`

> __기본 명령어__
>> [ref 1](https://theorydb.github.io/envops/2019/05/22/envops-blog-how-to-use-md/)
>> + __git pull__ : git서버에서 최신 코드 받아와 merge 하기
>> + __git add file_path__ : 수정한 코드 선택하기 ( git add * )
>> + __git commit -m “commit_description”__ : 선택한 코드 설명 적기 ( git commit -m “내용”)
>> + __git push romote_name branch_name__ : add하고 commit한 코드 git server에 보내기 (git push origin master)
>> + __git show 커밋해시값__ : 특정 커밋 정보를 확인함
>> + __git reset HEAD [file]__ : git add 취소하기(파일 상태를 Unstage로 변경하기)
>> + __git reset HEAD^__ : commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존
>> + __git reset --hard HEAD__ : 워킹 디렉터리를 원격 저장소의 마지막 commit 상태로 되돌린다.
>> + __git stash [save]__ : 아직 마무리하지 않은 작업을 스택에 잠시 저장( Modified, Staged 파일만 )
>> + __git stash list__ : stash 목록 확인하기
>> + __git stash apply [stash 이름]__ : stash 했던 작업을 다시 가져온다( stash 이름 예제 : stash@{2} ).
>>> [stash 이름]이 없다면 가장 최근의 stash를 가졍와 적용한다.
>> + __git stash drop [stash 이름]__ : stash 제거.
>> + __git stash pop [stash 이름]__ : apply + drop.
>> + __git stash show -p [stash 이름] &#124; git apply -R__ : stash 이름(ex. stash@{2})에 해당하는 stash를 이용하여 거꾸로 적용한다..
>> + __alias__ : 예제 => git config --global alias.stash-unapply '!git stash show -p | git apply -R'

> __용어__
>> + tracked : unmodified, modified, staged
