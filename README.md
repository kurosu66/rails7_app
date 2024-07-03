# README

- `$ docker compose run --no-deps web rails new . --force --database=postgresql`
  - → ファイルが生成される
- `$ docker compose build`
- `config/database.yml`の`encoding: unicode`の直下に以下を追記
  - host: db
  - username: <%= ENV["POSTGRES_USER"] %>
  - password: <%= ENV["POSTGRES_PASSWORD"] %>
- 再度`$ docker compose build`
- `$ docker compose up -d`
  - →`Gemfile.lock`に追記される
  - web サービスと db サービスが立ち上がり、`docker compose ps`で以下が確認できれば OK
    <img width="1028" alt="image" src="https://github.com/kurosu66/rails7_app/assets/85793702/e0fdfd58-4aeb-4205-97de-92eae820e35f">
