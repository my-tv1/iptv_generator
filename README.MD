# 播放列表生成器

本仓库包含一个M3U播放列表生成器，可以生成包含各种资源（如YouTube、Twitch、Dailymotion和直接URL流媒体）的播放列表。

**免责声明：**

请注意，提供的M3U链接可能会指向内容源。使用本软件时，您有责任确保遵守版权法律和使用政策。生成器和仓库所有者不对本软件的使用或滥用负责，包括任何可能指向受版权保护或盗版内容的链接。

## 如何安装：

1. 点击"Use this template"按钮并创建一个新的公共仓库。
2. 导航到仓库设置 -> Actions -> General -> Workflow permissions。
3. 选择"Read and Write"权限并保存设置。
4. 转到Actions，选择"M3U Generator" -> Run Workflow -> Run Workflow。
5. 验证工作流是否成功运行。

## 如何使用：

1. 按照指定格式编辑`channel_info.txt`文件：
格式：'频道名称' | '组名' | 'logo' | 'tvg-id' | 'kid' | 'key' | 'license'

Channel 1 | Movies | https://example.com/Channel1.jpg | ch1
https://www.youtube.com/@Channel1/live

2. 保存并提交更改到您的仓库。
3. 再次运行工作流。
4. 访问`playlist.m3u`，获取RAW文件并复制URL。
5. 将URL粘贴到VLC或您喜欢的媒体播放器中即可享受！

**工作流每3小时运行一次，更新链接。**

## 项目文件结构

```
iptv_generator/
├── .DS_Store - macOS系统自动生成的文件夹元数据文件
├── .gitignore - Git版本控制忽略文件配置
├── channel_info.txt - 频道信息配置文件，用于定义频道名称、组名、logo等信息
├── generate.sh - 生成脚本，用于执行播放列表生成
├── LICENSE - 项目许可证文件
├── log.txt - 日志文件，记录生成过程中的信息
├── plex.m3u - 生成的Plex播放列表文件
├── plex.sh - Plex播放列表生成脚本
├── plex.xml - Plex播放列表XML格式文件
├── pluto.m3u - 生成的Pluto播放列表文件
├── pluto.sh - Pluto播放列表生成脚本
├── pluto.xml - Pluto播放列表XML格式文件
├── README.MD - 项目说明文档
└── scripts/ - 脚本目录
    ├── add_manually.py - 手动添加频道的Python脚本
    ├── generator.py - 主生成器脚本，负责生成播放列表
    ├── merge.py - 合并脚本，用于合并多个播放列表
    ├── plex.py - Plex播放列表生成脚本
    └── pluto.py - Pluto播放列表生成脚本
```

## 主要功能说明

1. 核心功能文件：
   - scripts/generator.py: 主生成器，负责解析channel_info.txt并生成播放列表
   - channel_info.txt: 频道信息配置文件，定义频道元数据和播放源

2. 播放列表生成：
   - generate.sh: 主生成脚本，调用其他脚本生成播放列表
   - scripts/plex.py: 生成Plex格式播放列表
   - scripts/pluto.py: 生成Pluto格式播放列表

3. 辅助功能：
   - scripts/add_manually.py: 手动添加频道功能
   - scripts/merge.py: 播放列表合并功能
   - log.txt: 记录生成过程中的日志信息

4. 输出文件：
   - plex.m3u/plex.xml: Plex播放列表输出
   - pluto.m3u/pluto.xml: Pluto播放列表输出

5. 配置与文档：
   - .gitignore: Git版本控制配置
   - LICENSE: 项目许可证
   - README.MD: 项目说明文档
