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
| fast-answer | 趕時間用：最少證據、最短篇幅 |

## Skills

所有 skill 皆僅手動呼叫，格式為 `/<plugin>:<skill>`。

| Skill | 用途 | 範例 |
| --- | --- | --- |
| `just-answer:just-asking` | 快問快答 | `/just-answer:just-asking <問題>` |
| `just-answer:just-curious` | 聊天探索 | `/just-answer:just-curious <話題>` |
| `just-answer:just-word` | 單字短翻譯、規格術語提取（可附出處章節） | `/just-answer:just-word <詞句>` |
| `just-answer:just-ref` | 找規格／文件中描述某功能的原文，只給位置與一字不差的引文，依符合度排序；支援線上文件與本地檔案、目錄 | `/just-answer:just-ref SIP fork`<br>`/just-answer:just-ref <檔案或目錄> <功能描述>` |
| `fast-answer:fast-asking` | 急問急答：預設憑記憶、最多搜尋 1 次 | `/fast-answer:fast-asking <問題>` |
