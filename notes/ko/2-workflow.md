# WorkFlow (yml)

```yml
# 1. Workflow 이름 (GitHub Actions 탭에 표시됨)
name: My First CI/CD Pipeline

# 2. Event (언제 이 파이프라인을 실행할 것인가?)
on:
  push:
    branches: [ "main" ] # main 브랜치에 push될 때 실행
  pull_request:
    branches: [ "main" ] # main 브랜치로 PR 날릴 때 실행

# 3. Jobs (독립적인 작업 단위, 여러 개 설정 가능)
jobs:
  build-and-test:
    # 실행 환경 (Cloud Engineer라면 리눅스 환경에 익숙해져야 함)
    runs-on: ubuntu-latest

    # 4. Steps (Job 안에서 실행할 구체적인 단계들)
    steps:
      # (1) 코드 가져오기 (Checkout)
      - name: Checkout repository code
        uses: actions/checkout@v4

      # (2) 언어/환경 세팅 (예: Node.js)
      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      # (3) 의존성 설치 (Build 준비)
      - name: Install dependencies
        run: npm install

      # (4) CI의 핵심: 테스트 실행
      - name: Run tests
        run: npm test

      # (5) 결과 출력 (실제 배포 대신 간단한 확인)
      - name: Check build status
        run: echo "Build and Test completed successfully!"
```


## Keywords
- `on` (Event): 
  - 트리거. "언제 로봇을 깨울까?"를 정함.
- `jobs`: 
  - 작업 묶음. 기본적으로 여러 Job을 설정하면 병렬로 돌아감.
- `runs-on`: 
  - 가상 서버 종류. 보통 ubuntu-latest를 가장 많이 씀.
- `uses`: 
  - 남들이 만들어 놓은 오픈소스 액션을 가져다 쓰는 것. (예: actions/checkout은 내 코드를 가상 서버로 복사해오는 표준 액션임)
- `run`: 
  - 직접 터미널 명령어를 실행할 때 씀.