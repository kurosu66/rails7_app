# 手順

- `$ docker compose run --no-deps web rails new . --force --database=postgresql --api`
  - → ファイルが生成される
- `$ docker compose build`
- `config/database.yml`の`encoding: unicode`の直下に以下を追記
  - host: db
  - username: <%= ENV["POSTGRES_USER"] %>
  - password: <%= ENV["POSTGRES_PASSWORD"] %>
- 再度`$ docker compose build`
  - →`Gemfile.lock`に追記される
- `$ docker compose up -d`
- `$ docker compose run web rails db:create`
- `localhost:3000`にアクセス
