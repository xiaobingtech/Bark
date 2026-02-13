中文 | English
# Bark
Bark 是一款基于 APNs 的 iOS 推送通知工具，支持自建服务端与端到端加密，提供更细粒度的通知能力与可控的隐私方案。

## 功能概览
- 推送能力：标题/副标题/正文、URL 跳转、分组、铃声、自定义图标、时效性通知、重要警告、徽标
- 通知扩展：自动复制、图片与图标加载、Markdown 渲染、分组静音、归档开关、级别与音量处理
- 历史记录：消息列表、分组聚合、搜索、按时间范围清理
- 服务器管理：多服务端切换、复制地址与 key、重置 key、设置名称、扫码添加
- 本地管理：自定义铃声导入与试听、备份与恢复、归档设置

## UI 与页面
- 服务页（Home）：注册推送、示例预览列表、添加自建服务器、进入服务器列表
- 消息页（MessageList）：消息列表、分组展开/折叠、搜索、下拉刷新、批量清理
- 设置页（MessageSettings）：归档开关、备份/恢复、设备信息、捐赠、入口跳转
- 服务器列表（ServerList）：选择默认服务端、复制、重置 key、删除、设置名称
- 添加服务器（NewServer）：输入地址、扫码导入、跳转部署文档
- 铃声管理（Sounds）：系统与自定义铃声列表、试听、导入
- iPad 分栏（Section iPad）：左侧主导航 + 右侧详情页

## 架构与模块
- 架构：MVVM + RxSwift（ViewModelType 协议统一输入输出）
- 网络：Moya 封装 Bark API
- 本地存储：Realm 保存消息与配置
- 依赖：RxSwift/RxCocoa/RxDataSources、Material、SnapKit
- 扩展：NotificationServiceExtension 处理推送内容，NotificationContentExtension 提供通知交互与图片展示

## 目录结构与职责
- Bark/：应用入口、资源、配置与 AppDelegate
- Common/：网络层、设置管理、工具方法、全局配置
- Controller/：页面与导航控制器
- View/：列表单元、控件、页眉页脚等 UI 组件
- Model/：消息、分组、预览数据等数据模型
- NotificationServiceExtension/：推送处理管线（加密、Markdown、归档、图标等）
- notificationContentExtension/：通知展开视图与交互动作
- Intents/：Siri/Shortcuts 相关意图支持
- Sounds/：内置铃声资源
- BarkTests/：单元测试
- docs/：用户文档与部署说明

## 关键文件说明
- Bark/AppDelegate.swift：应用入口、通知注册、Tab/分栏根控制器、推送点击处理
- Bark/Info.plist：应用权限与基础配置
- Bark/Localizable.xcstrings：本地化字符串
- Bark/Bark.entitlements：推送与应用组权限
- Bark/Base.lproj/LaunchScreen.storyboard：启动页
- Bark/Assets.xcassets：图标与颜色资源
- Controller/BarkTabBarController.swift：iPhone 三个 Tab 入口
- Controller/BarkSplitViewController.swift：iPad 分栏容器
- Controller/SectionViewController-iPad.swift：iPad 左侧栏目
- Controller/HomeViewController.swift：服务页与示例预览
- Controller/MessageListViewController.swift：消息列表与分组
- Controller/MessageSettingsViewController.swift：设置页与备份
- Controller/ServerListViewController.swift：服务器列表与操作
- Controller/NewServerViewController.swift：添加服务器与扫码入口
- Controller/QRScannerViewController.swift：二维码扫描
- Controller/SoundsViewController.swift：铃声管理
- Common/ServerManager.swift：服务器配置与同步
- Common/ArchiveSettingManager.swift：归档设置
- Common/CryptoSettingManager.swift：加密设置
- Common/Moya/BarkApi.swift：服务端 API 定义
- Model/Message.swift：消息数据模型
- NotificationServiceExtension/NotificationService.swift：推送扩展处理流程
- NotificationServiceExtension/Processor/*：推送处理器集合
- notificationContentExtension/NotificationViewController.swift：通知内容展示与交互
- Intents/*：Siri/Shortcuts 意图实现
- Sounds/*：内置铃声音频资源

## 适配版本
- 最低系统：iOS 13.0
- iOS 14+：iPad 分栏、UIMenu 操作、文件导入
- iOS 15+：自定义图标与部分通知动作
- iOS 26+：搜索栏布局与分组圆角适配

## 下载与文档
- App Store：https://apps.apple.com/app/bark-custom-notifications/id1403753865
- 使用文档：https://bark.day.app

## 生态
- 浏览器扩展：https://github.com/ij369/bark-sender
- 定时发送：https://api.ihint.me/bark.html
- Windows 客户端：https://github.com/HsuDan/BarkHelper
- 命令行：https://github.com/JasonkayZK/bark-cli
- GitHub Actions：https://github.com/harryzcy/action-bark
