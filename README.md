# 회중 일정 공유 앱

## 배포 방법 (GitHub Pages)

### 1단계 — GitHub 저장소 생성
1. https://github.com/hawk4934-cmyk 로그인
2. 우측 상단 **+** → **New repository**
3. Repository name: `congregation-app`
4. Public 선택 → **Create repository**

### 2단계 — 파일 업로드
저장소 페이지에서 **Add file → Upload files** 클릭  
아래 파일들을 드래그해서 올리세요:
- `index.html`
- `manifest.json`
- `icon-192.png` (앱 아이콘 — 추후 추가)
- `icon-512.png` (앱 아이콘 — 추후 추가)

**Commit changes** 클릭

### 3단계 — GitHub Pages 활성화
1. 저장소 → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / folder: **/ (root)**
4. **Save**

약 1~2분 후 아래 주소로 접속 가능:
```
https://hawk4934-cmyk.github.io/congregation-app/
```

---

## Firebase 연결 방법

### 새 Firebase 프로젝트 만들기
1. https://console.firebase.google.com 접속
2. **프로젝트 추가** → 이름: `congregation-app`
3. Google Analytics: 사용 안 함 → **프로젝트 만들기**

### Firestore 활성화
1. 왼쪽 메뉴 **Firestore Database** → **데이터베이스 만들기**
2. **테스트 모드**로 시작 (나중에 보안 규칙 설정)
3. 위치: `asia-northeast3` (서울)

### Storage 활성화
1. 왼쪽 메뉴 **Storage** → **시작하기**
2. 테스트 모드 → 위치: `asia-northeast3`

### 앱 등록 및 설정 코드 복사
1. 프로젝트 홈 → **웹 앱 추가** (</> 아이콘)
2. 앱 닉네임: `congregation-web`
3. **앱 등록** → firebaseConfig 코드 복사

### index.html에 설정 코드 붙여넣기
`index.html` 상단의 아래 부분을 찾아 교체:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",           // ← 여기를
  authDomain: "...",                 //    복사한
  projectId: "...",                  //    실제 값으로
  storageBucket: "...",              //    교체
  messagingSenderId: "...",
  appId: "..."
};
```

---

## 현재 구현된 기능

### 게시판 탭
- [x] 카테고리 필터 (생활봉사 / 공개강연 / 주차·마이크 / 공지)
- [x] 파일 목록 표시 (업로드 날짜, 기간 표시)
- [x] 게시물 상세 보기 (이미지 미리보기, 엑셀 배정 미리보기)
- [x] 게시물 삭제

### 공식일정 탭
- [x] 달력 보기 (월 이동, 일정 있는 날 점 표시, 오늘 강조)
- [x] 텍스트 목록 보기 (월별 그룹, 날짜·장소·시간)
- [x] 일정 상세 보기 및 삭제

### 내 일정 탭
- [x] 이름 검색
- [x] 계획표별 그룹핑 표시
- [x] 날짜·역할·조언자·보조 표시
- [x] 다양한 날짜 형식 파싱 (6/3, 2025-06-03, 6월3일 등)

### 관리자 탭
- [x] 4단계 파일 업로드 (파일 선택 → 컬럼 지정 → 결과 확인 → 저장)
- [x] 엑셀 자동 파싱 (SheetJS)
- [x] 이미지 파일 업로드
- [x] 컬럼 매핑 설정 (다음 업로드에 자동 적용)
- [x] 공식 일정 추가 / 삭제
- [x] 회중 이름 설정
- [x] 공지 배너 설정
- [x] 형제 명단 관리

### 공통
- [x] PWA (홈 화면 추가 지원)
- [x] 로컬 저장 (localStorage — Firebase 미연결 시)
- [x] 토스트 알림
- [x] Safe area 지원 (아이폰 노치/홈바)

---

## 앞으로 추가할 기능 (2단계)

- [ ] Firebase Firestore 실시간 동기화
- [ ] Firebase Storage 파일 업로드 (현재는 로컬만)
- [ ] 관리자 로그인 (비밀번호 보호)
- [ ] 동명이인 구분 (형제 명단 연동)
- [ ] 월별 달력에서 개인 일정 하이라이트
- [ ] 알림 기능 (PWA Push Notification)
- [ ] 앱 아이콘 (icon-192.png, icon-512.png)
