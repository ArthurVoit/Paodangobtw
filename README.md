Instruções de como usar o software: Na página inicial o cliente pode escolher entre 3 funções sendo elas: Pedidos: Onde é possível ver os pedidos realizados, onde todos os pedidos cadastrados aparecerão nesta página. Cadastrar Itens: Onde é possível cadastrar novos itens com seus dados, sendo eles nome, data de validade, preço e descrição. Usuários: Onde é possível cadastrar um novo usuário com seus dados, sendo eles nome, telefone, email e senha.

Pré requisitos: Navegador de ler arquivos html, compatível com o MySQL e o Xampp

Passos: Baixe o repositório Mova o repositório a uma pasta no xampp Abra o xampp Configure a porta desejada e ative o MySQL Abra o projeto no navegador de sua escolha

Script SQL: CREATE DATABASE padaria_paodango; USE padaria_paodango;

CREATE TABLE categorias ( id_categoria INT AUTO_INCREMENT PRIMARY KEY, nome_categoria VARCHAR(50) NOT NULL );

CREATE TABLE produtos ( id_produto INT AUTO_INCREMENT PRIMARY KEY, nome_produto VARCHAR(100) NOT NULL, preco_produto DECIMAL(10,2) NOT NULL, quantidade_produto INT NOT NULL, id_categoria INT, FOREIGN KEY (id_categoria) REFERENCES categorias(id_categoria) );

CREATE TABLE clientes ( id_cliente INT AUTO_INCREMENT PRIMARY KEY, nome_cliente VARCHAR(100) NOT NULL, email_cliente VARCHAR(100), telefone_cliente VARCHAR(20) );

CREATE TABLE pedidos ( id_pedido INT AUTO_INCREMENT PRIMARY KEY, id_cliente INT NOT NULL, data_pedido DATETIME DEFAULT CURRENT_TIMESTAMP, total_pedido DECIMAL(10,2), FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente) );

CREATE TABLE itens_pedido ( id_itenspedido INT AUTO_INCREMENT PRIMARY KEY, id_pedido INT NOT NULL, id_produto INT NOT NULL, quantidade_itenspedido INT NOT NULL, preco_itenspedido DECIMAL(10,2), FOREIGN KEY (id_pedido) REFERENCES pedidos(id_pedido), FOREIGN KEY (id_produto) REFERENCES produtos(id_produto) );
