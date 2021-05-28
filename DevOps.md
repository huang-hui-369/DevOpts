
1. コード ： コードの開発とレビュー、バージョン管理ツール、コードのマージ
2. ビルド ： 継続的インテグレーションのツール、ビルドステータス
3. テスト ： パフォーマンスを決定するためのテストと結果
4. パッケージ ： 案件リポジトリ、アプリの展開前ステージング
5. リリース ： 変更管理、リリース承認、リリース自動化
6. コンフィギュレーション ： インフラストラクチャの設定と管理、インフラスト
7. ラクチャとしてのコードのツール
8. モニター ： アプリの性能監視、エンドユーザーエクスペリエンス

## 流れ

テスト、ビルド、デプロイ

## DevOpsを実現するツール

### バージョン管理システム

* GitLab

### チケット管理システム

* redmine

### CIツール

* Jenkins : gitやビルド自動化システム「Gradle（グレイドル）」などと連携し、ブランチへプッシュされるとビルドやテストを自動で実行する。

### CDツール
* Docker : Linux上で独立した別のLinuxシステムを起動することができるコンテナ型仮想化ソフトウェア。開発環境が簡単に用意でき、かつ本番環境と共通化できる。