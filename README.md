# nlp-remote-container

NLP Experiment environment with remote docker container and vscode

<img src = 'https://code.visualstudio.com/assets/docs/remote/containers/architecture-containers.png'>

## How to setup

### step 0) vscode와 원격 도커 서버를 함께 사용하기.
- 아래와 같은 extension들을 설치해야됨.
    - Remote Development
    - Docker
- settings에 도커 host 추가하기.
    - 근데 문제는 저렇게 하면 내 로컬의 도커 컨테이너에 접근할 수가 없음ㅠ

```json
{
    "docker.host": "ssh://USERNAME@IP"
}
```

### step 1) `devcontainer.json`을 통해 나의 컨테이너 환경을 정의하자.
- Dockerfile로 나만의 개발 환경 구성.
    - base image를 서버의 cuda/cudnn 설정에 맞춰서 nvidia docker image를 활용해라.
    - 하나의 환경에 pytorch, tensorflow, onnxruntime을 함께 설치하려면, 적합한 cuda/cudnn을 찾아야됨.
- appPort를 통해 컨테이너의 포트포워딩 설정을 해주자.
- settings로 본인의 도커 환경에 맞게 vscode의 세팅을 정의해주자.
- postCreateCommand로 파이썬 패키지를 최신 버전으로 설치해주자.

### step 2) NLP 프로젝트 시작하기
- 본 repository를 templates으로 하여 repo 생성.
- vscode에서 `Clone Repository in Docker Volume`을 통해 컨테이너를 실행.
- ENJOY!!!

## nlp 환경 구분 
- branch
    - `cu+101`
        - pytorch 1.8 with cuda 10.1
        - tensorflow 2.3.1
        - onnxruntime 1.4.0