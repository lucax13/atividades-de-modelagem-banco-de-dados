## Exercicio 04 - 26/02/2025

```sql
INSERT INTO generos (nome) VALUES('Terror');
INSERT INTO generos (nome) VALUES('Suspense');
INSERT INTO generos (nome) VALUES('Ação');
INSERT INTO generos (nome) VALUES('Fantasia');
```

```sql

INSERT INTO filmes (titulo, generos_id, lacamento)
VALUES ('velozes e furiosos', 3 ,'2020-02-07');

INSERT INTO filmes (titulo, generos_id, lacamento)
VALUES ('Panico', 1 , '2027-03-01');

INSERT INTO filmes (titulo, generos_id, lacamento)
VALUES ('A Mumia', 2 , '2026-04-05');

INSERT INTO filmes (titulo, generos_id, lacamento)
VALUES ('Star Wars', 4 ,'2024-06-03');
```
---------------------------------------

```sql
INSERT INTO detalhes (duracao, sinopse, bilheteria)
VALUES (120, 'Dois amigos de infancia crescem e viram pilotos de fuga', 55.000000  );
```

## uso dos joins no exercicio catalogo 
```sql
SELECT
    filmes.titulo AS "Título do filme",
    generos.nome AS "Gênero do filme"
FROM filmes
JOIN generos ON  filmes.genero_id = generos.id;

SELECT
    filmes.titulo AS "Título do filme",
    detalhes.sinopse AS "Resumo do filme"
FROM filmes
INNER JOIN detalhes ON filmes.id = detalhes.filme_id

SELECT 
    filmes.titulo AS filme,
    generos.nome AS genero,
    detalhes.sinopse AS resumo
FROM filmes
INNER  JOIN generos ON  filmes.genero_id = generos.id
INNER JOIN detalhes ON filmes.id = detalhes.filme_id;
```
