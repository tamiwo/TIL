GitHubで共有する
======================================================================

1. リポジトリを作成
2. Windowsでクローン
3. クローンしたディレクトリの下にUnityのプロジェクトを作成
4. プロジェクトの設定を確認
   Edit > ProjectSettings > Editor
   * Virsion ControlのModeがVisible Meta Filesになっている
   * Asset SerializationのModeがForce Textになっている
5. .ignore ファイルを参考の通りに記載
6. コミット
7. Macでクローン
8. Unityでopen
```
Opening Project in Non-Matching Editor Installation

...

The saved project (2018.1.0f2) does not match the launched editor (2017.4.2f2).
...
```
で怒られるMac側が古い

9. 一旦Quitを選ぶ
10. Unityのバージョンをあげる
  -> [アンインストール](Uninstall.md)して再インストール
11. 再度開くと無事openできた

参考
----------------------------------------------------------------------
[Unity を GitHub でバージョン管理する - Qiita](https://qiita.com/hkomo746/items/a6dfa76442a474dfdf3a)
