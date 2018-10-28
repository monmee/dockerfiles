## アーキテクチャ構成要素i

| イメージ名 | 用途 | service名 | Stack名
| -------- | -------- | -------- | -------- |
| MySQL | データストア | mysql_master, mysql_slave | MySQL |
| API     | データストアを操作するAPIサーバ | app_api | Application |
| Web | ビュー生成用アプリケーションサーバ | frontend_web | Frontend |
| Nging | プロキシサーバ | app_nginx, frontend_nginx | Application Frontend |

## MySQL
- 更新系query: Master DB
- 参照系query: Slave DB

### API
- TODOアプリにおけるタスクの基本的な操作を提供するRESTful API

### Web
- Webページのレンダリング(Node.js)
- API経由

### Nginx
- アプリケーションのフロントエンドサーバ　& APIの前段として配置、リバースプロキシとして動作
- キャッシュ利用、バックエンドへの柔軟なルーティングやアクセスログの出力の簡易化のため配置

### 配置戦略
- Swarmクラスタ上でそれぞれのServiceを展開する 
