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

| Plugin | 說明 | 使用方式 |
| --- | --- | --- |
| just-answer | 目標明確、不希望模型多講話的回答模式合集：快問快答、聊天探索、單字短翻譯與規格術語提取（可附出處章節）、規格與文件原文引用查找（一字不差引文＋位置，依符合度排序；支援線上文件與本地檔案／目錄） | `/just-answer:just-asking`、`/just-answer:just-curious`、`/just-answer:just-word <詞句>`、`/just-answer:just-ref [來源路徑…] <功能描述>`（皆僅手動呼叫） |
| fast-answer | 趕時間用的回答模式：最少證據、最短篇幅，預設只憑記憶、最多搜尋 1 次 | `/fast-answer:fast-asking`（僅手動呼叫） |
