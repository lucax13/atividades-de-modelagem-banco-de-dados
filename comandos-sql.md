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

### Criar relacionamento entre as tabelas e configurar a chave estrangeira

```sql
ALTER TABLE produtos
    --  adicionando uma restrição indicando o nome do relacionamneto

    ADD CONSTRAINT fk_produtos_fabricantes

    --criando a chave-estrangeira (fabricantes_id) que

    --aponta para a chave primaria (id) de outra 
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);

```
### exemplos de alterações estruturais em tabelas

#### adicionar coluna

```sql
ALTER TABLE produtos ADD quantidade INT NULL AFTER preco;
```

#### renomear tabela 
```sql
ALTER TABLE fabricantes RENAME TO fornecedores;
ALTER TABLE fornecedores RENAME TO fabricantes;
```
