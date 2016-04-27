# GitLab From Source Fixes

##### Change Git user to superuser

- Log in to psql dashboard.

```sql
ALTER USER myuser WITH SUPERUSER;
```

##### Fix issue with PG extension

```bash
sudo apt-get install postgresql-contrib
```

##### Change git-data path for repositories

1. Go to config/gitlab.yml
2. Change repos_path