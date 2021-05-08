https://github.com/ParkCH753/MarkDownAssignment

<br>MarkDown 설명서를 작성할 것입니다. <br>
혼자하면 꽤나 걸릴 것 같은데 다행히 같이 해준다는 친구가 있어서 친구와 협력을 하려고 합니다.<br>
그럼 먼저 저희가 git과 github을 사용할 줄 알아야겠네요. git 사용법부터 익혀볼까요?<br>
<br>

# 0. git 기본설정
먼저 git을 사용하기 위해 기본적인 설정부터 하려고 합니다.
<br>
<br>

## git 명령어의 구성

git 명령어는 맨 앞에 git을 붙이고 뒤에 명령어, 옵션 등을 붙입니다.

    git (명령어) [이러저러 옵션]



각각의 명령어마다 많이 쓰이는 것은 나중에 설명하겠지만 필요한 경우 `-help` 옵션을 통해 사용법이나, 옵션 등을 확인할 수 있습니다.

<br><br><br>

## git 폴더 설정

### init

먼저 작업을 할 폴더로 이동해준뒤 이 폴더에서 git으로 작업을 할 것이라는 표시를 해주어야 합니다.

![0_fordercreate](https://user-images.githubusercontent.com/81542290/117533900-14dbdb80-b02a-11eb-8973-0f77d94eaa9b.png)
![1_init](https://user-images.githubusercontent.com/81542290/117533850-e6f69700-b029-11eb-98ab-e2ad3742624b.png)<br>

<br>
리눅스와 동일하게 파일을 만들어준뒤

    mkdir MarkDownAssignment

파일로 이동합니다. (물론! 이미 진행중인 작업물이 있는 곳으로 이동만 해도 됩니다.)

    cd MarkDownAssignment

그리고 다음 명령어를 입력해 이 파일을 git이 관리하는 파일로 만듭니다.

    git init

이 명령어를 수행하면 폴더에 `.git`폴더가 생성됩니다.

<br><br><br>

## git 사용자 설정
git으로 기록을 남길 땐 작성자가 누구인지 알려야 합니다. 그러니 먼저 git에다가 사용자의 정보를 입력해 줍시다.<br>



![2_config](https://user-images.githubusercontent.com/81542290/117533851-e78f2d80-b029-11eb-8ac1-49ca73543797.png)

<br>
이름과 이메일을 등록할 경우 다음과 같은 명령어를 입력합니다.


    git config --global user.name "ParkCH"
    git config --global user.email qpwoei3388@naver.com

`config`는 git에서 설정을 담당한다고 생각하면 될 것 같습니다.
git에 대한 여러가지 정보를 수정하고 설정할 수 있습니다.<br>
다음 통해 git의 여러 설정사항들을 한눈에 볼 수 있습니다.

    git config --list


<br><br><br><br>

# 1. 파일 git에 저장하기

파일도 만들고 열심히 설명서를 작성하다가 왔습니다. 오늘은 여기까지 하고 백업파일을 만들어 git에 올려볼까요?


### status
먼저 git에 작업을 하기 위해서는 파일들의 상태를 보아야 합니다.<br>
다음 명령어로 확인할 수 있습니다.

    git status


![3_status](https://user-images.githubusercontent.com/81542290/117533852-e78f2d80-b029-11eb-84c4-b4adbb439a85.png)

<br>보아하니,, 빨간색으로,, 우리가 작성한 설명서가 있고 untracked 되어있다고 뜨네요?<br>

git에다가 버전을 만드는 것을 `commit`이라고 합니다. 그런데 git은 버전을 만드는데 있어서 쓸데없는 파일들까지 commit 하는 것을 방지하기 위해 파일 각각을 올려서 commit하도록 되어있습니다.

### add
즉, 먼저 git이 어떤 파일들을 commit할지 선택을 해주면 그 파일들만 일괄 commit한다는 뜻입니다. <br> 우리는 `add` 명령을 통해 git이 파일을 추적하도록 해줄 수 있습니다.
추가해준 뒤 상태를 다시 볼까요?
<br><br>


    git add MarkDownAssignment.md
    git status

<br>![4_add](https://user-images.githubusercontent.com/81542290/117533853-e827c400-b029-11eb-8003-2676d1d83f69.png)<br><br>

오 초록색으로 뜨니까 그래도 조금 기분이 좋네요.
### commit
이제 올라간 파일들은 모두 commit을 할 수 있는 파일들이라는 뜻입니다. 이제 진짜 commit만 해주면 되겠네요! <br><br>

    git commit -am "First commit"
    git log

![5_commit](https://user-images.githubusercontent.com/81542290/117533854-e827c400-b029-11eb-9c65-985fb2f3c92f.png)
<br><br> 명령어 뒤에 붙은 `"First commit"`은 이 버전에 대한 설명을 의미합니다. 로그에서 이 버전이 어떤 수정사항/내용의 버전인지 확인할 수 있습니다.

### log
로그에 보면 먼저 작성자와 이메일, 등록시간이 나오고 노란색으로 오버플로우가 일어난 것만 같은 문자열이 하나 보입니다.
이 문자열이 log의 ID로 나중에 버전들을 식별할 때 사용됩니다.<br><br>

|옵션| 용도| 
|---|---|
| -m |간단한 메모|
| -a | add 생략 |

<br>

먼저 `-m`은 버전의 메모를 간단하게 작성할 때 사용합니다. `-m`이 없이 사용하면 vim이 열리면서 메모를 작성하게 되는데, `-m`을 붙이면 명령행 뒤에 적어만 주어도 됩니다.

`-a`는 앞에서 나온 add명령을 사용하지 않고 모든 파일들을 commit해버리는 옵션입니다. 지금같은 간단한 작업에는 훨씬 편리합니다.
<br><br><br><br>

# 2. 버전 관리하기

버전을 만들기는 했는데,, 이전으로 되돌아가거나 삭제하는 건 어떻게 하는 걸까요? <br>하는 김에 이것까지 알아봅시다.
<br><br>

## 1) 버전 삭제하기

작업을 하고 나서 버전을 하나 더 만들게 되었습니다.<br> log가 두개가 되었죠?

![6_log2](https://user-images.githubusercontent.com/81542290/117533855-e8c05a80-b029-11eb-9f90-b9048623be8f.png)


`(HEAD ->master)`가 지금 현재 파일의 ???

근데 작업을 하고 나니,, 어째 처음에 한걸로 돌아가는게 나아보입니다. <br>
작업한 내용은 과감히 삭제하고 한번 되돌아가 봅시다.

명령어는 다음과 같습니다.

    git reset --hard "돌아가고 싶은 버전 ID"

<br>실제로 실행해볼까요? 첫번째 버전의 ID를 넣어보겠습니다.

    git reset --hard 451b80db7cb66c543facfbf05f4de2aa04f19645

![7_reset](https://user-images.githubusercontent.com/81542290/117533857-e8c05a80-b029-11eb-8cdf-ef270ec17068.png)


HEAD가 First commit에 위치한다고 뜨면서 log에도 두번째 커밋이 보이지 않네요.

`--hard`는 보시는 그대로 reset의 옵션중 하나입니다. 말그대로 하드한 reset으로 완전한 삭제를 의미합니다.


이외에 아무것도 붙이지 않은 `--mixed`와 `--soft` 도 있습니다.
<br><br><br>

## 2) Tag 붙이기
중간정도 작업을 마쳤고 이전부분 수정사항은 없을 거 같으니 Tag를 이용해서 표식을 만들어볼까요? 
<br> 태그를 이용하면 태그를 붙인 버전을 찾아오기도 쉽고 릴리즈하듯이 이 버전을 고정시킬 수 있어요. 
<br> 중간단계 완성 표식정도로 보면 되겠네요!

1.0v라는 Tag를 한번 붙여봅시다!
    
    git tag 1.0v    //tag 붙이기
    git tag         //tag 목록 보기
    git log

![8_tag](https://user-images.githubusercontent.com/81542290/117533859-e958f100-b029-11eb-8276-12870aa991b8.png)

태그 목록과 로그에 Tag가 붙여진 걸 볼 수 있습니다. 

이외에 다음 옵션들을 이용해서 Tag를 조작할 수 있습니다.

|옵션|용도|
|---|---|
|-a | 주석이 달린 태그 생성<br><code>git tag -a <태그이름>|
|-am | 주석 바로 입력<br><code>git tag -am "주석"|
|-n| 주석과 함께 tag 목록 보기 <br><code>git tag -n|
|-d| 주석 삭제<br><code>git tag -d <태그이름>|
<br><br><br><br>

# 3. branch로 작업하기
작성하다보니 이제 6번, 코드 부분을 작성할 때가 되었네요. <br>그런데 지금까지는 예시구문을 박스 안에다 넣었는데 코드구문은 자체로 박스가 있어서 박스 안에다가 할지, 그냥 코드 구문으로 할 지 고민이 되는 것 같아요.<br>
마음 같아서는 전 둘 다 만들어보고 싶은데 그렇게 하자니 파일을 전체 다 복사해야 하고,, 번거로울 거 같아요.

이때 사용할 수 있는 기능이 바로 branch 기능이에요!<br>
branch는 말 그대로 가지를 친다는 의미로, 한 작업을 따로 한 후 병합하거나, 작업을 동시에 병행해 나중에 병합하는 식으로 작업을 가능하게 해줘요.
<br><br>

## 1) branch 생성

어려우니까 바로 볼까요?
<br>먼저 branch라는 걸 만들어봅시다.

<br>

    git branch box      //box라는 branch 생성
    git branch          //branch 목록
    git log

![9_CreateBranch](https://user-images.githubusercontent.com/81542290/117533861-e9f18780-b029-11eb-8713-51acfeeb1d45.png)

branch라는건,, 윳놀이 말이라고 생각해도 될 것 같아요. 각자 위치에서 있다가 움직이고 싶을 때 말을 골라서 움직이면 되듯이 지금은 현재 버전에 box라는 말을 놓은 거에요. 

따로 생성하지 않아도 가장 처음부터 있는 말은 master라고 네이밍되어있어요. 지난번에 그냥 지나갔지만 log ID 옆에 보이던 HEAD -> master표시에서의 master가 이것이었어요.

### scheckout
HEAD는 내가 지금 바라보고 있는 branch의 위치를 뜻해요. 만약 HEAD가 box를 가르키고 있는 건 사용자가 box의 위치에서 작업을 하겠다는 뜻이죠.<br>
지금은 HEAD가 master를 가리키고 있으니까 box로 시선을 옯겨준다음, 설명서를 box형식으로 만들어볼까요?

<br>

    git checkout box
    git branch

![10_Checkout](https://user-images.githubusercontent.com/81542290/117533862-e9f18780-b029-11eb-8f01-b730a1101bec.png)

branch 목록과 하늘색 글씨를 통해서 누가봐도 box로 시선이 옮겨진 걸 알 수 있겠죠? 이제 이 상태에서 작업을 한 후, commit을 하면 branch와 master는 다른 방향으로 제 갈길 찾아서 commit이 돼요.<br>
그래서 box에서 작업을 하다가 master로 checkout해주면 master가 있던 버전으로 돌아가게 돼요.

<br><br>
## 2) branch마다 작업
그럼 일단 box로 가서 수정을 해준 뒤 commit을 하고 다시 master로 돌아와서는 코드블럭으로 작성하는 걸로 해볼게요!
<br>

    //box로 설명서 작업
    git commit -am "write 6.CODE in box"        //box에 버전 생성
    git checkout master                         //master로 이동

    //code box로 설명서 작업
    git commit -am "write 6.CODE in code box"   //master에 버전 생성
    git log --graph --all --decorate            //전체 branch 상황 그래프로 표현
    

![11_BranchLog](https://user-images.githubusercontent.com/81542290/117533863-ea8a1e00-b029-11eb-9bd5-ca263d353395.png)

그림을 보니 왜 이름이 branch라고 붙었는지 조금은 이해가 가시죠?

<br><br>

## 3) branch 병합하기
그런데 작업을 하고 보니 '6.코드작성'부분은 그대로 코드 블록을 이용하는 것이 좋을 것 같고,, '6.1코드'부분은 하던대로 box로 하는 것이 좋을 것 같아요! <br>그럼 이때 두 파일을 부분부분 가져와서 병합해야겠죠? 이때 사용할 수 있는 명령어가 rebase와 merge입니다.
<br>둘 다 파일들을 병합한다는 것은 동일한데, 로그를 어떻게 남기느냐의 방식이 조금 다릅니다.
<br><br>

> ## 주의!
>두 명령어들의 차이점을 설명하기 전에 먼저 병합할 때의 주의점을 짚고 넘어갈게요! <br>
병합을 진행하게 되면 두 branch의 다른 작업상황들이 하나의 버전으로 뭉치게 돼요. 그런데 만약 같은 파일의 동일한 행의 작업 상황이 다르다면 git은 둘 중 어느 것으로 병합해야 할 지 모르기 때문에 이러한 충돌 상황에서는 병합을 하지 못하도록 만들어요.그래서 실제로는 동일한 파일을 여러 개발자가 수정하지 못하도록 정해놓는 식으로 작업이 이루어져요.
>
>그런데 우리 설명서는 형식은 동일하더라도 box branch의 부분과 master branch의 부분의 '6.코드블럭'부분이 겹치게 되어서 conflict가 발생하게 될거에요.
><br>저희는 box 부분의 '6.1코드'만 가져오고 '6.코드블럭' 은 master 것을 쓰려고 하니까 box의 '6.코드블럭'부분을 master부분의 것으로 동일하게 바꿔주던가 해서 충돌을 없애줘야 해요.
>
> 항상 아름답게 병합이 되면 좋겠지만,, 이 작업은 개발자들에게는 꽤나 번거로운 작업이에요.
> <br>이후 설명에서는 충돌이 생기지 않도록 수정된 상태에서 진행하도록 할게요!<br>
>       
>       git checkout box
>       //수정
>       git commit -am "conflict fix"
>       git checkout master
>
![12_ConflictFix](https://user-images.githubusercontent.com/81542290/117533844-e4943d00-b029-11eb-95ac-75ce20fe5072.png)


<br><br>

### merge
먼저 merge부터 알아보겠습니다.  merge는 모든 로그를 그대로 남기면서 병합합니다. 사진을 보는 것이 훨씬 이해가 빠를 것 같으니 바로 해보도록 하죠.

    git merge box //master를 box와 병합

![13_merge](https://user-images.githubusercontent.com/81542290/117533845-e5c56a00-b029-11eb-9d0e-175114c382dc.png)

와! 잘 합쳐졌네요 ㅎㅎ

### rebase
rebase도 동일하게 병합을 할 때 사용하는 명령어입니다. 하지만 조금 다른 것은 버전 기록에 있어서 조금 다르다고 말씀드렸죠?

merge는 방금처럼 두 갈래로 갈라졌던 것이 그대로 남지만 rebase는 병합하면서 버전들의 log들도 한번에 합쳐 깔끔하게 만들어줍니다.

    git rebase box

![14_rebase](https://user-images.githubusercontent.com/81542290/117533846-e5c56a00-b029-11eb-8865-e26f0c571ec1.png)

이렇게 말이죠!

<br><br><br><br>
# 4. Github에 올리기
처음에 말했던 도와준다던 친구가 도와주겠다며 github에 파일을 올려달라 그러는데,, Git과 Github을 연동시키는 방법도 알아야겠네요!
<br>(독자분 Github아이디는 있으시죠? 없다면 만들고 옵시다.)

<br>

## 1) github과 연결하기
github에 들어가셔서 과제를 위한 새로운 Repository를 만들어줍시다.

잘 만드셨면 다음 커멘드를 입력하라고 뜰 거에요. 그대로 입력해줍시다!
### remote
    git remote add origin https://github.com/ParkCH753/MarkDownAssignment.git
    git branch -M main
    git push -u origin main

일단 첫번째 문장은 origin이라는 이름으로 github의 주소를 저장하겠다는 의미로 보시면 돼요!


### push
그리고 Main이라는 branch를 만들어주고 세번째 문장을 통해서 origin으로 현재 branch의 내용을 넣어준다는 의미에요.<br>
그리고 push 뒤에 준 옵션 덕분에 이후로 push작업을 할때는 뒤에 옵션 없이 사용하면 돼요.

    git push

이제 github 페이지에 들어가면 저희가 작성한 코드가 있는 걸 볼 수 있어요.

## 2) github에서 파일 가져오기
github에 올렸더니 친구가 README.md 파일을 작성했다고 하네요?
<br> 한번 가져와봅시다. 사용하는 명령어는 `pull`이에요!
<br> 앞에서 push할 때 -u 옵션을 붙여둔 덕분에 여기서도 그냥 `pull`만 사용하면 돼요.
### pull

    git pull
    
![15_pull](https://user-images.githubusercontent.com/81542290/117533847-e65e0080-b029-11eb-8bc9-0f91171dab40.png)

그럼 저희도 설명서를 마저 작성하고 github에 올린 뒤 마무리해볼까요?



<br><br><br>

### clone

몇번 헤매긴 했지만 일단 설명서는 우여곡절 끝에 github에 다 올렸네요. 이왕김에 clone 명령어도 배워보도록 할까요?<br>
clone은 pull하고 동일한 효과를 내요. 하지만 다른 점은, clone은 github등의 저장소에 있는 repository를 쌩 처음 파일에 가져올 때 사용하고 pull은 자유롭게 가져온다는 차이가 있죠.

새로운 폴더를 만들고 clone을 한번 시험해볼까요?<br>

    git clone https://github.com/ParkCH753/MarkDownAssignment

![16_clone](https://user-images.githubusercontent.com/81542290/117533848-e65e0080-b029-11eb-9e98-9de4e1235df1.png)

아까 clone은 처음 생성할 때 사용하는 것이라 했죠? 그래서 따로 `git init`하지 않은 상태에서 진행해도 clone이 생성돼요.


<br>

그럼 이상으로 git 설명은 마칠께요. 수고했어요!

|명령|위치|
| :---:| :---: |
|init|[init](#init)|
|config|[config](#git-사용자-설정)|
|status|[status](#status)
|add|[add](#add)
|commit|[commit](#commit)|
|log|[log](###log)|
|reset|[reset](#1\)-버전-삭제하기)|
|--hard|[--hard](#1\)-버전-삭제하기)|
|tag|[tag](#2\)-Tag-붙이기)|
|branch|[branch](#1\)-branch-생성)|
|checkout|[checkout](#checkout)|
|merge|[merge](#merge)|
|rebase|[rebase](#rebase)|
|remote|[remote](#remote)|
|push|[push](#push)|
|pull|[pull](#pull)|
|clone|[clone](#clone)|
