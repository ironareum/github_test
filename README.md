# 로컬저장소 생성하기

0. 로컬 저장소로 사용할 폴더 생성
1. README.md 파일 생성
2. 터미널 실행

```unix
$ git => 기존에 git 다운로드 되어있다는 전제하에. git 정보 확인
$ cd '폴더명' => 로컬 저장소로 이동
$ git init => 리포지토리 생성 (.git 폴더 생성된거 확인 == 로컬 저장소)
```

# COMMIT 하기

```
//버전관리를 위한 내 정보 등록 (커밋시 사용될 깃허브 정보)
$ git config --global user.email "깃허브이메일주소"
$ git config --global user.name "깃허브닉네임"

//커밋하기
$ git add README.md
$ git commit -m "커밋 내용 작성" => 로컬저장소에 등록

//다른 커밋으로 시간 여행하기
$ git log => 커밋 기록 확인 가능
$ git checkout "커밋정보 앞7자리" => 해당 커밋으로 이동
```

# 원격저장소에 커밋 올리기

1. 깃허브에 리포지토리 생성 후 url 복사

```
$ git remote add origin "리포지토리url주소" //로컬저장소에 원격저장소 주소 알려주기
$ git push origin master //로컬 저장소 내용 => 원격저장소에 등록
=> github 로그인창에서 계정정보 입력하기
=> 내 깃허브 리포지토리에서 push된 소스 확인하기
```

# 원경저장소의 커밋을 로컬 저장소에 내려받기

```
$ git clone "리포지토리url" . <== 뒤에 꼭 (스페이스) . 점 해줘야됨!!!!(현재경로)
```

# Branch

master 브랜치를 base로 두고 새로운 branch들을 생성해서 개별 작업 후 추후에 합침

# Merge : 소스 병합

- Merge의 종류 3가지

  1. Merge commit (병합 커밋) : 새로운 커밋 (추가/삭제 되는 파일이 있는경우)
  2. Fast-forward (빨리 감기) : 기존 커밋과 동일(새로 추가되거나 충돌나는 파일이 없음, 파일생성 갯수가 동일한 경우)
  3. Conflict (충돌) : 둘중 어느것을 커밋해야 할지 모르겠는 경우

- 두 브랜치를 합치는 과정 [기준(base): master | 개별브랜치들]
  Pull Request: 내가 개발(수정)한 소스를 병합해달라고 pull 요청하기 \*개별 브랜치들에서 mater로 병합하고 싶을때 Pull Request 보내는게 예의다!

# Patch

= 소스트리 새로고침

# Release

= 프로그램 출시

- 배포: 병합을 마친 master 브랜치를 서버에 올려서 사용자들이 쓸 수 있도록 하는것
- 버전 명시 필요 : 최초: v1.0.0
  이후 버전 업그레이드 : 메이저 v2.x -> v3.x / 마이너 v2.3 -> v2.4
- LTS(long time support)
  ex) 10.15.0
  메이저 버전인 10, 마이너 버전인 5, 그리고 세번째 버전이 있음을 알수있음. 이는 메인테넌스(maintenance)버전으로 버그나 유지보수 등 작은 수정이 들어갔을때 변경함

  1. Tag : 특정 커밋에 포스트잇 붙이기

// 다시 커밋 ===================

# Contribute: 둘 이상의 원격저장소로 협업하기

## branch vs fork

    1. branch: 하나의 원본저장소에서 분기를 나눔
    2. fork: 여러 원격저장소를 만들어 분기를 나눔

[컨트리뷰터 입장]

1. 컨트리뷰트 원하는 저장소(=원본저장소)에서 fork하기 (= 내 원격저장소에 fork한 소스 리포지토리 생김)
2. 소스트리를 이용해 내 로컬 저장소에 저장하기 (내 계정의 fork한 리포지토리 url을 이용)
3. 수정작업
4. 컨트리뷰트 원하는 저장소(원본저장소)에 pull request 보내기 (fork한 원격저장소에서 원본저장소로 코드 합치기)

[원본저장소 입장]

1. fork/pull request 확인
2. File changed 탭을 클릭해 컨트리뷰트 코드 확인(=코드리뷰)
3. 코드리뷰 완료 후, 우측 상단의 Review changes를 클릭
   => Comment(댓글만 달기) / Approve (댓글 + 코드병합) / Request changes (수정 요청) 선택 후 Submit 클릭
4. Approve Submit 후, Merge pull request 로 병합하기
5. 병합 완료 후 원본 저장소에 소스 반영 확인 및 Insights 탭의 Contributors에 내 계정 확인 가능

# rebase : 묵은 커밋을 새 커밋으로 이력 조작하기
