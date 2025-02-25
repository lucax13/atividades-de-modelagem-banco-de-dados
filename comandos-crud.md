# comandos para operações crud no banco de dados

## resumo

- C -> Create -> INSERT: inserir dados/registros na tabela
- R -> Read -> SELECT: consultar/ler dados/registros na tabela
- U -> Update -> UPDATE: atualizar dados/registros na tabela
- D -> Delete -> DELETE: excluir dados/registros na tabela

## INSERT (fabricantes)

```sql
INSERT INTO fabricantes (nome) VALUES('Asus');
INSERT INTO fabricantes (nome) VALUES('Apple');
INSERT INTO fabricantes (nome) VALUES('Dell');

INSERT INTO fabricantes (nome) VALUES('Xaiomi'), ('LG'), ('Samsung');
```
## SELECT (Fabricantes)
```sql
SELECT * from fabricantes;
```

-----------

## INSERT (Produtos)

```sql
INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)

VALUES('Ultrabook','Equipamento de ultima geração', 3969.56, 7, 2);
```