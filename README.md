# PaperArt 壁纸资源管理指南

本指南将帮助您准备和管理用于 PaperArt 壁纸应用的测试数据，以便上传到 GitHub 进行远程测试。

## 目录结构

```
TestData/
├── wallpaper-packages.json       # 主配置文件，包含所有壁纸包信息
└── packages/                     # 壁纸包目录
    ├── nature/                   # 自然风光系列
    │   ├── cover.jpg             # 壁纸包封面图
    │   ├── wallpaper1/           # 第一张壁纸
    │   │   ├── thumbnail.jpg     # 缩略图 (建议: 300x169)
    │   │   ├── preview.jpg       # 预览图 (建议: 1920x1080)
    │   │   └── full.jpg          # 完整分辨率图 (建议: 3840x2160)
    │   ├── wallpaper2/
    │   │   ├── thumbnail.jpg
    │   │   ├── preview.jpg
    │   │   └── full.jpg
    │   └── wallpaper3/
    │       ├── thumbnail.jpg
    │       ├── preview.jpg
    │       └── full.jpg
    └── abstract/                 # 抽象艺术系列
        ├── cover.jpg
        ├── wallpaper1/
        │   ├── thumbnail.jpg
        │   ├── preview.jpg
        │   └── full.jpg
        └── wallpaper2/
            ├── thumbnail.jpg
            ├── preview.jpg
            └── full.jpg
```

## 配置文件说明

### wallpaper-packages.json

主配置文件包含一个壁纸包数组，每个壁纸包包含以下字段：

- `id`: 壁纸包唯一标识符 (UUID)
- `name`: 壁纸包名称
- `description`: 壁纸包描述
- `category`: 壁纸包分类
- `coverImageURL`: 封面图URL
- `wallpapers`: 壁纸数组
- `createdAt`: 创建时间 (ISO 8601格式)
- `updatedAt`: 更新时间 (ISO 8601格式)

每个壁纸对象包含以下字段：

- `id`: 壁纸唯一标识符 (UUID)
- `packageId`: 所属壁纸包ID
- `name`: 壁纸名称
- `thumbnailURL`: 缩略图URL
- `previewURL`: 预览图URL
- `fullResolutionURL`: 完整分辨率图URL
- `width`: 完整分辨率宽度
- `height`: 完整分辨率高度
- `fileSize`: 完整分辨率文件大小 (字节)

## 图片资源准备

1. **分辨率要求**：
   - 缩略图：建议 300x169 (16:9 比例)
   - 预览图：建议 1920x1080 (16:9 比例)
   - 完整分辨率：建议 3840x2160 (4K) 或更高

2. **格式要求**：
   - 支持 JPG、PNG 格式
   - 建议使用 JPG 格式以减小文件大小
   - 压缩质量：建议 80-90% (平衡质量和大小)

3. **命名规则**：
   - 封面图：`cover.jpg`
   - 缩略图：`thumbnail.jpg`
   - 预览图：`preview.jpg`
   - 完整分辨率图：`full.jpg`

## 上传到 GitHub

1. 在 GitHub 上创建一个新的仓库（建议命名为 `PaperArt-Wallpapers`）
2. 将 `TestData` 目录下的所有文件和子目录上传到仓库
3. 更新 `wallpaper-packages.json` 中的 URL，将 `yourusername` 替换为您的 GitHub 用户名
4. 确保仓库设置为公开访问

## 使用方法

上传完成后，您可以在应用中配置 API 服务，将 `WallpaperAPIService.swift` 中的 `baseURL` 替换为您的 GitHub 仓库 RAW URL：

```swift
private let baseURL = URL(string: "https://raw.githubusercontent.com/yourusername/PaperArt-Wallpapers/main/")!
```

## 注意事项

1. 确保所有图片 URL 都指向正确的文件路径
2. 检查文件大小，避免过大的图片影响加载速度
3. 定期更新 `updatedAt` 字段，以便应用检测到新内容
4. 可以根据需要添加更多壁纸包和壁纸

## 示例工作流

1. 创建新的壁纸包目录：`packages/new-category/`
2. 添加封面图：`packages/new-category/cover.jpg`
3. 创建壁纸目录：`packages/new-category/wallpaper1/`
4. 添加不同分辨率的壁纸图片
5. 在 `wallpaper-packages.json` 中添加新的壁纸包和壁纸信息
6. 上传到 GitHub
7. 在应用中测试新壁纸包

## 更新日志

- 2025-12-31: 初始版本，包含自然风光和抽象艺术两个系列示例

---

祝您使用愉快！
