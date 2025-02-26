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

INSERT INTO fabricantes (nome) VALUES('Xaiomi'), ('LG'), ('Samsung'), ('Positivo'), ('Microsoft');
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


INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES(
    'Tablet Android',
    'Tablet Android E34 128gb',
    1000,
    7,
   4
);

INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES(
    'Tv',
    'Tv 55polegadas smart',
    5400,
    10,
    7

),
(
    'Iphone 15proMax ',
    '128gb cores azul brnaco e rosa',
    4125.55,
    6,
    2
),
(
    'ipad Mini',
    '64gb 6ram cor preta',
    650,
    6,
    4
); 


INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES
(
   'Xbox Series S',
   'Velocidade e desempenho de última geração',
    1997.00,
    5,
    11
), 
(
    'Notebook motoin',
    'Descrição: Intel Dual Core 4GB de RAM, 128GB SSD e Tela 14,1 polegadas',
    1213.65,
    8,
    10
);
```

## SELECT (produtos)

```sql
--lendo todas as colunas todas registradas
SELECT * FROM produtos;

--lendo somento o nome e o preço registrados
SELECT nome, preco FROM produtos;

SELECT preco, nome  FROM produtos;

--Mostrando nome, preço e quantidade somente dos produtos que custam abaixo de 5000
SELECT nome, preco, quantidade FROM produtos
WHERE preco < 5000;

```