# Ansible Role: PostgreSQL

Ansible role устанавливает и конфигурирует PostgreSQL server на Debian и AlmaLinux
## Требования

- Ansible 2.15+
- Debian или AlmaLinux

## Переменные роли

Следующие переменные содержатся в `defaults/main.yml`:

```yaml
# PostgreSQL version to install
postgresql_version: "13"

# PostgreSQL data directory
postgresql_data_dir: "/var/lib/postgresql/{{ postgresql_version }}/main"

# PostgreSQL configuration directory
postgresql_config_dir: "/etc/postgresql/{{ postgresql_version }}/main"

# PostgreSQL port
postgresql_port: 5432

# PostgreSQL superuser password
postgresql_superuser_password: ""

# List of databases to create
postgresql_databases: []

# List of users to create
postgresql_users: []
```

## Примерный playbook

```yaml
- hosts: database_servers
  roles:
    - role: ansible-role-postgresql
      vars:
        postgresql_version: "13"
        postgresql_superuser_password: "secure_password"
        postgresql_databases:
          - name: myapp
            owner: myapp_user
        postgresql_users:
          - name: myapp_user
            password: "user_password"
            databases: ["myapp"]
```

## Особенности

- Поддерживает операционные системы Debian и AlmaLinux
- Устанавливает сервер PostgreSQL
- Создаёт указанные базы данных
- Создаёт и настраивает пользователей баз данных
- Устанавливает соответствующие права доступа

## License

MIT

## Author Information

This role was created by grrg.
