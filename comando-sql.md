# comandos SQL - Documentação
 
## Modelagem Física
 
Neste arquivo está a referência de comando visando a estruturação do banco de dados MySQL/MariaDB.
 
### Criar banco de dados
 
``` sql
CREATE DATABASE vendas CHARACTER SET utf8mb4; 
```

### Criar tabela de Fabricantes

``` sql
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL 
);
```

### Visualizar detalhes estruturais da tabela
``` sql
DESC fabricantes;
```

### Criar tabela produtos
``` sql
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2) NULL,
    fabricante_id INT NOT NULL
);
```

### Criando relacionamento entre tabelas e configurar chave estrangeira

``` sql
ALTER TABLE produtos
    -- Adicionando uma restrição indicando o nome do relacionamento
    ADD CONSTRAINT fk_produtos_fabricantes

    -- Criando a chave-estrangeira (fabricante_id) que aponta para chave-primária (id) de OUTRA TABELA (fabricantes)
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);
```

### Exemplos de alterações estruturais em tabelas

#### Adicionar coluna
``` sql
ALTER TABLE produtos ADD quantidade INT NULL AFTER preco;
```

#### Renomear tabela

``` sql
ALTER TABLE forncecedores RENAME TO fabricantes
```

#### Renomear coluna 
``` sql
ALTER TABLE produtos CHANGE detalhes descricao TEXT(500) NULL;
```

 