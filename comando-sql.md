# comandos SQL - Documentação
 
## Modelagem Física
 
Neste arquivo está a referência de comando visando a estruturação do banco de dados MySQL/MariaDB.
 
### Criar bande de dados
 
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

 