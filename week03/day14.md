## PR 리뷰
- PR 리뷰할 때 변경된 파일 하나씩 보면서 확인해 보기
- 배포할 때 변경사항 다 스태시나 커밋해야 된다고 해서 gemfile.lock은 변경 내역 취소 처리했다.
- git checkout master 단축어: gcm
- 깃 upstream 풀 해 오는 명령어: glum (단축어)

### 배포 전 PR 리뷰할 때 신경쓸 부분

1. 서버 잘 켜지는지 (rails s)
2. 관리자(staff) 페이지 확인하고(버그 생기면 운영팀이 일을 못하니까)
3. 내가 작업한 곳 잘 되는지 확인

## 배포
- 배포는 회사에서 사용하는 서버에 올리는 것
- 변경사항 생겼을 때 해도 괜찮다(자주 해도 괜찮다)

### 배포 과정
1. 앞으로 2-3달은 배포 전에 developer 채널에 배포한다고 적기(다른 분들이 알 수 있게. 에러 날 수도 있으니)
2. 마스터 브랜치로 체크아웃(gcm)
3. 마스터 브랜치가 최신 버전인지 확인(그 사이에 다른 분들이 커밋하셨을 수도 있으니..?)
4. 반영 안 된 변경사항 없도록(노랑 엑스 없어지도록) 하기(보통 gem 파일 때문인 듯)
5. glum 입력해서 upstream pull
6. bundle exec cap production deploy

## 기기 감지해서 모바일/데스크탑 버전 분기하는 방법
1. 분기용 컨트롤러를 만든다(컨트롤러 만들 때 꼭 rails g controller 안 쓰고 컨트롤러 폴더 안에서 직접 새 파일 추가해도 된다)
2. 컨트롤러 안에서 변수를 하나 만들어서(ex)landing_link) landing_link를 데스크탑 버전 주소로 지정하기
3. routes.rb에서 라우팅 추가(컨트롤러 새로 만들었으니)
4. if문을 써서, 만약 DeviceDetector로 감지한 기기 device_type이 스마트폰이면 landing_link에 모바일 링크 대입
5. landing_link로 리다이렉트
6. 내 폰으로 들어가서 잘 되는지 확인해 보기(ip주소 이용해서)
5. 배포해서 분기처리 내역 반영 

- 참고한 사이트: https://github.com/podigee/device_detector


## vi 편집기 사용법

- i 누르면 편집 모드
- end 누르면 그 줄 맨 끝으로 이동
- 수정 완료했으면 esc 누르고 :wq 눌러서 종료


## 공개키
- 공개키 생성 방버: ssh-keygen
- 이미 있는 공개키 찾으려면 아래 명령어 입력하기

```
cd .ssh
```
- 그리고 그 안에 있는 pub파일 읽어서 공개키를 확인할 수 있다.
- 파일 내용 읽는 명령어:

```
cat '파일명' 
```
- 파일명 일일이 입력하지 않아도 탭키 누르면 현재 폴더 안의 파일 선택할 수 있다(탭 한번, 탭 두 번, … 누르기)
- 서버 컴퓨터(aws나 깃허브)에 내 공개키 정보를 주어서 등록해 두면 서버에 접속하려고 할 때 그 컴퓨터가 내 컴퓨터에 있는 ssh 폴더에서 개인키를 알아서 찾아 간다.

#### 서버 접속 방법
- ssh '서버 주소'

## repository not found 에러

```
ERROR: Repository not found.
fatal: Could not read from remote repository.
```
- 깃 푸시하려고 했을 때 이런 에러가 났다.

```
git remote remove origin
```
이 명령어로 리모트 브랜치와의 연결 끊고 깃허브 데스크탑 버전에서 다시 연결하니까 에러가 사라졌다.

## 레일즈
- http://localhost:3000/rails/info/routes 여기 들어가면 라우팅 정보 한 번에 볼 수 있다.
- 파일 하나로 모바일, 데스크탑 2개 레이아웃 관리하는 방법: content_for 사용

## 기타
- 배포 환경에는 stage, production 등 여러 가지가 있다.
