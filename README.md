# Nginx Proxy Manager Docker 설정

이 저장소는 [Nginx Proxy Manager](https://nginxproxymanager.com/)를 Docker를 사용하여 쉽게 설정할 수 있도록 구성되어 있습니다.

## 개요

Nginx Proxy Manager는 Nginx 웹 서버를 관리하기 위한 직관적인 웹 인터페이스를 제공합니다. 이를 통해 호스트, 프록시 호스트, 리다이렉션, 스트림 등을 쉽게 관리할 수 있으며, Let's Encrypt SSL 인증서 발급 및 갱신도 자동으로 처리할 수 있습니다.

## 사용 방법

### 사전 요구 사항

- Docker 설치
- Docker Compose 설치

### 시작하기

1. 저장소를 클론합니다:

```bash
git clone <repository-url>
cd <repository-directory>
```

2. 데이터 저장을 위한 디렉토리를 생성합니다:

```bash
mkdir -p data letsencrypt
```

3. Docker Compose를 사용하여 컨테이너를 시작합니다:

```bash
docker-compose up -d
```

4. 브라우저에서 관리 UI에 접속합니다:

```
http://localhost:81
```

5. 초기 로그인 정보:

   - 이메일: `admin@example.com`
   - 비밀번호: `changeme`

6. 첫 로그인 후 관리자 계정 정보를 변경하세요.

## 포트 정보

- **80**: HTTP 트래픽
- **81**: Nginx Proxy Manager 관리 UI
- **443**: HTTPS 트래픽

## 볼륨 정보

이 설정은 Docker 볼륨 대신 로컬 디렉토리를 사용합니다:

- **./data**: Nginx Proxy Manager 설정 및 데이터가 저장되는 로컬 디렉토리
- **./letsencrypt**: Let's Encrypt SSL 인증서가 저장되는 로컬 디렉토리

이렇게 하면 컨테이너가 삭제되어도 데이터가 로컬 디렉토리에 보존되며, 데이터 백업 및 관리가 더 쉬워집니다.

## 참고 사항

- 프로덕션 환경에서는 보안을 위해 기본 관리자 계정 정보를 반드시 변경하세요.
- 방화벽 설정이 필요한 경우 위에 명시된 포트들을 개방해야 합니다.
- SSL 인증서를 사용하려면 도메인이 서버의 공용 IP로 올바르게 연결되어 있어야 합니다.
- 로컬 디렉토리에 대한 적절한 권한 설정이 필요할 수 있습니다.

## 문제 해결

문제가 발생할 경우 다음 명령어로 로그를 확인할 수 있습니다:

```bash
docker-compose logs -f
```

## 추가 자료

- [Nginx Proxy Manager 공식 문서](https://nginxproxymanager.com/guide/)
- [jc21/nginx-proxy-manager GitHub 저장소](https://github.com/jc21/nginx-proxy-manager)
