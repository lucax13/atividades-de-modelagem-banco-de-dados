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

### Visualizar detalhes estruturais da tabela

```sql
DESC fabricantes;
```

###  criar tabela produtos

```sql
CREATE TABLE produtos(
    id INT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2) NOT NULL,
    fabricante_id INT NOT NULL -- será chave estrangeira
);  
```