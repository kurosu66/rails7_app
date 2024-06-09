# 手順

- `$ docker compose run --no-deps web rails new . --force --database=postgresql --api`
  - → ファイルが生成される
- `$ docker compose build`
- `config/database.yml`の`encoding: unicode`の直下に以下を追記
  - host: db
  - username: <%= ENV["POSTGRES_USER"] %>
  - password: <%= ENV["POSTGRES_PASSWORD"] %>
- 再度`$ docker compose build`
- `$ docker compose up -d`
  - →`Gemfile.lock`に追記される
  - webサービスとdbサービスが立ち上がり、`docker compose ps`で以下が確認できればOK
<img width="1028" alt="image" src="https://github.com/kurosu66/rails7_app/assets/85793702/e0fdfd58-4aeb-4205-97de-92eae820e35f">

- `$ docker compose run web rails db:create`
- `localhost:3000`にアクセス


## 以下エラーには、downしてbuildしてup
<img width="1353" alt="image" src="https://github.com/kurosu66/rails7_app/assets/111398600/c3ec95ee-3a2a-4e30-aa4e-e2fce13e26c1">
