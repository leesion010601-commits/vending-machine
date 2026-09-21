# LK 광고형 홈타운 밴딩머신 홈페이지

파일 하나로 돌아가는 홈페이지입니다. 이미지와 스타일, 스크립트가 모두 `index.html` 안에 들어 있어 빌드 과정이 필요 없습니다.

## 들어 있는 파일

| 파일 | 하는 일 |
| --- | --- |
| `index.html` | 홈페이지 본체. 소개 페이지, 이용 후기, 관리자 모드가 모두 여기에 있습니다 |
| `netlify.toml` | Netlify 설정. 깔끔한 주소(`/chill`, `/post/글주소`)가 열리도록 합니다 |
| `robots.txt` | 검색로봇 안내. 사이트맵 위치를 알려 줍니다 |
| `sitemap.xml` | 검색엔진에 제출할 주소 목록 |
| `rss.xml` | 네이버 서치어드바이저에 제출할 글 목록 |

---

## 1. GitHub에 올리기

1. GitHub에서 새 저장소를 만듭니다.
2. 위 다섯 개 파일을 저장소 **루트**에 올립니다. 폴더 안에 넣지 않습니다.
3. 파일명은 소문자 그대로 둡니다.

## 2. Netlify 연결

1. Netlify에 로그인하고 **Add new site → Import an existing project**를 누릅니다.
2. GitHub를 고르고 방금 만든 저장소를 선택합니다.
3. 빌드 설정은 비워 둡니다.
   - Build command: 비움
   - Publish directory: `.`
4. Deploy를 누르면 `https://무작위이름.netlify.app` 주소가 만들어집니다.
5. **Site configuration → Change site name**에서 주소를 원하는 이름으로 바꿉니다.

주소가 정해지면 아래 세 곳의 주소를 실제 주소로 바꿔 주세요.

- `index.html` 안의 `var SITE_URL = 'https://lk-vending.netlify.app';`
- `robots.txt` 의 `Sitemap:` 줄
- `sitemap.xml`, `rss.xml` 안의 주소 (관리자 모드에서 다시 내려받으면 자동으로 바뀝니다)

## 3. 네이버 서치어드바이저 연동

1. [서치어드바이저](https://searchadvisor.naver.com) → **웹마스터 도구 → 사이트 등록**에 Netlify 주소를 넣습니다.
2. 소유확인은 **HTML 태그** 방식을 고릅니다. 네이버가 보여 주는 코드에서 `content="..."` 안의 값만 복사해, `index.html` 위쪽의 이 줄에 붙여 넣습니다.

   ```html
   <meta name="naver-site-verification" content="네이버_소유확인_코드를_여기에">
   ```

3. 바뀐 `index.html`을 GitHub에 올리고(= Netlify 재배포), 네이버에서 **소유확인**을 누릅니다.
4. 확인이 끝나면 **요청 → 사이트맵 제출**에 `sitemap.xml` 을 넣습니다.
5. **요청 → RSS 제출**에 `rss.xml` 을 넣습니다.
6. **검증 → robots.txt** 에서 수집이 허용되는지 확인합니다.

구글은 [Search Console](https://search.google.com/search-console)에서 같은 방식으로 등록하고, `google-site-verification` 줄에 코드를 넣으면 됩니다.

## 4. 글 발행하는 방법

1. 홈페이지 주소 뒤에 `/admin` 을 붙여 들어갑니다. (예: `https://내주소.netlify.app/admin`)
2. 비밀번호를 넣고 들어갑니다. 처음 비밀번호는 `lk1175` 입니다.
3. 제목, 날짜, 분류, 요약, 본문을 채우고 **글 저장**을 누릅니다. 본문은 마크다운으로 씁니다.
   - `## 소제목`, `**굵게**`, `- 목록`, `> 인용`, 표까지 지원합니다.
   - **미리 보기**로 실제 화면을 먼저 확인할 수 있습니다.
4. **파일 내려받기**를 누르면 글이 들어간 새 `index.html` 이 만들어집니다.
5. 그 파일을 GitHub의 `index.html` 자리에 덮어쓰면, Netlify가 1분 안에 다시 배포합니다.
6. 글을 새로 올린 날에는 **sitemap · rss** 버튼도 눌러 두 파일을 내려받아 같이 덮어써 주세요. 검색엔진이 새 글을 더 빨리 가져갑니다.

> 저장만 하고 파일을 내려받지 않으면 글이 사라집니다. 브라우저를 닫기 전에 꼭 내려받으세요.

## 5. 올리기 전에 확인할 것

- **관리자 비밀번호** — `index.html` 안의 `var ADMIN_PW = 'lk1175';` 를 바꿔 주세요. 공개 저장소에 올리면 누구나 파일을 열어 볼 수 있으므로, 중요한 비밀번호는 쓰지 않는 편이 좋습니다.
- **소유확인 코드** — 네이버·구글 코드를 넣기 전에는 검색 등록이 되지 않습니다.
- **전화번호와 사업자 정보** — 바뀐 내용이 있으면 `index.html` 안에서 `010-3206-1175` 를 찾아 함께 수정해 주세요.
