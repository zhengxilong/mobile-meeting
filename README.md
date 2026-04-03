# Mobile Meeting

一个可本地直接打开的移动会议快捷访问网页应用，适合把收到的会议邀请文本快速整理成可搜索、可保存、可一键入会的会议列表。

项目特点：

- 单文件应用，核心入口只有一个 [`index.html`](./index.html)
- 纯 HTML、CSS、JavaScript，无第三方依赖
- 支持剪贴板解析会议邀请文本
- 支持手动新增、编辑、删除会议
- 支持快速输入会议号直接入会
- 支持 LocalStorage 本地持久化
- 支持浅色、深色、跟随系统三种主题模式
- 支持按时间智能区分近期会议与历史会议

## 在线使用

下载项目文件后，直接用浏览器打开 [`index.html`](./index.html) 即可，无需安装依赖或启动服务。

```bash
open index.html
```

如果你在 Windows 上，可以直接双击 `index.html`，或使用默认浏览器打开。

## 适用场景

- 经常从聊天工具、短信、邮件里收到移动会议邀请
- 想把分散的会议信息收拢到一个本地页面中统一管理
- 希望在不开企业系统的情况下，快速保存和跳转会议链接
- 希望整个工具完全本地运行，不依赖后端服务

## 核心功能

### 1. 会议管理

- 新增会议
- 编辑会议
- 删除会议
- 搜索会议主题
- 查看历史会议

### 2. 快速入会

- 点击已保存会议的一键入会按钮
- 输入会议号直接拼接链接加入会议
- 自动根据会议号生成默认参会链接

### 3. 智能解析

支持从剪贴板识别如下格式的会议邀请文本：

```text
会议组织者邀请您参加移动会议
会议主题：项目沟通会
会议时间：2026-03-04  10:00  (GMT+08:00) 示例时区城市
移动会议：378167162
参会链接：https://meeting.example.com/share/378167162?xlocation=DEMO
点击链接，进入H5邀请页面。
```

可自动提取的字段包括：

- 发起人
- 会议主题
- 会议时间
- 会议号
- 会议密码
- 参会链接

## 数据与隐私

- 所有会议数据默认保存在当前浏览器的 `LocalStorage`
- 页面不会主动将数据上传到任何服务器
- 剪贴板读取仅在浏览器支持且用户允许的前提下生效
- 快速入会使用的默认链接规则基于当前页面内置地址模板生成

如果你需要共享数据或多设备同步，需要自行扩展存储方案。

## 目录结构

```text
mobile-meeting/
├── index.html
├── LICENSE
├── README.md
└── docs/
    ├── design.md
    ├── implementation-report.md
    └── archive/
        ├── index-v1.html
        └── index-v2.html
```

## 开发说明

这是一个刻意保持轻量的单文件项目。若要继续迭代，建议优先保持以下原则：

- 尽量不引入构建步骤
- 尽量不引入运行时依赖
- 优先保证浏览器直接打开即可使用
- 新功能优先围绕“快速保存会议”和“快速进入会议”展开

## 文档

- 设计文档：[docs/design.md](./docs/design.md)
- 实现报告：[docs/implementation-report.md](./docs/implementation-report.md)
- 历史版本归档：[docs/archive/index-v1.html](./docs/archive/index-v1.html)、[docs/archive/index-v2.html](./docs/archive/index-v2.html)

## License

本项目使用 MIT License，详见 [`LICENSE`](./LICENSE)。
