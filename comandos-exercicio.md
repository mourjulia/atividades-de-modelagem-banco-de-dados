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

 


