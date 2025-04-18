# Ansible Role: PostgreSQL

Ansible role устанавливает и конфигурирует PostgreSQL server на Debian и RHEL
## Требования

- Ansible 2.15+
- Debian или RHEL

## Переменные роли

Следующие переменные содержатся в `defaults/main.yml`:

```yaml
# PostgreSQL version to install
pg_version: "13"

# PostgreSQL data directory
pg_data_dir: "/var/lib/postgresql/{{ pg_version }}/main"

# PostgreSQL configuration directory
pg_config_dir: "/etc/postgresql/{{ pg_version }}/main"

# PostgreSQL port
pg_port: 5432

# PostgreSQL superuser password
pg_superuser_password: ""

# List of databases to create
pg_databases: []

# List of users to create
pg_users: []
```

## Примерный playbook

```yaml
- hosts: database_servers
  roles:
    - role: ansible-role-postgresql
      vars:
        pg_version: "13"
        pg_superuser_password: "secure_password"
        pg_databases:
          - name: myapp
            owner: myapp_user
        pg_users:
          - name: myapp_user
            password: "user_password"
            databases: ["myapp"]
```

## Особенности

- Поддерживает операционные системы Debian и RHEL
- Устанавливает сервер PostgreSQL
- Создаёт указанные базы данных
- Создаёт и настраивает пользователей баз данных
- Устанавливает соответствующие права доступа

## License

MIT

## Author Information

This role was created by grrg.
