# 📊 델타 중립 펀딩비 전략 대시보드 v39

## 파일 구조 (v38 → v39 변경사항)

```
ewy_fundingfee/
├── index.html          ← HTML 구조만 (v38 대비 3700줄 → 750줄)
├── css/
│   └── dashboard.css   ← 전체 스타일 (292줄)
├── js/
│   └── app.js          ← 전체 JS 로직 (3251줄)
└── README.md
```

### 변경된 것
- `index.html`에서 `<style>` 블록 → `css/dashboard.css`로 분리
- `index.html`에서 `<script>` 블록 → `js/app.js`로 분리
- 타이틀 v38 → v39 업데이트

### 변경되지 않은 것
- 모든 기능 100% 동일 (코드 수정 없음, 순수 파일 분리)
- localStorage 데이터 호환 (SETTINGS_VER = v38 유지)
- 클라우드 동기화 코드 호환
- 모든 API 연동 동일

## GitHub Pages 배포 방법

### 방법 1: GitHub 웹에서 직접 (가장 쉬움)

1. https://github.com/traveler2030/ewy_fundingfee 접속
2. **기존 `index.html` 교체:**
   - `index.html` 클릭 → ✏️ 연필 아이콘(Edit) → 전체 선택(Ctrl+A) → 새 `index.html` 내용 붙여넣기 → Commit
3. **새 파일 추가:**
   - "Add file" → "Create new file"
   - 파일명: `css/dashboard.css` 입력 (`/`를 입력하면 폴더가 자동 생성됨)
   - 내용 붙여넣기 → Commit
4. **같은 방법으로:**
   - `js/app.js` 파일 생성 및 내용 붙여넣기 → Commit

### 방법 2: Git CLI

```bash
cd ewy_fundingfee
# 기존 파일 백업 (이미 v38-stable 태그로 완료)

# 새 파일 복사 (다운로드 받은 파일들을 저장소 폴더에 배치)
# index.html  → 기존 파일 교체
# css/dashboard.css → 새 폴더+파일
# js/app.js → 새 폴더+파일

git add .
git commit -m "v39: 파일 구조 분리 (CSS/JS 외부화)"
git push
```

## 롤백 방법

```bash
# v38 안정 버전으로 즉시 복원
git checkout v38-stable -- index.html
git rm -r css/ js/  # 새로 추가된 폴더 제거
git commit -m "롤백: v38-stable로 복원"
git push
```

또는 GitHub 웹에서:
1. Releases → v38-stable 클릭
2. Source code 다운로드
3. `index.html`을 기존 위치에 덮어쓰기
4. `css/`, `js/` 폴더 삭제

## 테스트 방법

배포 전에 로컬에서 테스트하려면:
1. 3개 파일을 같은 폴더 구조로 저장
2. `index.html`을 브라우저에서 직접 열기
3. 바이낸스 API, 시세 갱신, 클라우드 동기화 모두 정상 동작 확인

> ⚠️ `file://` 프로토콜에서는 CORS 제한으로 일부 API가 작동하지 않을 수 있습니다.
> 로컬 테스트 서버 사용 권장: `python3 -m http.server 8080`
