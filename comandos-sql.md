# comandos sql - documentação

neste arquivo está a referencia de comandos visando banco de dados MYSQL/MariaDB.

### criar banco de dados

```sql
CREATE DATABASE vendas CHARACTER SET utf8mb4;
```

### criar tabela de fabricante

```sql
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL
);
```