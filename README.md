# Zerops Hello World Python

```yaml
project:
  name: zerops-hello-world-python
  tags:
    - zerops
    - hello-worlds

services:
  - hostname: python39
    type: python@3.9
    envSecrets:
      DB_HOST: db
      DB_NAME: db
      DB_PASS: ${db_password}
      DB_PORT: "5432"
      DB_USER: ${db_user}
    ports:
      - port: 5000
        httpSupport: true
    enableSubdomainAccess: true
    buildFromGit: https://github.com/zeropsio/recipe-onboarding-python
    minContainers: 1
    maxContainers: 6

  - hostname: adminer
    type: php-apache@8.0+2.4
    buildFromGit: https://github.com/zeropsio/recipe-adminer@main
    enableSubdomainAccess: true
    minContainers: 1
    maxContainers: 1

  - hostname: db
    type: postgresql@14
    mode: NON_HA
    priority: 1
```

