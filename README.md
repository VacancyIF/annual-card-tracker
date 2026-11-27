# 年卡使用统计（游泳 · 健身套卡）

一个轻量的年卡打卡与成本核算小工具，前端为单文件 HTML，外层用 Android WebView 封装为 APK，数据保存在本地（localStorage），无需联网。

## 功能

- **参数配置**：卡片名称、开卡日期、有效期（月）、年卡总价、单次原价。
- **打卡记录**：健身 / 游泳 / 两项都做，每次记录日期与时间；按钮二次确认防误触，确认后有短暂冷却。
- **成本核算**：
  - 当前实际单次成本（按到访次数、按人次两种口径）
  - 按当前频率推算全周期预计到访次数与预计单次成本
  - 对比单次原价的累计节省金额
  - 有效期状态（未生效 / 生效中 / 已过期）、已过天数、剩余天数
- **统计图表**：月度到访柱状趋势、健身/游泳人次占比环图、单次成本随到访次数下降曲线。
- **数据管理**：记录可单条删除，支持导出 / 导入 JSON 备份、清空记录。

## 目录结构

```
app/src/main/assets/index.html        # 前端工具（HTML/CSS/JS 单文件）
app/src/main/java/.../MainActivity.java # WebView 壳
.github/workflows/build.yml           # GitHub Actions 构建并发布 APK
```

## 本地构建（可选）

需要 JDK 17 与 Android SDK（compileSdk 34）：

```bash
gradle assembleDebug
# 产物：app/build/outputs/apk/debug/app-debug.apk
```

## 自动打包

推送到 `main` 分支后，GitHub Actions 自动构建 debug APK 并发布到 `latest` Release，下载地址见仓库 Release 页面。
