# rsrs-zh-master

《ロマンシング サガ リ・ユニバース》（SaGa RS / RSRS）繁体中文 master 数据分发仓库。

## 用途

配合打了路径重定向补丁的客户端使用：客户端从官方缓存目录改为读取
`/storage/emulated/0/Android/media/com.square_enix.android_googleplay.RSRS/AssetBundleCache/`，
本仓库按 **官方 master hash** 索引提供已套用繁中翻译的 master 文件。

## 工作方式

1. 客户端按服务器下发的 master 版本计算出 `Hash128` 文件名（如 `17ef27f0…`）；
2. 在上述目录查找同名文件：存在 → 直接使用；不存在 → 游戏自行从官方下载（自动 fallback）；
3. `manifest.json` 以官方 master hash 为键：

```json
{
  "17ef27f01a8caf80ff3418b5fd61128a": {
    "file": "masters/17ef27f01a8caf80ff3418b5fd61128a.bundle",
    "sha256": "…",
    "master_version": "…",
    "job": "quality-release-zh-20261101",
    "status": "approved"
  }
}
```

- 只有 `status: approved` 的包才会发布；发布时附 SHA-256 校验。
- 官方 master 更新而翻译未跟上时，客户端自动使用官方版本，不会错版。

## 声明

- 本仓库仅分发粉丝翻译的文本数据补丁，**不分发游戏本体 APK**；请自备正版权益客户端。
- 游戏数据版权归 © SQUARE ENIX 所有。翻译仅供学习交流，请支持官方。
