# grupo_2_av2
/*GRUPO 2*/
drop database pizzaria;

create database pizzaria;

use pizzaria;

create table prato(
	id int not null auto_increment, primary key(id),
    nome varchar(255) not null,
    descricao varchar(255) not null,
    preco int not null
);

insert into prato (nome, descricao, preco) values("Pizza Margherita", "Pizza com tomate,
manjericão e mussarela", 40.00);
drop table prato;
select * from prato;

create table cliente(
	id int not null primary key auto_increment,
    nome varchar(255) not null,
    telefone varchar(255) not null,
    email varchar(255) not null
);
insert into cliente (nome, telefone, email) values("João", "123456789", "joao@example.com");
select * from cliente;


create table pedido(
	id int not null primary key auto_increment,
    data_pedido date not null,
    situacao varchar(255) not null,
    cliente_id int not null, 
		foreign key(cliente_id) references cliente(id)
);
insert into pedido (data_pedido, situacao, cliente_id) values( "2024-11-19", "Aberto", "1");
select * from pedido;


create table item_pedido(
	id int not null primary key auto_increment,
    quantidade int not null,
	prato_id int not null,
		foreign key(prato_id) references prato(id),
    pedido_id int not null,
		foreign key(pedido_id) references pedido(id)
);
insert into item_pedido (quantidade, prato_id, pedido_id) values( 2, "1",  "1");
select * from item_pedido;


create table mesa(
	id int not null primary key auto_increment,
    numero varchar(255) not null,
    capacidade varchar(255) not null
);
insert into mesa(numero, capacidade) values( "5", "4");
