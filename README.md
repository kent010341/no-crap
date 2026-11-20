# no-crap
A Claude marketplace of plugins to stop Claude from talking crap.

## 安裝

在 Claude Code 中加入本 marketplace：

```
/plugin marketplace add kent010341/no-crap
```

再安裝需要的 plugin：

```
/plugin install just-answer@no-crap
```

## 目錄結構

```
.claude-plugin/marketplace.json        # marketplace 清單
plugins/<plugin>/.claude-plugin/plugin.json
plugins/<plugin>/skills/<skill>/SKILL.md
```

## Plugins

| Plugin | 說明 |
| --- | --- |
| just-answer | 目標明確、不希望模型多講話的回答模式合集 |
| fast-answer | 趕時間用：最少證據、最短篇幅；含長內容速讀摘要 |
| loose-answer | 放行證據不足時的推斷與估算：不拒答、不堆免責，只用短標記註記；可單用或疊加 |
| stop-answer | 優雅中止：讓模型把進行中的操作做完後停手，不再改動檔案或狀態；可帶一句原因 |
| plain-answer | 簡單易懂：文句簡單、低複雜度但不失精準；科普問答、看不懂就重講、簡單翻譯、依你的意思寫簡單的文字；預設讀者是沒有相關背景的成年人 |

## Skills

所有 skill 皆僅手動呼叫，格式為 `/<plugin>:<skill>`。

| Skill | 用途 | 範例 |
| --- | --- | --- |
| `just-answer:just-asking` | 快問快答 | `/just-answer:just-asking <問題>` |
| `just-answer:just-curious` | 聊天探索 | `/just-answer:just-curious <話題>` |
| `just-answer:just-word` | 單字短翻譯、規格術語提取（可附出處章節） | `/just-answer:just-word <詞句>` |
| `just-answer:just-ref` | 找規格／文件中描述某功能的原文，只給位置與一字不差的引文，依符合度排序；支援線上文件與本地檔案、目錄 | `/just-answer:just-ref SIP fork`<br>`/just-answer:just-ref <檔案或目錄> <功能描述>` |
| `fast-answer:fast-asking` | 急問急答：預設憑記憶、最多搜尋 1 次 | `/fast-answer:fast-asking <問題>` |
| `fast-answer:fast-tldr` | 急速摘要：貼文、網址、檔案、目錄或前一則回答壓成極短重點；保留數字、日期時間、人名；原文無結論不硬湊；只影響這一次 | `/fast-answer:fast-tldr <文字、網址、檔案或目錄>`<br>`/fast-answer:fast-tldr`（摘要前一則回答） |
| `loose-answer:loose-evidence` | 低證據／無證據時放行推斷與適度發散，只留一個短標記；可單獨使用或與其他 skill 疊加 | `/loose-answer:loose-evidence <問題>`<br>`/just-answer:just-curious /loose-answer:loose-evidence <話題>` |
| `loose-answer:loose-estimate` | 估算題（含虛構作品設定）：缺資料也給量級、區間、假設（區分查到／自設）與算式 | `/loose-answer:loose-estimate <估算問題>` |
| `stop-answer:stop-goodhart` | 優雅中止：模型正為了讓測試通過而修改（Goodhart 問題）；執行中途也能送出 | `/stop-answer:stop-goodhart`<br>`/stop-answer:stop-goodhart 補充說明` |
| `stop-answer:stop-now` | 優雅中止：不說明原因 | `/stop-answer:stop-now` |
| `stop-answer:stop-quota` | 優雅中止：token 配額將盡 | `/stop-answer:stop-quota` |
| `plain-answer:plain-asking` | 科普等級問答：少術語、多例子與譬喻，簡單但不失精準；可指定讀者 | `/plain-answer:plain-asking <問題>` |
| `plain-answer:plain-explain` | 看不懂就重講：用簡單的話重新解釋前一則回答或貼上的內容；結論、數字、限定條件、指令與程式碼原樣保留 | `/plain-answer:plain-explain`（重講前一則回答）<br>`/plain-answer:plain-explain <文字、網址或檔案>` |
| `plain-answer:plain-translate` | 簡單詞彙與文法的翻譯，預設中英互翻；佔位符（角括號、方括號、大括號內容）原樣保留不翻 | `/plain-answer:plain-translate <原文>`<br>`/plain-answer:plain-translate 日文 <原文>` |
| `plain-answer:plain-write` | 依你的意思寫出簡單的文字（回信、訊息等）；語言依指定、回覆材料、指令語言判斷；跨語言時附回譯供確認 | `/plain-answer:plain-write 我想回覆這封信，說下週可以` |
