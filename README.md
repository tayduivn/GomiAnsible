# GomiAnsible V1.0

## Wellcome!

### 시작하기


`GomiAnsible`은 고미 개발팀이 번거로운 수동 배포의 불편함과 불확실성을 줄이고 본질적인 작업에 집중하는 것을 돕습니다.
간단한 명령어로, 대상 제품의 특정 환경에 일련의 배포과정을 자동 수행하는 것이 주 기능입니다.

당신의 기능 브랜치를 스토어 스테이징서버에 배포 해보세요! 
`gomsible deploy -t store -e staging -b feat/your-feature-branch`

---
_* 이 프로젝트는 `Ansible`을 사용합니다._
_`zshell`을 사용하는 것을 가정하고 작성되었습니다._

1. 먼저 ansible을 설치해야 합니다.
```
~ $ brew update
~ $ brew install ansible
```
차 한 잔 마시며 기다립시다. ☕️

2. 설치가 끝나면 확인해봅시다
```
~ $ ansible -h
~ $ ls ~/.ansible
```
홈 디렉토리에 있는 `.ansible` 폴더! 우리는 저 고지를 점령할겁니다.

3. `GomiAnsible` 레포를 클론 받습니다 그리고 gomsible command를 읽어옵니다.
```
~ $ git clone https://github.com/gomicorp/GomiAnsible.git
~ $ cd GomiAnsible
~/GomiAnsible $ source bin/gomsible
```

4. `gomsible init` 명령어를 실행합니다. 이 명령어에서는 세가지 작업을 수행합니다.
  - 소스 코드를 반영하기 위한 git 명령에 필요한 account config 등록
  - `GomiAnsible`dir을 `.ansible`dir로 덮어쓰기
  - `gomsible` 명령어를 전역으로 사용하기 위한 path 등록

5. init을 성공적으로 완료하면 확인해봅시다.
```
$ gomsible -h


================================================
Wellcome to Gomi Ansible!
Please read README
https://github.com/gomicorp/GomiAnsible/
================================================
```

6. 여기까지 진행하셨다면 성공적으로 초기화를 완료하셨습니다! 🎉

### deploy
원하는 서버의 원하는 환경에 코드를 배포하는, ~무서운~ 😇 명령어입니다.
`-t` : target 옵션입니다. 배포하고자 하는 제품명을 입력해주세요. 현재는 가능한 타겟은 store / api 가 있습니다.
`-e` : envronment 옵션입니다. 현재 가능한 환경은 staging / production 이 있습니다.
`gomsible deploy -t store -e staging`

`-b` : branch를 명시하는 옵션입니다. 생략 가능합니다. 
명시하는 경우 해당 branch를 바라보고 배포됩니다. ※ production에서는 작동하지 않습니다 ※
생략하는 경우 브랜치 스위칭 없이 현재 브랜치를 그대로 최신화 하여 배포합니다.
`gomsible deploy -t store -e staging -b develop` 

`--hoxfix` : production 환경은 deploy명령을 수행할 때 master branch를 유지하도록 동작합니다. 
다만 hotfix옵션을 주면 브랜치 스위칭 없이 현재 브랜치를 그대로 최신화하여 배포합니다.
`gomsible deploy -t api -e production --hotfix`

### secredit
init에서 입력한 git account config를 수정할 수 있습니다.
내부적으로 아래의 명령을 수행합니다.
`ansible-vault edit ${ANSIBLE_PATH}/secrets.yml`

### setdir
init에서 수행한, `GomiAnsible`dir을 `.ansible`dir로 교체하기 작업을 수행합니다.

---
새로운 커밋은 언제나 환영입니다!
