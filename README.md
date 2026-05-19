# Sino 群晖方案拓扑系统

基于 [draw.io](https://github.com/jgraph/drawio) v30.0.2 定制的群晖专属方案拓扑图工具，供 Synology 经销商快速生成专业方案拓扑图。

## 功能特性

- **拖拽式拓扑设计**：从侧边栏拖拽 NAS 机型和 DSM 软件包到画布，快速搭建方案拓扑
- **全系列机型支持**：DS、RS、SA、DX、RX 全系列共 36 款 Synology NAS 机型图标
- **96 款 DSM 软件包**：涵盖备份、存储、虚拟化、监控等全品类套件
- **子串搜索**：输入型号关键词（如 "3618"、"dri"）即可快速定位图标
- **中文界面**：默认中文语言，加载页与操作界面全面汉化
- **多格式导出**：支持 PNG、SVG、PDF 导出方案图
- **公司署名**：页面加载页与工具栏底部显示 SinoSignal 品牌标识

## 技术栈

- draw.io (diagrams.net) v30.0.2 - mxGraph 图形引擎
- Java WAR 包结构，支持 Tomcat 等 Servlet 容器部署
- 纯前端 JavaScript，无需后端服务

## 部署方式

### 开发模式

```bash
# 启动 Tomcat 后访问（带 dev 参数加载未压缩 JS）
http://localhost:8080/index.html?dev=1
```

### 生产部署

```bash
# 编译 WAR 包
mvn package

# 部署到 Tomcat
cp target/*.war $CATALINA_HOME/webapps/ROOT.war
```

## 项目结构

```
src/main/webapp/
├── index.html                          # 入口页面（含 SinoSignal 加载页）
├── img/
│   ├── synology/                       # NAS 机型图标（36款）
│   ├── synology-software/              # DSM 软件包图标（96款）
│   └── sinosignal-logo/               # SinoSignal 公司 logo
├── js/diagramly/sidebar/
│   └── Sidebar-Synology.js            # 群晖形状库定义
├── js/diagramly/sidebar/Sidebar.js    # 侧边栏配置（精简后）
├── js/grapheditor/Sidebar.js          # 搜索逻辑（含子串匹配）
├── js/grapheditor/Menus.js            # 菜单配置（精简后）
├── js/diagramly/App.js                # 应用主逻辑
└── styles/grapheditor.css             # 样式定义
```

## 定制说明

本项目基于 draw.io 开源版（Apache 2.0 许可证）进行以下定制：

1. **侧边栏精简**：仅保留通用、基本、箭头、流程图、Synology NAS、Synology DSM 六个面板
2. **菜单精简**：移除 Help 菜单和 Extras（其它）菜单
3. **搜索增强**：添加子串匹配，支持型号关键词模糊搜索
4. **品牌定制**：替换 draw.io logo 为 SinoSignal 公司标识
5. **语言汉化**：默认中文界面，加载页文案汉化

## 许可证

基于 [draw.io](https://github.com/jgraph/drawio)（Apache License 2.0）定制。

SinoSignal 公司 logo 版权归 SinoSignal 所有。
