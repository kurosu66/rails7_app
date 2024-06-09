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


## 以下エラーには、downしてbuildしてup
<img width="1353" alt="image" src="https://github.com/kurosu66/rails7_app/assets/111398600/c3ec95ee-3a2a-4e30-aa4e-e2fce13e26c1">
