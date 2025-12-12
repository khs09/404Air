# 404NotFound - 기업 인사 관리 시스템

## 📋 프로젝트 개요

404NotFound는 기업의 인사 관리와 업무 효율화를 위한 통합 웹 애플리케이션입니다. 결재, 근태 관리, 캘린더, 채팅, 시설 예약 등 다양한 기능을 제공하는 풀스택 애플리케이션입니다.

## 🛠 기술 스택

### Backend
- **Framework**: Spring Boot 3.4.9
- **Language**: Java 21
- **Database**: MySQL 8.1
- **Security**: Spring Security
- **WebSocket**: Spring WebSocket (STOMP)
- **Build Tool**: Gradle
- **Mail**: Spring Mail (Gmail SMTP)
- **Validation**: Spring Validation

### Frontend
- **Framework**: React 19.1.1
- **Build Tool**: Vite 7.1.2
- **Routing**: React Router DOM 7.8.0
- **HTTP Client**: Axios 1.11.0
- **UI Library**: Bootstrap 5.3.7, React Bootstrap 2.10.10
- **Calendar**: FullCalendar 6.1.19
- **Maps**: React Google Maps API 2.20.7
- **WebSocket**: STOMP.js 7.1.1, SockJS 1.6.1
- **Icons**: Bootstrap Icons 1.13.1, Lucide React 0.541.0

### Infrastructure
- **Containerization**: Docker, Docker Compose
- **Web Server**: Nginx (Frontend)
- **Application Server**: Tomcat (Embedded)

## 📁 프로젝트 구조

```
Project-master/
├── 404NotFound/              # Backend (Spring Boot)
│   ├── src/
│   │   └── main/
│   │       ├── java/com/pj/springboot/
│   │       │   ├── approval/         # 결재 시스템
│   │       │   ├── arch/             # 자료실
│   │       │   ├── attendance/       # 근태 관리
│   │       │   ├── auth/             # 인증/인가
│   │       │   ├── calendars/        # 캘린더/근무표
│   │       │   ├── chat/             # 채팅 (WebSocket)
│   │       │   ├── common/           # 공통 유틸리티
│   │       │   ├── config/           # 설정 (Security, WebSocket)
│   │       │   ├── facilities/       # 시설 예약
│   │       │   ├── location/         # 위치 서비스
│   │       │   └── recaptcha/        # reCAPTCHA
│   │       └── resources/
│   │           └── application.properties
│   ├── build.gradle
│   └── Dockerfile
│
├── projectreact/              # Frontend (React)
│   ├── src/
│   │   ├── api/              # API 클라이언트
│   │   ├── components/
│   │   │   ├── pages/
│   │   │   │   ├── approval/        # 결재 페이지
│   │   │   │   ├── attendance/      # 근태 페이지
│   │   │   │   ├── boardForm/       # 게시판
│   │   │   │   ├── calendars/       # 캘린더 페이지
│   │   │   │   ├── chatfrom/        # 채팅 페이지
│   │   │   │   ├── Facilities/      # 시설 관리
│   │   │   │   ├── Location/        # 위치 서비스
│   │   │   │   └── LoginForm/       # 인증 페이지
│   │   │   └── Navbar.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   ├── vite.config.js
│   └── Dockerfile
│
├── docker-compose.yml        # Docker Compose 설정
├── 404NotFound.sql          # 데이터베이스 스키마
└── dump.sql                 # 데이터베이스 덤프
```

## ✨ 주요 기능

### 1. 인증 및 인가
- 일반 회원가입/로그인
- 소셜 로그인 (Google, Kakao OAuth)
- 비밀번호 찾기 (이메일 인증)
- reCAPTCHA 통합
- 세션 기반 인증

### 2. 결재 시스템
- 결재 문서 작성/수정/조회
- 결재선 설정 및 승인 프로세스
- 파일 첨부 기능
- 결재 상태 관리 (대기/진행/승인/반려)
- 휴가 신청서 관리

### 3. 근태 관리
- 출퇴근 기록
- 근태 통계 및 조회
- 근태 수정 기능
- 월별/일별 근태 현황

### 4. 캘린더 및 근무표
- FullCalendar 기반 일정 관리
- 근무표 작성 및 조회
- 시프트 메모 기능
- 이벤트 관리

### 5. 채팅 시스템
- WebSocket 기반 실시간 채팅
- 1:1 채팅 및 그룹 채팅
- 채팅방 관리
- STOMP 프로토콜 사용

### 6. 시설 예약
- 시설 등록/수정/삭제
- 시설 예약 신청
- 예약 승인 프로세스
- 내 예약 현황 조회

### 7. 게시판 및 자료실
- 게시글 CRUD 기능
- 검색 기능
- 파일 업로드/다운로드
- 자료실 관리

### 8. 위치 서비스
- Google Maps API 통합
- 위치 정보 조회

### 9. 홈 대시보드
- 날씨 정보 (기상청 API)
- 항공편 정보 (공공데이터 API)
- 실시간 정보 표시

## 🚀 시작하기

### 사전 요구사항
- Java 21 이상
- Node.js 20 이상
- Docker 및 Docker Compose
- MySQL 8.1 (또는 Docker 사용)

### 환경 변수 설정

#### Backend (`404NotFound/src/main/resources/application.properties`)
```properties
# 데이터베이스 설정
spring.datasource.url=jdbc:mysql://localhost:3306/404notfound?serverTimezone=Asia/Seoul&characterEncoding=UTF-8&useSSL=false&allowPublicKeyRetrieval=true
spring.datasource.username=404notfound
spring.datasource.password=1234

# 메일 설정 (Gmail SMTP)
spring.mail.username=your-email@gmail.com
spring.mail.password=your-app-password

# reCAPTCHA
recaptcha.secret=your-recaptcha-secret-key
```

#### Frontend (`projectreact/.env`)
```env
VITE_PUBLIC_API_KEY=your-public-api-key
VITE_KMA_KEY=your-kma-api-key
```

### Docker Compose를 사용한 실행 (권장)

1. **프로젝트 클론**
```bash
git clone <repository-url>
cd Project-master
```

2. **Backend 빌드**
```bash
cd 404NotFound
./gradlew build
cd ..
```

3. **Docker Compose 실행**
```bash
docker-compose up -d
```

4. **접속**
- Frontend: http://localhost
- Backend API: http://localhost:8081/api

### 로컬 개발 환경 설정

#### Backend 실행
```bash
cd 404NotFound
./gradlew bootRun
```

Backend는 `http://localhost:8081`에서 실행됩니다.

#### Frontend 실행
```bash
cd projectreact
npm install
npm run dev
```

Frontend는 `http://localhost:5173`에서 실행됩니다.

### 데이터베이스 설정

1. **MySQL 데이터베이스 생성**
```sql
CREATE DATABASE 404notfound CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER '404notfound'@'localhost' IDENTIFIED BY '1234';
GRANT ALL PRIVILEGES ON 404notfound.* TO '404notfound'@'localhost';
FLUSH PRIVILEGES;
```

2. **스키마 및 데이터 임포트**
```bash
mysql -u 404notfound -p 404notfound < 404NotFound.sql
# 또는
mysql -u 404notfound -p 404notfound < dump.sql
```

## 📦 빌드 및 배포

### Backend 빌드
```bash
cd 404NotFound
./gradlew clean build
# WAR 파일: build/libs/*.war
```

### Frontend 빌드
```bash
cd projectreact
npm run build
# 빌드 결과: dist/
```

### Docker 이미지 빌드
```bash
# Backend
cd 404NotFound
docker build -t 404notfound-backend .

# Frontend
cd projectreact
docker build -t 404notfound-frontend .
```

## 🔧 설정 파일

### Backend 주요 설정
- **포트**: 8081
- **세션 타임아웃**: 무제한 (`-1`)
- **파일 업로드 최대 크기**: 20MB
- **JPA DDL**: `none` (수동 스키마 관리)

### Frontend 주요 설정
- **포트**: 80 (Docker), 5173 (개발)
- **API Base URL**: `/api`
- **Proxy 설정**: Nginx를 통한 백엔드 프록시

## 📝 API 엔드포인트

주요 API 엔드포인트:

- **인증**: `/api/auth/*`
- **결재**: `/api/approval/*`
- **근태**: `/api/attendance/*`
- **캘린더**: `/api/calendars/*`
- **채팅**: `/api/chat/*` (WebSocket: `/ws`)
- **시설**: `/api/facilities/*`
- **게시판**: `/api/arch/*`
- **위치**: `/api/location/*`

## 🔐 보안

- Spring Security를 통한 인증/인가
- 세션 기반 인증
- reCAPTCHA 통합
- CORS 설정
- SQL Injection 방지 (JPA 사용)
- XSS 방지

## 📄 라이선스

이 프로젝트는 교육 목적으로 개발되었습니다.

## 👥 개발팀

404NotFound Team

## 📞 문의

프로젝트 관련 문의사항이 있으시면 이슈를 등록해주세요.

---

**참고**: 프로덕션 환경에서는 다음 사항을 반드시 변경하세요:
- 데이터베이스 비밀번호
- 메일 계정 정보
- reCAPTCHA 시크릿 키
- API 키들을 환경 변수로 관리
- HTTPS 설정
- 보안 설정 강화

