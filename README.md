# Picmodify

Picmodify 是一个基于浏览器的离线文档扫描矫正工具。它使用 OpenCV.js 自动识别图片中的文档区域，并通过透视变换生成拉正后的扫描效果。

## 功能

- 离线运行，无需上传图片
- 一次导入多张图片
- 按导入顺序自动处理
- 左侧纵向列表切换图片
- 自动识别文档四个角点
- 可手动拖动角点微调
- 实时预览透视矫正结果
- 支持输出比例：原比例、A/B 系列、16:9、9:16、2:3、3:2、自定义比例
- 支持彩色增强
- 支持 JPEG 压缩质量调整
- 支持单张下载
- 支持全部处理结果打包为 ZIP 下载

## 使用方式

直接用浏览器打开：

```text
document_scanner_app.html
```

确保以下文件在同一目录：

```text
document_scanner_app.html
opencv.js
```

打开网页后：

1. 点击“导入图片”，选择一张或多张图片。
2. 程序会按顺序自动识别并处理。
3. 在左侧列表中切换图片。
4. 如识别边界不准，可拖动红色角点微调。
5. 调整输出比例和 JPEG 质量。
6. 点击“下载结果”保存当前图片，或点击“全部下载”导出 ZIP。

## 技术说明

项目使用原生 HTML、CSS、JavaScript 和 Canvas 构建，不依赖构建工具。

角点识别优先使用 OpenCV.js：

- 灰度转换
- 高斯模糊
- 多阈值 Canny 边缘检测
- 形态学闭运算
- 轮廓检测
- 四边形近似
- 大轮廓合并与候选评分
- 纸张区域占比评分，减少识别区域过大的情况

如果 OpenCV.js 加载失败，页面仍保留内置 JavaScript 检测逻辑作为降级方案。

## 文件结构

```text
.
├── document_scanner_app.html
├── opencv.js
├── README.md
└── .gitignore
```

## 许可证建议

建议使用 Apache License 2.0。

OpenCV 4.5.0 及以后版本使用 Apache 2.0 许可证。由于本项目分发并依赖 OpenCV.js，项目自身也采用 Apache-2.0 会更清晰。

如果正式发布，建议补充：

- `LICENSE`
- `THIRD_PARTY_NOTICES.md`

用于说明 OpenCV.js 的版权和许可证信息。
