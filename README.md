# Conceitos-e-MelhoresPraticas_BancosDados_PostgreSQL
Apoio para Aulas BD Postgress

## O que são dados
Valores
Fatos
Observações sobre eventos
Domínios que são estocados/ armazenados
Não sofrem alterações

Assim como nome de pessoas, objetos...

### Informações
Agrupamento de dados
Dando sentido a eles
Gerar valor aos dados
	Arvore (DADO), A partir da arvore é feito borracha (INFORMAÇÃO)

 

Dados que provem informação

# Modelagem Relacional
Modelar – criar modelo, que explica o comportamento do software (Modelo de dados)

Modelo de dados  Explica como os dados se relacionam entre si

## Modelo de dados representativo
Todos os dados armazenados, são armazenados em Tabelas, dentro de Linhas e Colunas  TUPLAS

Quando em tabelas
	Quando tem TELEFONES e PROPRIETARIOS
		Há a relação entre as tabelas

 	Um Para Um
IMAGEM NAO SUPORTADA
 	Muitos Para Um
IMAGEM NAO SUPORTADA

Dessa forma para relacionar elas em Linguagem BD Relacional
  Muitos para Um

# O que são tabelas
Conjunto de dados em colunas e linhas
Representa um objetivo em comum

# Como criar uma tabela
Filtrar em coisas físicas Tangiveis  Automovel, Arvore...
Funções  Perfil de usuário(Gerente, ADMIN, Operador...), ações, status de uma compra
Eventos ou Ocorrências  historico de dados, armazenagem de dados, erros de login...

Para Relacionamento
Definir a PrimaryKey (PK/ Chave Primaria)  
Informação nunca se repete (Como em um CPF), e através dela, a relação com as outras tabelas, a relação com as outras tabelas ou sua chave primaria

ForeignKey (FK/Chave Estrangeira) 
Valor de referência a uma PK de outra tabela
		É o que faz o relacionamento geral entre tabelas
			É a PK de OUTRA TABELA dentro da TABELA PRIMARIA
 

- Em um exemplo TELEFONIA
	Telefone não pode existir sem um PROPRIETÁRIO, e não pode existir sem OPERADORA
		Dessa forma, pega os IDs das classes PRINCIPAIS para a DEPENDENTE,
Tornando-as Chaves Estrangeiras

Como gerenciar / criar essas informações
Atraves de SGBD, programa que gerencia
	Um BD para criar essas Entidades e relacionamentos, RELACIONAL E NÃO RELACIONAL

Banco de Dados Open Source - Postgre SQL
	Sistema de gerenciamento BD
	Objeto Relacional

OpenSource
Pode ser alterado as informações entro dele, disponível para Community, e Enterprise
Arquitetura Multiprocessos
 
Postmaster
Sempre que tem que se conectar no BD, gerenciar conexões de instancias, e login
Childs
Gerencia as conexões que entram e saem do Banco de Dados
Storage
Grava os processos em Discos

Objetos e Tipos de Dados PostgreSQL
Instalando Postgress, vem o PGADMIN
	Caso de erro ao se Conectar o PGADMIN, tente isso:
1.	Liberar acesso ao Cluster, em postgresql.conf
2.	Liberar acesso ao Cluster para Usuario de BancoDeDados em pb_hba.conf
3.	Criar/ editar usuário

### Para Criação de Um Servidor e Começar a Brincar
Clicar em SERVERS, criar em SERVER GROUP Servidor AULA
Em seguida, clicando em AULA, criar em SERVER AULA_INTRO(PARA CRIAR UMA CONEXÃO)

Criando Servidor, indo em Schemas, consegue visualizar as tabelas, function...;

# Entendento o que são Usuarios 
- Roles  Funções 
- Groups contas  perfil de atuação
- User  usuários do sistema

Criando Roles, como no exemplo abaixo...
 
## Criando a Role Administradores, tem acesso total 
	Criando a Role professores, tem acesso na mesma classe e classes inferiores
	As roles, podem ler tudo em todas as Roles, mas so pode alterar conforme seu grau de hierarquia

	Se ela é uma SUPERUSUARIO, ela tem permissões Irrestritas sobre todas as demais classes/ roles

Tem permissão de criar ou não uma DB, pode ou não criar novas Roles

 

Se criar uma role, dizendo que ela herda de outra role, ela herda as informações 

# Analisando Configurações Usuarios
 
- Administradores
Cria novas DB | novas Roles | pode ter associações, Não pode se logar
- Professores
Não cria novas DB | nao cria novas roles| pode ter associações, não pode se loga, conexão limite 10
- Alunos
Não cria novas DB | nao cria novas roles| pode ter associações, não pode se loga, conexão limite 90

# Entendendo detalhes Config
Para associar uma Role a outra, é necessário ter INHERIT
	Para poder herdar ou repassar informações
IN ROLE  a role passa a pertencer a role informada
ROLE  A role atual se torna “mae” da role informada

# ! SE CASO ESQUECER DE COLOCAR ESSAS INFOS
Esqueci de colocar um professor na role professores
### utilizar GRANT
GRANT [role a ser concedida (Role “Cassiana”)] TO [role a assumir as permissões (Role “Professores””]
 

### Para Remover uma role de outra role (revogar)
 
Daniel não faz mais parte de Professores

### Alterar uma role (Alter Role)
 

### Para remover uma role
Daniel não faz parte mais da escola, excluir as informações dele
 

GRANTS  Administrar Acessos Usuarios
 

Declarando em Database | Schema | Table;
	Deve colocar GRANT{{tipos de acessos que ele vai ter}[, ...] | ALL[todos os privilegios]}
			ON DATABASE nome do banco de dados
			TO a role especificada
 

REVOKE Se quiser retirar as permissões do user
 

 

# Schema
A partir do moento que criou um DataBase, ele cria um Schema public

Se quiser criar um Schema próprio, so para produtos, ou processos

- CRIAR SCHEMA  CREATE SCHEMA produtos
- PARA RENOMEAR  ALTER SCHEMA produtos RENAME TO produto
- PARA APAGAR O SCHEMA  DROP SCHEMA produto
- Para ignorar os CREATES Já criados  IF NOT EXISTS 
      CREATE SCHEMAS IF NOT EXISTS produtos
 

## Criando Banco de Dados
	A partir de Criado um Servidor
Criar em DataBase  Postgress  clicar em TOOLS  ir em Query Tools (LINHA DE COMANDO BD)
 

Em seguida, fechar o Query, e abrir novamente em Tools, dentro da DATABASE criada...

# Criando Colunas	
 Quando criar colunas
  
## Primary Key DNV @_@
	DEVE DECLARAR UMA PRIMARY KEY	 	um Identificador para não repetir itens
 
A PK  Primary Key, pode conter mais de uma coluna para validação
	Como no caso de Camisetas, 
pode ter outras marcas que tenham P,M,G; 
pode ter mesmos tamanhos da mesma marca, e assim por diante
		 

## Foreign Key
São chaves primarias de outras tabelas, dentro de da tabela atual
A FK é uma referencia de CPF do Cliente, em Uma tabela de Venda de Carro identificado por Placa UM EXEMPLO
 
Declarando da seguinte forma  

### Tipos de Dados
Numericos Monetarios TiposDEDatas Booleanos BotString TextSource
 
	Os Principais são 
o	NUMERICOS | CHARACTER | DATA / TIME | BOOLEAN
- Numerico
 
Os Ultimos 3 elementos, são números sequenciais que definem os elementos

- Character
 
Varchar (100)  definir o tamanhos de letras no Varchar

- Data
 
Interval  Traz os intervalos de dados, a comparação entre 2 datas

- Boolean
 

## DMS E DDL (INSERT UPDATE DELETE SELECT), (CREATE ALTER REVOKE DROP)
DMS é a linguagem de Manipulação de Dados
DDL linguagem de definição desses dados (CREATE TABLE xxx)

### DMS faz todas as modificações de dados dentro das tabelas, enquanto DDS faz as modificações das tabelas, UM EXEMPLO BEM POR CIMA
- INSERT
 Para inserção de dados
INSERT INTO cliente (nome, email, ativo) VALUES ('André', 'contato.touchtech@gmail.com', TRUE);
  
- UPDATE
  
Sempre se ATENTAR em declarar UPDATE, pois senão colocar WHERE... 
	Todas as informações das tabelas passarão a ser a mesma que deu UPDATE
 	
- DELETE 
 
Sempre se ATENTAR em declarar DELETE, pois senão colocar WHERE... 
	Todas as informações das tabelas serão DELETADAS
 

!!! Em vez disso, pode somente dropar os valores, com DROP TABLE

 
Evitar Utilizar o SELECT *, pois não é uma boa pratica, é melhor fazr um SELECT codigo” FROM banco
Para solicitar os Codigos do banco, criados a partir de 2019
 
 

Condições 
Dentro do Select, pode adicionar Condições nas buscas
Select da tabela “X” valores, onde UM é IGUAL a OUTRO
	DEPOIS DA CONDIÇÃO, se quiser continuar com a requisição,
	INCREMENTAR com AND ou OR
“data MAIOR que Dezembro 2019 E/OU ativo IS TRUE”
 

- Truncate
TRUNCATE esvazia a tabela, mas para isso existe condições
 
- CREATE ALTER REVOKE DROP
 
 
## Chamando Todas As Colunas
Para visualizar todas as colunas de DETERMINADA TABELA

SELECT column_name, data_type FROM information_schema.columns WHERE table_name = ‘cliente_transacoes’;
	ELE VAI PEGAR TODAS AS COLUNAS DA TABELA cliente_transacoes

## Funções Aritméticas
Funções dentro de SELECT, para alteração dos valores
 

### AVG
SELECT AVG (valor) FROM cliente_transacoes;

Ele faz a Média dos valores dentro de tal tabela

### COUNT
Quantos clientes tenho disponível

SELECT COUNT (numero) FROM cliente;

Faz a contagem de quantos elementos, de determinada tabela

### MIN 
Traz o menor valor de determinada tabela
SELECT MIN (numero) FROM cliente;

### MAX
Traz o maior valor de determinada tabela
SELECT MIN (numero) FROM cliente;

### SUM
A soma de todos os valores de determinada tabela

SELECT SUM(valor) FROM cliente;
	Pega todos os valores da tabela cliente

SELECT SUM(valor), tipo_transacao FROM cliente_transacao GROUP BY tipo_transacao_id ORDER BY ASC/DESC
	CONSULTA MAIS DETALHADA
PEGANDO A SOMA DE VALORES DE CADA TIPO DE TRANSAÇÃO, COLOCANDO-AS EM UM GRUPO, EM ORDEM ASCENDENTE OU DESCENDENTE

# Revisando Antes de Codar
Pk para identificar o que não pode ser igual numa tabela
Fk referencia a Pk de outra dentro da tabela atual
Tipos de dados  VARCHAR  (N), INTEGER, BIGINT, BOOLEAN, TIMESTAMP
DDL DML (CRUD  Post Put Get Delete  CONVERTIDO EM DB  Insert Update Select Delete) 
Idepotencia
Propriedade que ações possuem, para serem executadas diversas vezes, sem alterar a Tabela ou objeto (COMO O “IF NOT EXIST”)
 

## JOINS  Relacionamento entre Tabelas
Quando se faz um Select e precisa unir uma ou mais tabelas

JOIN | LEFT JOIN | RIGHT JOIN | FULL JOIN | CROSS JOIN
 

Unir 2 tabelas, fazer um Select para buscar os elementos relacionados

Como declarar JOIN  
	SELECT tabela_1.campos, tabela_2.campos
	FROM tabela_1
	    JOIN tabela_2
	        ON tabela_2.campo = tabela_1.campo
Esse ON é idêntico a ON do BD, mas relacionado ao JOIN
	Ele é a comparação da tabela 2 a algum elemento declarado da tabela 1

Juntando nome com valor
 		 

Há tabelas a Esquerda, ou a Direita
   
   
   
### A Esquerda, ele retorna todas as que estão presentes 
Dando prioridade as que estão a esquerda

### A direita, se tiver, é a mesma situação que LEFT, MAS senão tiver nenhum dado, ELE RETORNA NULO
	Dá prioridade as que estão a direita
		Em ordem de quem vai entrar na tabela
 

### Full Join
	Traz todas as informações possíveis
		Ate mesmo as informações sem nenhum valor
 

Cross Join  NÃO É UMA BOA PRATICA
 


## CTE
Forma de organizar blocos de códigos para consultas grandes
	Gera colunas temporárias


# Começando Modelagem 
CREATE TABLE IF NOT EXISTS banco(
	numero INTEGER NOT NULL,
	nome VARCHAR(50) NOT NULL,
	ativo BOOLEAN NOT NULL DEFAULT TRUE, --Se a conta esta ativa = TRUE
	data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP, --registrado a data atual
	PRIMARY KEY(numero) -- Dizer que NUMERO é o principal
);

CREATE TABLE IF NOT EXISTS agencia (
	banco_numero INTEGER NOT NULL,
	numero INTEGER NOT NULL,
	nome VARCHAR(80) NOT NULL,
	ativo BOOLEAN NOT NULL DEFAULT TRUE,
	data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
	PRIMARY KEY(banco_numero, numero),
	FOREIGN KEY(banco_numero) REFERENCES banco(numero)
);

CREATE TABLE cliente(
	numero BIGSERIAL PRIMARY KEY, --Gera automaticamente
	nome VARCHAR(80) NOT NULL,
	email VARCHAR(150) NOT NULL,
	ativo BOOLEAN NOT NULL DEFAULT TRUE,
	data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
	--PRIMARY KEY JA DEFINIDO
	-- nao tenho FOREIGN KEY()
);

CREATE TABLE c_corrente(
	banco_numero INTEGER NOT NULL, --referenciando BANCO
	agencia_numero INTEGER NOT NULL,--referenciando AGENCIA
	cliente_numero BIGINT NOT NULL,--referenciando CLIENTE
	numero BIGINT NOT NULL,
	digito SMALLINT NOT NULL,
	ativo BOOLEAN NOT NULL DEFAULT TRUE,
	data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
	PRIMARY KEY (banco_numero, agencia_numero, cliente_numero, numero, digito), --SE PREFERIR, DEFINIR ISSO NUM OBJETO A PARTE
	--Quando REFERENCIAR mais de uma TABELA, Definir mais de um FOREIGN KEY
	--Quando Definir uma FOREIGN KEY, definir com as referencias que a Tabela ja possui em sua PK
	FOREIGN KEY (banco_numero, agencia_numero) REFERENCES agencia(banco_numero, numero),
	FOREIGN KEY (cliente_numero) REFERENCES cliente(numero)
);

CREATE TABLE transacoes(
	id BIGSERIAL PRIMARY KEY,
	nome VARCHAR(50) NOT NULL,-- NOME DA TRANSACAO
	ativo BOOLEAN NOT NULL DEFAULT TRUE,
	data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE cliente_transacoes(
	id BIGSERIAL PRIMARY KEY,
	banco_numero INTEGER NOT NULL, --referenciando BANCO
	agencia_numero INTEGER NOT NULL,--referenciando AGENCIA
	c_corrente_numero BIGINT NOT NULL,
	c_corrente_digito SMALLINT NOT NULL,
	cliente_numero BIGINT NOT NULL,
	tipo_transacao SMALLINT NOT NULL,
	valor NUMERIC(15, 2) NOT NULL, --15 digitos, com 2 casas decimais
	data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
	FOREIGN KEY (banco_numero, agencia_numero, c_corrente_numero, c_corrente_digito, cliente_numero) REFERENCES c_corrente (banco_numero, agencia_numero, cliente_numero, numero, digito) --SE PREFERIR, DEFINIR ISSO NUM OBJETO A PARTE
);

INSERT INTO banco (numero, nome) VALUES (0001, 'NuBank');
SELECT * FROM banco;

INSERT INTO cliente (nome, email, ativo) VALUES ('André', 'contato.touchtech@gmail.com', TRUE);
INSERT INTO cliente (nome, email, ativo) VALUES ('Felipe', 'contato.touchtech@gmail.com', FALSE);
SELECT * FROM cliente;
SELECT * FROM cliente WHERE ativo IS FALSE;


 

 
   


