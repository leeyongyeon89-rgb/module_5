# TODO List

## Feature: 로그인/회원가입 기능

### 1. DB 작업 (db-agent)

- [ ] User 모델 생성
  - [ ] 테이블 필드 정의 (id, username, email, password_hash, created_at, updated_at)
  - [ ] 고유 제약조건 설정 (email, username)
- [ ] User CRUD 함수 작성
  - [ ] `create_user()` - 새 사용자 생성
  - [ ] `get_user_by_email()` - 이메일로 사용자 조회
  - [ ] `get_user_by_username()` - 사용자명으로 조회
  - [ ] `get_user_by_id()` - ID로 사용자 조회
- [ ] DB 테스트 작성
  - [ ] User 모델 생성 테스트
  - [ ] 중복 이메일/사용자명 제약 테스트

### 2. BE 작업 (be-agent)

- [ ] Pydantic 스키마 정의
  - [ ] `UserCreate` - 회원가입 요청 스키마
  - [ ] `UserLogin` - 로그인 요청 스키마
  - [ ] `UserResponse` - 사용자 정보 응답 스키마
  - [ ] `Token` - JWT 토큰 응답 스키마
- [ ] 인증 유틸리티 구현
  - [ ] 비밀번호 해싱 함수 (bcrypt/passlib)
  - [ ] 비밀번호 검증 함수
  - [ ] JWT 토큰 생성 함수
  - [ ] JWT 토큰 검증 함수
- [ ] 인증 API 엔드포인트 생성
  - [ ] `POST /api/auth/register` - 회원가입
  - [ ] `POST /api/auth/login` - 로그인
  - [ ] `GET /api/auth/me` - 현재 사용자 정보 조회
  - [ ] `POST /api/auth/logout` - 로그아웃 (선택)
- [ ] 인증 의존성/미들웨어
  - [ ] `get_current_user()` - JWT에서 현재 사용자 추출
  - [ ] 보호된 라우트에 적용
- [ ] API 테스트 작성
  - [ ] 회원가입 성공/실패 테스트
  - [ ] 로그인 성공/실패 테스트
  - [ ] 인증된 요청 테스트

### 3. FE 작업 (fe-agent)

- [ ] 로그인 페이지 구현
  - [ ] `/login` 페이지 생성
  - [ ] 로그인 폼 컴포넌트 (이메일, 비밀번호)
  - [ ] 폼 유효성 검사
  - [ ] 에러 메시지 표시
- [ ] 회원가입 페이지 구현
  - [ ] `/register` 페이지 생성
  - [ ] 회원가입 폼 컴포넌트 (사용자명, 이메일, 비밀번호, 비밀번호 확인)
  - [ ] 폼 유효성 검사
  - [ ] 에러 메시지 표시
- [ ] API 연동
  - [ ] 로그인 API 호출 함수
  - [ ] 회원가입 API 호출 함수
  - [ ] 현재 사용자 정보 조회 함수
- [ ] 인증 상태 관리
  - [ ] AuthContext 생성 (Context API)
  - [ ] 토큰 로컬 스토리지 저장/불러오기
  - [ ] 로그인 상태 전역 관리
- [ ] 보호된 라우트 처리
  - [ ] 인증 확인 컴포넌트/HOC
  - [ ] 미인증 시 로그인 페이지로 리다이렉트
- [ ] 네비게이션 업데이트
  - [ ] 로그인/회원가입 링크 추가
  - [ ] 로그인 상태에 따른 메뉴 표시 (로그아웃 버튼 등)
- [ ] 컴포넌트 테스트 작성
  - [ ] 로그인 폼 렌더링 테스트
  - [ ] 회원가입 폼 렌더링 테스트
  - [ ] API 호출 인터랙션 테스트

---

## 작업 순서 (권장)

1. **DB 작업** (db-agent) - User 모델 및 CRUD 정의
2. **BE 작업** (be-agent) - 인증 로직 및 API 엔드포인트 구현
3. **FE 작업** (fe-agent) - 로그인/회원가입 UI 및 API 연동

---

## 참고사항

- JWT secret key는 환경변수로 관리 (.env 파일)
- 비밀번호는 반드시 해싱하여 저장 (bcrypt 권장)
- CORS 설정 확인 (FastAPI에서 프론트엔드 도메인 허용)
- 토큰 만료 시간 설정 (예: 24시간)
