# Comandos usados no 1° Exercício de Bnaco de dados

### Criar tabela de genero

``` sql
CREATE TABLE generos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);
```

## Criar tabela filmes
``` sql
CREATE TABLE filmes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulodofilme VARCHAR(100) NOT NULL,
    datadelancamento DATE NOT NULL,
    generos_id INT NOT NULL
);
```

## Craindo tabela detalhes
``` sql
CREATE TABLE detalhes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    duracaodofilme INT NOT NULL,
    sinopse TEXT(10000),
    orcamento DECIMAL(16,2),
    bilheteria DECIMAL(16.2),
    filmes_id INT NOT NULL
);
```


### Criando relacionamento entre tabelas e configurar chave estrangeira

``` sql
ALTER TABLE filmes
    ADD CONSTRAINT fk_filmes_generos
    FOREIGN KEY (generos_id) REFERENCES generos(id);
```

``` sql
ALTER TABLE detalhes
    ADD CONSTRAINT fk_detalhes_filmes
    FOREIGN KEY (filmes_id) REFERENCES filmes(id);
```

# Exercício  01


#### Adiconando novos fabricantes
```sql
INSERT INTO fabricantes (nome) VALUES ('Positivo'),('Microsft')
```

#### Adiconando novos produtos 

```sql
INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES(
    'Xbox Series S',
    'Velocidade e desempenho de última geração.',
    1997.00,
    5,
    8
), 
(
    'Notebook Motion',
    'Intel Dual Core 4GB de RAM, 128GB SSD e Tela 14,1 polegadas.',
    1213.65,
    8,
    7
);
```

# Mini-exercício 02

```sql
SELECT nome, descricao  FROM produtos WHERE fabricante_id = 3;
```

# Mini-exercício 03

```sql
-- Exibir nome, descricao dos produtos da apple e da samsung (USANDO (OU))
SELECT nome, descricao FROM produtos WHERE fabricante_id = 3  OR  fabricante_id = 5
```

## EXERCÍCIO 

#### Adicionando novos generos

```sql
INSERT INTO generos (nomedogenero) VALUES ('Terror'), ('Suspense'), ('Fantasia'), ('Ação');


INSERT INTO filmes (titulodofilme, datadelancamento, generos_id)
VALUES(
    'Invocação do mal 1',
    '2013-09-13',
    1
);

INSERT INTO filmes (titulodofilme, datadelancamento, generos_id)
VALUES(
    'O Iluminado',
    '1980-10-29',
    2
);

INSERT INTO filmes (titulodofilme, datadelancamento, generos_id)
VALUES(
    'Wicked',
    '2024-11-22',
    3
);

INSERT INTO filmes (titulodofilme, datadelancamento, generos_id)
VALUES(
    'Busca Implacável',
    '2008-01-30',
    4
);

INSERT INTO detalhes (filmes_id, duracaodofilme, sinopse, orcamento, bilheteria)
VALUES(
   1,
   112,
   'Invocação do Mal 1, segue os investigadores paranormais Ed e Lorraine Warren, que tentam salvar uma família de uma entidade demoníaca em sua casa.',
   119000000,
   319000000
);


```

