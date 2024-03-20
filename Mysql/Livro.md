# Introdução a Banco de Dados Relacional - Mysql

Independentemente do aplicativo que se deseja usar para o armazenamento e manipulação das informações, todos os bancos de dados são constinstuídos por elementos básicos: campos, colunas, linhas ou tuplas e tabelas.
Campos são os espaços reservados para inserção de um determinado dado;
as colunas são os registros de um determinado campo; as tuplas são as linhas de registros de um conjunto de campos; e as tabelas são os conjuntos de linhas, campos e colunas.

* Banco são um conjuto de tabelas relacionais, tão chamados de relações - dai o nome de banco relacional

## Linguagem SQL 
A três categorias principais na utilização dessa linguagem. São elas:
* DML Linguagem de Manipulação de Dados: esses comandos indicam uma ação para o SGBD executar. Utilizados para recuperar, inserir e modificar um registro no banco de dados. Seus comandos são:
INSERT, DELETE, UPDATE, SELECT e LOCK
* DDL Linguagem de Definição de Dados: comandos DDL são responsáveis pela criação, alteração e exclusão dos objetos no banco de dados.
São eles: CREATE TABLE, CREATE INDEX, ALTER TABLE, DROP
TABLE, DROP VIEW e DROP INDEX;
* DCL Linguagem de Controle de Dados: responsável pelo controle de
acesso dos usuários, controlando as sessões e transações do SGBD. Alguns de seus comandos são: COMMIT, ROLLBACK, GRANT e REVOK

---

### Tipos de dados
O MySQL, como a maioria dos outros SGBD, possui 3 categorias de tipos
de dados: texto, número e data/tempo.
**Tipo texto**
* CHAR(tamanho): Este tipo de dado é usado para armazenar strings de tamanho fixo. Quando você define um campo como CHAR, você precisa especificar o tamanho máximo da string que será armazenada nesse campo. Os espaços em branco são usados para preencher qualquer espaço não utilizado até o tamanho máximo. Por exemplo, se você definir um campo CHAR(10) e inserir "ABC" nele, ele será armazenado como "ABC " (com espaços em branco adicionados para preencher até o tamanho máximo de 10 caracteres). Isso significa que os valores armazenados ocuparão sempre o mesmo espaço na memória, independentemente do comprimento real da string.

* VARCHAR(tamanho): Este tipo de dado é usado para armazenar strings de tamanho variável. Quando você define um campo como VARCHAR, você também precisa especificar o tamanho máximo da string, mas ele só usará o espaço necessário para armazenar os dados reais. Por exemplo, se você definir um campo VARCHAR(10) e inserir "ABC" nele, ele será armazenado como "ABC", ocupando apenas 3 caracteres na memória. Isso significa que os valores armazenados podem variar em tamanho, dependendo do comprimento real da string. Ele possui as características do tipo CHAR, com a diferença de que, se você criar com mais de 255 caracteres, ele transforma para o tipo TEXT. Ou seja, se for criar algum campo com mais de 255, já crie como TEXT.

* TEXT: guarda uma string: com o tamanho máximo de 65.535 caracteres.

* BLOB: é o tipo de dado medido pela quantidade de bytes, em vez de
pela quantidade de caracteres, conforme a maioria. Pode salvar por
imagens, por exemplo, com o máximo de 65.535 bytes de arquivo.

---

**Dica:** *Em muitos lugares você encontrará exemplos que salvam as imagens diretamente no banco de dados. Mas, em vez de salvá-las nele, prefira utilizar um campo TEXT para salvar apenas o caminho em que a imagem se encontra e, por meio da programação de sua aplicação, linká-la. Assim, você ganhará em desempenho de banco de dados, pois não vai salvá-la no banco. Também, se você for desenvolver em duas plataformas que usem bancos de dados distintos, isso facilitará quando quiser recuperá-las.*

---

* Tipo Numerico

TINYINT: guarda números do tipo inteiro. Suporta de -128 até 127
caracteres.
* SMALLINT: guarda números do tipo inteiro. Suporta de -32768 até
32767 caracteres.
* MEDIUMINT: guarda números do tipo inteiro. Suporta de -8388608
até 8388607 caracteres.
* INT(tamanho): guarda números inteiros. Suporta de -2147483648 até
2147483647 caracteres. O número máximo de caracteres pode ser especificado entre parênteses.
* BIGINT: guarda números do tipo inteiro. Suporta de -
9223372036854775808 até 9223372036854775807 caracteres.
* FLOAT(tamanho,decimal): guarda números REAIS. O número máximo de caracteres pode ser especificado entre parênteses. Deve-se especificar o tamanho inteiro e o tamanho numérico da coluna.
 DOUBLE(tamanho,decimal): guarda números REAIS. O número
máximo de caracteres pode ser especificado entre parênteses. Devese especificar o tamanho inteiro e o tamanho numérico da coluna. Esse
tipo armazena uma quantidade maior de número do que os campos do
tipo FLOAT

--- 

**Tipo date/time**
* DATE(): tipo de campo que vai armazenar datas no: YYYY-MM-DD,
onde Y refere-se ao ano, M ao mês e D ao dia;
* DATETIME(): a combinação de data e tempo, no formato YYYY-MMDD HH:MI:SS;
* TIME(): armazena horas, minutos e segundos no formato HH:MI:SS.

---

**Três etapas para a construção de qualaquer Projeto** 
* Fase conceitual: na qual temos um cenário da vida real, e, baseado
nele, faremos o levantamento de requisitos que o projeto deve atender.
Nesta etapa, devemos explorar todas as necessidades do problema que
vamos resolver e, com essas informações, conseguiremos criar um modelo conceitual, que será independente da tecnologia que utilizaremos.
Registraremos que dados podem aparecer no banco, mas não como estes dados estão armazenados. Por exemplo: cadastro de clientes (dados necessários: nome fantasia, razão social, endereço, CNPJ, cidade,
estado, telefone etc.).

* Fase lógica: ao contrário dos modelos conceituais, os lógicos são os
modelos em que os objetos, suas características e seus relacionamentos
têm suas representações de acordo com as regras de implementação e
limitantes impostos por alguma tecnologia. Ele é utilizado já na fase de projeto mais independente de dispositivo físico, implementando conceitos de construção de um banco de dados. Por exemplo: a figura 2.7;

* Fase física: elaborada a partir do modelo lógico, leva em consideração
limites impostos por dispositivo físico e por requisitos não funcionais
dos programas que acessam os dados. Um SGBD diferente poderá definir um modo diferente de implementação física das características e
dos recursos necessários para o armazenamento e a manipulação das
estruturas de dados. 








---

















### Requisitos para o projeto
No decorrer deste livro, vamos simular que fomos contratados para desenvolver um projeto para um cliente, que solicitou um sistema para vendas de
produtos. Nesse sistema, ele gostaria de fazer os seguintes cadastros:
* Clientes
* Fornecedores
* Vendedores
* Produtos
* Venda

```sql
create database Comercial;


show databases; -- comando pra conefrir criação do banco de dado


use Comercial;
```
