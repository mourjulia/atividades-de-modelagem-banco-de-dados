# Comandos para operações de CRUD no Banco de Dados

## Resumo 

- C -> **C**reate -> **INSERT**: Inserir dados/registros na tabela
- R -> **R**ead   -> **SELECT**: Colcultar/ler dados/registros na tabela
- U -> **U**pdate -> **UPDATE**: Atualizar dados/registros na tabela
- D -> **D**elete -> **DELETE**: Excluir dados/registros na tabela 

---

## INSERT (Fabricantes)

```sql
INSERT INTO fabricantes (nome) VALUES('Asus');
INSERT INTO fabricantes (nome) VALUES('Dell');
INSERT INTO fabricantes (nome) VALUES('Apple');

INSERT INTO fabricantes (nome) VALUES ('LG'),('Samsung'),('Brastemp')
```

## Select (Fabricantes)

```sql
SELECT *FROM fabricantes;
```

---

## INSERT (Produtos)

```sql
INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES('Ultrabook', 'Equipamento de Última geração cheio de 
        recursos', 3999.45, 7, 2 )

INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES(
    'Tablet Android',
    'Tablet com versão 16 do sistema operacional Android, Possui tela de 10 polegadas e armazenamento de 128 GB.',
    900, 
    12, 
    5
);



INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES(
    'Geladeira',
    'Refrigerador frost-free com acesso à intenet',
    5000,
    12,
    6
), 
(
    'Iphone 18 Pro Max Ferradão',
    'Smartphone Apple cheio de frescura e caro para caramba',
    9666.66,
    3,
    3
), (
    'Ipad Mini',
    'Tablet Apple com tela retina display e varias outras coisas',
    4999.12,
    5,
    3
);
```


## SELECT (Produtos)

```sql
-- Lendo todas as colunas de todos os registros 
SELECT * FROM produtos;

-- Lendo somente o nome e preço de todos os registros
SELECT nome, preco FROM produtos; 
SELECT preco, nome FROM produtos; -- Pode ser ao contrário

--Mostrar nome, preco e quantidade SOMENTE DOS PRODUTOS QUE CUSTAM ABAIXO DE 5000
SELECT nome, preco, quantidade FROM produtos WHERE preco < 5000;


-- mini Exercicío: Mostrar o nome e descrição somente dos produtos da apple

SELECT nome, descricao  FROM produtos WHERE fabricante_id = 3;
```

### Operadores Lógicos: E, OU e NÃO 

#### E (AND)

```sql
--Exibir nome  e preco dos produtos que custam entre 2000 e 6000
SELECT nome, preco FROM produtos WHERE preco >= 2000 AND preco <=6000;
```

#### OU (OR)

```sql
-- Exibir nome, descricao dos produtos da apple e da samsung
SELECT nome, descricao FROM produtos WHERE fabricante_id = 3  OR  fabricante_id = 5;

-- Versão usando a função SQL IN()
SELECT nome, descricao FROM produtos WHERE fabricante_id IN(3, 5);
```

#### NÃO (NOT)

```sql
-- Nome de todos os produtos exceto o da positivo
SELECT nome, descricao, preco FROM produtos WHERE NOT fabricante_id = 7;

-- Versão usando operador relacional de "diferença/diferente"
SELECT nome, descricao, preco FROM produtos WHERE fabricante_id != 7;
```

------

## UPDATE (Fabricantes e Produtos) 
```sql
-- CUIDADO💣💣💣💣📌📌📌!!!!!!! UPDATE SEMPRE acompanha WHERE 
-- Trocar o nome do fabricante Asus para Asus do Brasil
UPDATE fabricantes SET nome = 'Asus do Brasil' WHERE id = 1;

-- Mini-exeicício: alterar a quantidade para 10 dos produtos que custam abaixo de 2000 exceto o da Microsoft.

UPDATE produtos SET quantidade = 10 WHERE preco <2000 AND NOT fabricante_id = 8;

```

## UPDATE (Fabricantes e Produtos) 
```sql
-- CUIDADO💣💣💣💣📌📌📌!!!!!!! UPDATE SEMPRE acompanha WHERE 

DELETE FROM fabricantes WHERE id = 4;
DELETE FROM fabricantes WHERE id = 1;

DELETE FROM produtos WHERE id = 4;

DELETE FROM fabricantes WHERE id = 3;
```

--------------------------------------------------------------------------------
## SELECT: outras formas de uso
 
### Classificação/Ordenação
 
```sql
-- DESC: ordena em ordem decrescent
-- ASC: ordena em ordem crescente (padrão)
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY nome DESC;
 
SELECT nome, preco, quantidade FROM produtos
WHERE fabricante_id = 5 ORDER BY quantidade;
```
 
---
 
### Operações e funções de agregação
 
```sql
-- Função de SOMA (SUM)
SELECT SUM(preco) FROM produtos;
 
-- alias/apelido para coluna
SELECT SUM(preco) AS Total FROM produtos;
SELECT SUM(preco) AS "Total dos Preços dos Produtos" FROM produtos;
SELECT nome AS Produto, preco as Preço FROM produtos;
SELECT nome Produto,preco Preço FROM produtos; -- omitindo o AS
 
-- Funções de formatação/configuração: FORMAT e REPLACE
SELECT FORMAT(SUM(preco), 2) AS Total FROM produtod;
SELECT REPLACE(FORMAT(SUM(preco), 2), ",", ".") AS Total FROM produtos;
 
-- Função de média: AVG
SELECT AVG(preco) as "Média dos Preços" FROM produtos;
SELECT ROUND(AVG(preco), 2) AS "Média dos Preços" FROM produtos;
 
-- Função de contagem: COUNT
SELECT COUNT(id) AS "Qtd de Produtos" FROM produtos;
SELECT COUNT (DISTINCT fabricante_id) AS "Qtd de Fabricantes com Produtos" FROM produtos
 
-- Operações matemáticas
SELECT nome, preco, quantidade, (preco * quantidade) as Toltal
FROM produtos;
 
--- Segmentção/Agrupamento de resultados
SELECT fabricante_id, SUM(preco) AS Total FROM produtos
GROUP BY fabricante_id;
```
## Consultas (Queries) em duas ou mais tabelas relacionadas (JUNÇÃO/JOIN)
 
### Exibir o nome do produto e o nome do fabricante do produto
```sql
-- SELECT nomeDaTabela1.nomeDaColuna, nomeDaTabela2.nomeDa.Coluna,
SELECT produtos.nome, fabricantes.nome
 
-- JOIN permite Juntar as tabelas no momento do SELECT
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
 
### Fabricante, Soma dos Preços, QUnatidade de Produtos POR Fabricante
```sql
SELECT
    fabricantes.nome AS Fabricante,
    SUM(produtos.preco) AS Total, -- SUM equivale a soma, AS é o apleido da coluna
    COUNT(produtos.fabricante_id) AS "Qtd de produtos"
FROM produtos RIGHT JOIN fabricantes -- sql JOINS
ON produtos.fabricante_id = fabricantes.id
GROUP BY Fabricante
ORDER BY Total;

SELECT
    filmes.titulodofilme  AS "Nome do filme"
    generos.nomedogenero AS "nome do gênero"
    FROM filmes INNER JOIN generos
    ON filmes.generos_id = generos.id
    ORDER BY "Nome do filme" ASC, "nome do gênero" DESC;
```
 