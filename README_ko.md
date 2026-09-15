# Sephiria ModMaker

- README와 업데이트 기록은 GitHub 저장소에서 확인할 수 있습니다. Release ZIP에는 포함하지 않습니다.
- 편집기를 실행할 때마다 새 판을 확인합니다. 새 판이 있으면 업데이트 창이 열리며, 나중에 하려면 창을 닫고 상단 알림줄에서 다시 선택할 수 있습니다. 자동 확인을 끄거나 해당 판을 건너뛰면 자동 창은 표시하지 않습니다.


[한국어](README_ko.md) · [English](README_en.md) · [日本語](README_jp.md) · [中文](README_zh.md)

## 라이선스

이 저장소는 [MIT License](LICENSE)로 배포됩니다.
배포물에 포함된 외부 라이브러리의 저작권 및 라이선스는
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)를 확인하세요.

---

## 고지

Sephiria ©TEAM HORAY.
Sephiria Mod Maker by **Xetsumei**. This is an unofficial modding tool for Sephiria.
Built with the assistance of Claude.

문의: Discord `Xetsumei`

이 저장소와 기여자들은 Sephiria, TEAM HORAY 또는 그와 관련된 어떠한 조직과도 아무런 관련이 없습니다.
게임 자산은 저장소에 포함되어 있지 않으며, 모드 배포 시에도 게임 파일을 재배포하지 마세요.

## 일지/훈련장 비공개 (2.5.5)

아이템 상세 상단에서 **일지/훈련장 비공개**를 켜면 일지와 훈련장 목록에서 숨겨지고, 그 화면에서 꺼낼 수 없습니다. 일지 검색·즐겨찾기와 훈련장 즐겨찾기 일괄 꺼내기에도 적용됩니다. 이미 얻은 아이템은 정상적으로 사용할 수 있습니다.

보상·상점·해금·차원 주머니 규칙은 그대로입니다. 특정 아이템 효과로만 얻는 비밀 아티팩트를 만들려면 **보상 제외**도 함께 켜세요. JSON에는 `hideFromJournalAndTraining`으로 저장되며, 필드가 없는 기존 모드는 공개로 취급합니다. 사용하려면 편집기와 게임 런타임을 모두 2.5.5 이상으로 업데이트하세요.
