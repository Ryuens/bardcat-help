# Bardcat Help Center

바드캣 키우기 (Meow Rangers) 고객 지원 헬프센터

## 배포 정보

| 항목 | 값 |
|------|-----|
| **도메인** | https://help.layerlab.games |
| **호스팅** | GitHub Pages |
| **GitHub 레포** | https://github.com/Ryuens/bardcat-help |
| **브랜치** | `main` |
| **빌드 타입** | Legacy (정적 파일) |
| **DNS** | GoDaddy CNAME → `ryuens.github.io` |

## 페이지 구성

| 파일 | 설명 | URL |
|------|------|-----|
| `index.html` | 메인 헬프센터 (FAQ, 확률정보, 공지사항, 게임소식) | https://help.layerlab.games/ |
| `probability.html` | 확률 정보 (인게임 링크용 별도 페이지) | https://help.layerlab.games/probability.html |
| `terms.html` | 서비스 이용약관 | https://help.layerlab.games/terms.html |
| `privacy.html` | 개인정보 처리방침 | https://help.layerlab.games/privacy.html |

## 기능

- 한국어/영어 언어 전환 (우측 상단 드롭다운)
- FAQ 카테고리별 필터링 (아코디언)
- 확률 정보 탭 (소환, 마을건물, 특성/액세서리 옵션, 상자, 룰렛)
- 블랙 & 화이트 컬러 톤

## 인게임 연동

`PopupProbabillity.cs`에서 확률 상세보기 버튼 클릭 시 아래 URL로 이동:
- 장비 소환: `https://help.layerlab.games/probability.html#summon-gear`
- 스킬 소환: `https://help.layerlab.games/probability.html#summon-skill`
- 동료 소환: `https://help.layerlab.games/probability.html#summon-buddy`
- 액세서리 소환: `https://help.layerlab.games/probability.html#summon-accessory`

## 배포 방법

```bash
cd /Users/ryuens/Documents/GitHub/helpcenter
git add .
git commit -m "업데이트 내용"
git push origin main
```

push 후 GitHub Pages가 자동으로 빌드/배포합니다 (보통 1-2분 소요).

## DNS 설정

GoDaddy에서 CNAME 레코드 설정:
- **Host**: `help`
- **Points to**: `ryuens.github.io`
- **TTL**: 1 Hour

## 확률 데이터 출처

게임 JSON 데이터 파일에서 추출:
- `Assets/StreamingAssets/GameData/SummonLevel.json` - 소환 확률 (Lv.1~10)
- `Assets/StreamingAssets/GameData/TownItemAcquisitionBuildingRate.json` - 마을 건물 확률
- `Assets/StreamingAssets/GameData/TraitTierRate.json` - 특성 티어 확률
- `Assets/StreamingAssets/GameData/AccessoryOptionTierRate.json` - 액세서리 옵션 티어 확률
- `Assets/StreamingAssets/GameData/DailyRoulette.json` - 일일 룰렛 확률
- `Assets/StreamingAssets/GameData/Chest.json` - 상자 구성 확률

확률 데이터 변경 시 `index.html`과 `probability.html`의 JavaScript 데이터도 함께 업데이트 필요.
