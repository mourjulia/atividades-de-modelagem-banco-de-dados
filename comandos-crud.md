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
````sql
-- CUIDADO💣💣💣💣📌📌📌!!!!!!! UPDATE SEMPRE acompanha WHERE 
-- Trocar o nome do fabricante Asus para Asus do Brasil
UPDATE fabricantes SET nome = 'Asus do Brasil' WHERE id = 1;

-- Mini-exeicício: alterar a quantidade para 10 dos produtos que custam abaixo de 2000 exceto o da Microsoft.



```