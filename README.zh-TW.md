# Mood Diary Studio

台灣繁體中文 | [English](README.md)

Mood Diary Studio 是一個可攜式 Agent Skill，用來製作角色型心情手帳插圖。它不是單純擴寫生圖 Prompt，而是一套編輯決策框架：從日常敘述提煉情緒核心、刪除彼此競爭的事件、規劃低資訊密度構圖、套用已核准角色卡，最後產生模型中立的生圖 Prompt。

它也能建立與稽核純資料型角色擴充，而不把私人角色硬編進公開 framework。

## 核心差異

一般 Prompt 產生器傾向增加描述；Mood Diary Studio 的工作是判斷哪些內容不該畫。

它負責：

- 情緒核心選擇；
- 敘事刪減；
- visual budget 控制；
- 具有敘事作用的留白；
- 角色卡治理；
- quick、guided 與 advanced 三層 ONBOARD review；
- 分離角色身份與美術風格治理；
- 日期與短句處理；
- 身份與構圖 drift review。

## 用邊界保留創意空間

Mood Diary Studio 統一的是治理結果，不是每一句文字或每一種構圖。
事實狀態、已核准身份、儲存 style policy、日期授權、儲存狀態與寫入
核准是硬邊界；情緒措辭、場景處理、輔助線索與 Prompt 表達則可在
邊界內自由變化。

Acceptance 因此查核不變量，而不是逐字比對輸出。合規的差異屬於模型
正常變化；只有可重現、且改變事實、身份、權限或持久狀態的越界行為，
才視為 framework 缺陷。

## 三種模式

- **DIARY**：日常敘述轉成情緒核心、構圖 brief 與 Prompt。
- **ONBOARD**：由參考圖產生候選 `character.md`，依風險選用 quick、guided
  或 advanced review。
- **AUDIT**：比對既有角色卡與新證據，產生可審查的修訂建議。

ONBOARD 與 AUDIT 未經使用者明確核准，不得安裝或修改角色資料。

## 安裝 Skill

請安裝或複製完整目錄：

```text
skill/mood-diary-studio/
```

`SKILL.md`、`references/` 與 `assets/` 必須一起保存。Repo 根目錄是專案文件與測試，不是可安裝 Skill 本體。

可向支援標準 Skill 的 Agent 提出：

```text
使用 mood-diary-studio 的 DIARY 模式，把這段日常敘述整理成克制、
低資訊密度的角色型心情手帳 brief 與模型中立生圖 Prompt。
```

## 角色擴充

角色 plugin 是資料目錄，不含可執行程式碼：

```text
paper-dot/
├── character.md
└── references/
    └── front.png
```

公開 repo 只附一個原創、通用的示範角色。私人 character pack 應保存在 repo 外部，詳見 [私有角色包指南](docs/private-character-packs.md)。

`assets/sample-character/` 是唯讀的公開測試 fixture，不得作為私人角色或新角色的安裝目的地。

新候選卡採用 `mood-diary-character/v2`，將 immutable identity 與 soft
style guidance 分開。既有 v1 卡仍可讀取，但只能透過經核准的 AUDIT
提案遷移。內附的 Paper Dot 卡刻意保留為 v1 相容性 fixture；v2
候選模板才是目前 schema 的示範。

## 私人角色實際放在哪裡

Framework 定義 character pack 的資料結構，但刻意不 hardcode 萬用目錄。每個 host 必須提供 storage binding：

| Storage profile | 常見情境 | 持久性 |
|---|---|---|
| `bundled-assets` | 隨 Skill 發布的公開 sample | 隨 Skill 保存且唯讀 |
| `local-filesystem` | 能存取已核准 pack 路徑的本機 Agent | 本機持久 |
| `workspace-files` | 受控 Agent 工作區 | 工作區範圍 |
| `managed-project` | 網頁 Project 或 host 管理的知識空間 | Host 管理 |
| `account-library` | 帳號或 workspace 管理的檔案庫 | 帳號範圍 |
| `runtime-filesystem` | 任務 VM 或暫存 sandbox | 單次任務 |
| `chat-attachments` | 單次聊天 | 聊天範圍 |
| `manual-export` | 沒有可寫入儲存空間 | 使用者另行保存 artifact |

本機 Agent 必須明確指定私人 pack：

```text
使用 mood-diary-studio 的 ONBOARD 模式。Review 完成後，把核准角色安裝到：
/使用者明確選定的/mood-diary-characters
```

沒有本機目錄存取能力的網頁 host，仍可附上定裝圖執行 ONBOARD。新
candidate 通常是 `in-context` 與 `export-ready`；精確 artifact 經確認
存在 Project 或帳號檔案庫後可稱為 `host-saved`，但不是
`pack-installed`。任務 VM 在全新任務持久性實測前只能稱為
`transient`。

本機、workspace 與網頁 host 的完整流程見 [私有角色包指南](docs/private-character-packs.md)。

## Agent 中立

可安裝 Skill 採用開放 Agent Skills 目錄結構，不需要腳本、套件管理器、網路服務、MCP、特定生圖模型或平台 metadata。

Host 至少需要：

- 發現或載入 `SKILL.md`；
- 解析相對路徑；
- 讀取使用者文字；
- 在 ONBOARD 或圖片型 AUDIT 中檢視圖片；
- 回傳 Markdown artifact；
- 寫入角色資料前取得核准。

無法讀圖的 host 仍可使用 DIARY；ONBOARD 或圖片型 AUDIT 必須明確回報能力不足，不得虛構觀察結果。

## 範圍邊界

Mood Diary Studio 不會：

- 內附私人角色宇宙；
- 保證跨次生成的角色完全一致；
- 自行渲染圖片；
- 執行角色 plugin；
- 靜默寫入或更新角色卡；
- 綁定 ChatGPT、Claude Code、Codex、Hermes 或特定生圖服務。

## 授權

MIT。Paper Dot 示範角色與參考圖均為本專案建立的原創測試資產，適用相同授權。
