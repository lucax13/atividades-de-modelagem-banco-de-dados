# Exercicio 02
 
 ```sql
 ALTER TABLE fabricantes RENAME TO generos;

 ```


## Banco de dados

```sql
CREATE DATABASE filmes CHARACTER SET utf8mb4;
```

### Tabela
```sql
CREATE TABLE generos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

### Tabela Filme
```sql
CREATE TABLE filme(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45),
    lacamento DATE NOT NULL,
    generos_id INT NOT NULL
);    
```

### detalhes
```sql
    CREATE TABLE detalhes(
      id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
      duracao INT NOT NULL,
      sinopse TEXT(1000) NOT NULL,
      bilheteria DECIMAL(16,2), 
      orcamento DECIMAL(16,2),
      filmes_id INT NOT NULL
    );
```

### relacionamento estrangeiro
```sql
ADD CONSTRAINT fk_generos_filmes_detalhes 

FOREIGN KEY
```