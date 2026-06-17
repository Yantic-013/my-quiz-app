# 技术设计规范

## 技术栈
- **架构**：纯前端单文件 (HTML + CSS + JS)
- **数据存储**：浏览器 localStorage
- **Excel 解析**：SheetJS (xlsx) CDN 引入
- **版本**：xlsx 0.20.1
- **无构建工具，无框架，无 npm 依赖**

## 数据模型

### 题库数据 (localStorage key: `questionBank`)
```js
[
  {
    id: "uuid",           // 唯一标识
    chapter: "第一章 概述",
    type: "single",       // "single" | "multi"
    question: "题目文本",
    options: ["选项1", "选项2", "选项3", "选项4"],  // 原始顺序（显示时打乱）
    answer: ["A"],        // 正确答案索引数组，单选 ["A"]，多选 ["A","C"]
    explanation: "解析文本"
  }
]
```

### 错题集 (localStorage key: `errorBook`)
```js
[
  {
    questionId: "uuid",   // 关联题目 id
    wrongCount: 3,        // 错误次数
    lastWrong: "2026-06-06",  // 最后错误日期
  }
]
```

### 用户设置 (localStorage key: `settings`)
```js
{
  memorizationMode: false
}
```

## Excel 解析规则
- 读取第一行作为表头
- 必填列：章节、题型、题目、选项A、选项B、选项C、选项D、正确答案
- 选填列：解析、选项E、选项F...（程序自动检测非空列头）
- 选项列识别：列头匹配 `选项[A-Z]` 且内容非空的列
- 正确答案解析：按逗号分割 → 去空格 → 转为大写字母数组
- 跳过题目为空的空行

## localStorage 键名
| 键名 | 内容 |
|------|------|
| `questionBank` | 题库数组 |
| `errorBook` | 错题集数组 |
| `settings` | 用户设置对象 |
