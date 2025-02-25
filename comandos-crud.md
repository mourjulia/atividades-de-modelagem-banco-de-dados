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
```