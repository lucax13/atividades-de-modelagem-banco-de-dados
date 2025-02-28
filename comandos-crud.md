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

VALUES('Ultrabook','Equipamento de ultima geração', 3969.56, 7, 1);


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

-- Mini-exercicio: mostre o nome de descrição somente dos produtos apple
SELECT nome, descricao  FROM produtos
WHERE fabricante_id = 2;
```
## Operadores logicos: E, OU e Não


#### E (AND)
```sql
-- Exibir nome e preco dos produtos que custam entre 2000 e 6000
SELECT nome, preco FROM produtos
WHERE preco >=  2000 AND preco <= 6000;
```


#### OU (OR)

```sql
--Exibir nome e descrição dos produtos da Apple e da samsung
SELECT nome, descricao FROM produtos
WHERE fabricante_id = 2 OR  fabricante_id = 7;

--Versão usando função sql IN()
SELECT nome, descricao FROM produtos
WHERE fabricante_id IN(3, 5);
```

#### Não (NOT)
```sql
-- nome, descrição e preço de todos os produtos EXCETO da positivo
SELECT nome, descricao, preco FROM produtos
WHERE NOT fabricante_id = 10;

SELECT nome, descricao, preco FROM produtos
WHERE fabricante_id != 10;
```

## UPDATE (Fabricantes)

**CUIDADO**

**SEMPRE USE** a clausula 'WHERE' em seu comando 'UPDATE' especificando uma ou mais condições para a atualização

```sql
--TRocar o nome do fabricante asus para asus do brasil
UPDATE fabricantes SET nome = 'Asus do Brasil'
WHERE id = 1;

--alterar a quantidade para 10 dos produtos que custam abaixo de 2000 exceto da microsoft.
UPDATE produtos  SET quantidade = 10
WHERE preco < 2000 AND NOT fabricante_id = 11;
```

## DELETE (Fabricantes e Produtos)

**☠️ PRERIGO! 🚨**

**SEMPRE USE** a cláusula `WHERE` em seu comando `DELETE` especificando uma ou mais condições para a atualização.


```sql
DELETE FROM fabricantes WHERE id = 4;
DELETE FROM fabricantes WHERE id = 1;

DELETE FROM produtos WHERE id = 4;

DELETE FROM fabricantes WHERE id = 2;
```

## SELECT: outras formas de uso

### Classificação/Ordenação

```sql
-- DESC: ordena em ordem decrescente
-- ASC: ordena em ordem crescente (padrão)
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY preco DESC;

SELECT nome, preco, quantidade FROM produtos
WHERE fabricante_id = 5 ORDER BY quantidade;
```

### Operações e funções de agregação

```sql
-- Função de SOMA (SUM)
SELECT SUM(preco) FROM produtos;

-- alias/apelido pra colunas
SELECT SUM(preco) AS Total FROM produtos;
SELECT SUM(preco) AS "Total dos Preços dos Produtos" FROM produtos; 
SELECT nome AS Produto, preco as Preço FROM produtos;
SELECT nome Produto, preco Preço FROM produtos; -- omitindo o AS

-- Funções de formatação/configuração: FORMAT e REPLACE
SELECT FORMAT(SUM(preco), 2) AS Total FROM produtos;
SELECT REPLACE(FORMAT(SUM(preco), 2), ",", ".") AS Total FROM produtos;

-- Função de média: AVG (Average) 
-- Função de arredondamento: ROUND
SELECT AVG(preco) AS "Média dos Preços" FROM produtos;
SELECT ROUND(AVG(preco), 2) AS "Média dos Preços" FROM produtos;

-- Função de contagem: COUNT
SELECT COUNT(id) AS "Qtd de Produtos" FROM produtos;
SELECT COUNT(DISTINCT fabricante_id) AS "Qtd de Fabricantes com Produtos" FROM produtos;

-- Operações matemáticas
SELECT nome, preco, quantidade, (preco * quantidade) as Total
FROM produtos;

--- Segmentação/Agrupamento de resultados
SELECT fabricante_id, SUM(preco) AS Total FROM produtos
GROUP BY fabricante_id;
```



## Consultas (Queries) em duas ou mais tabelas relacionadas (JUNÇÃO/JOIN)

### Exibir o nome do produto e o nome do fabricante do produto

```sql
-- SELECT nomeDaTabela1.nomeDaColuna, nomeDaTabela2.nomeDaColuna, 
SELECT produtos.nome AS Produto, fabricantes.nome AS Fabricante

-- JOIN permite JUNTAR as tabelas no momento do SELECT
FROM produtos JOIN fabricantes

-- ON tabela1.chave_estrangeira = tabela2.chave_primaria
ON produtos.fabricante_id = fabricantes.id;
```

### Nome do produto, preço do produto, nome do fabricante ordenados pelo nome do produto e pelo preço

```sql
SELECT 
    produtos.nome AS Produto,
    produtos.preco AS Preço,
    fabricantes.nome AS Fabricante
FROM produtos INNER JOIN fabricantes
ON produtos.fabricante_id = fabricantes.id
ORDER BY Produto ASC, Preço DESC;
```

### Fabricante, Soma dos Preços, Quantidade de Produtos POR Fabricante

```sql
SELECT
    fabricantes.nome AS Fabricante,
    SUM(produtos.preco) AS Total,
    COUNT(produtos.fabricante_id) AS "Qtd de Produtos"
FROM produtos RIGHT JOIN fabricantes
ON produtos.fabricante_id = fabricantes.id
GROUP BY Fabricante
ORDER BY Total;    
```