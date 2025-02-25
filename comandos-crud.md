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


