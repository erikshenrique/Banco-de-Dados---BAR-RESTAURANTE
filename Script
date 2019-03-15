-- -----------------------------------------------------
-- Banco de Dados de Bar e Restaurante
-- Desenvolvido: Eriks Henrique dos Santos
-- -----------------------------------------------------

CREATE SCHEMA IF NOT EXISTS `projeto` DEFAULT CHARACTER SET utf8 ;
USE `projeto` ;

-- -----------------------------------------------------
-- Table `projeto`.`usuario`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`usuario` (
  `id_usuario` INT NOT NULL auto_increment,
  PRIMARY KEY (`id_usuario`))
ENGINE = InnoDB;

insert into usuario values
(default),
(default);

describe usuario;

select * from usuario;

-- -----------------------------------------------------
-- Table `projeto`.`pedido`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`pedido` (
  `id_pedido` INT NOT NULL auto_increment,
  `usuario_id_usuario` INT NOT NULL,
  PRIMARY KEY (`id_pedido`, `usuario_id_usuario`),
  INDEX `fk_pedido_usuario_idx` (`usuario_id_usuario` ASC),
  CONSTRAINT `fk_pedido_usuario`
    FOREIGN KEY (`usuario_id_usuario`)
    REFERENCES `projeto`.`usuario` (`id_usuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

insert into pedido values
(default, '1'),
(default, '2');

describe pedido;

select * from pedido;

-- -----------------------------------------------------
-- Table `projeto`.`categoria`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`categoria` (
  `id_categoria` INT NOT NULL auto_increment,
  `nome_categoria` VARCHAR(50) NOT NULL,
  `quantidade_ categoria` INT NOT NULL,
  `peso_categoria` DOUBLE NOT NULL,
  `pedido_id_pedido` INT NOT NULL,
  PRIMARY KEY (`id_categoria`, `pedido_id_pedido`))
ENGINE = InnoDB;

insert into categoria values
(default, 'Bebidas', '1', '0','1'),
(default, 'Lanches', '1', '0.5','2');

describe categoria;

select * from categoria;

-- -----------------------------------------------------
-- Table `projeto`.`produto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`produto` (
  `id_produto` INT NOT NULL auto_increment,
  `nome_produto` VARCHAR(30) NOT NULL,
  `quantidade_produto` DOUBLE NOT NULL,
  `peso_produto` DOUBLE NOT NULL,
  `valor_produto` DOUBLE NOT NULL,
  `categoria_id_categoria` INT NOT NULL,
  `categoria_pedido_id_pedido` INT NOT NULL,
  `categoria_pedido_usuario_id_usuario` INT NOT NULL,
  PRIMARY KEY (`id_produto`, `categoria_id_categoria`, `categoria_pedido_id_pedido`, `categoria_pedido_usuario_id_usuario`),
  INDEX `fk_produto_categoria1_idx` (`categoria_id_categoria` ASC, `categoria_pedido_id_pedido` ASC, `categoria_pedido_usuario_id_usuario` ASC),
  CONSTRAINT `fk_produto_categoria1`
    FOREIGN KEY (`categoria_id_categoria` , `categoria_pedido_id_pedido`)
    REFERENCES `projeto`.`categoria` (`id_categoria` , `pedido_id_pedido`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

insert into produto values
(default, 'Água S/Gás','1','0','2.00','1','1','1'),
(default, 'X-Salada','1','0.200','5.00','2','2','2');

SELECT categoria.id_categoria AS Categoria, produto.nome_produto AS Produto
FROM produto
INNER JOIN categoria
ON produto.categoria_id_categoria = categoria.id_categoria
INNER JOIN produto
ON produto.nome_produto = produto.id_produto;

describe produto;

select * from produto;

-- -----------------------------------------------------
-- Table `projeto`.`excecao`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`excecao` (
  `id_excecao` INT NOT NULL auto_increment,
  `nome_excecao` VARCHAR(30) NOT NULL,
  `produto_id_produto` INT NOT NULL,
  `produto_categoria_id_categoria` INT NOT NULL,
  `produto_categoria_pedido_id_pedido` INT NOT NULL,
  `produto_categoria_pedido_usuario_id_usuario` INT NOT NULL,
  PRIMARY KEY (`id_excecao`, `produto_id_produto`, `produto_categoria_id_categoria`, `produto_categoria_pedido_id_pedido`, `produto_categoria_pedido_usuario_id_usuario`),
  INDEX `fk_excecao_produto1_idx` (`produto_id_produto` ASC, `produto_categoria_id_categoria` ASC, `produto_categoria_pedido_id_pedido` ASC, `produto_categoria_pedido_usuario_id_usuario` ASC),
  CONSTRAINT `fk_excecao_produto1`
    FOREIGN KEY (`produto_id_produto` , `produto_categoria_id_categoria` , `produto_categoria_pedido_id_pedido` , `produto_categoria_pedido_usuario_id_usuario`)
    REFERENCES `projeto`.`produto` (`id_produto` , `categoria_id_categoria` , `categoria_pedido_id_pedido` , `categoria_pedido_usuario_id_usuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

insert into excecao values
(default, 'Gelo','5','1','1','1'),
(default, 'Sem Cebola','6','2','2','2');

describe excecao;

select * from excecao;

-- -----------------------------------------------------
-- Table `projeto`.`pedido_has_produto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`pedido_has_produto` (
  `pedido_id_pedido` INT NOT NULL,
  `pedido_usuario_id_usuario` INT NOT NULL,
  `produto_id_produto` INT NOT NULL,
  `produto_categoria_id_categoria` INT NOT NULL,
  `produto_categoria_pedido_id_pedido` INT NOT NULL,
  `produto_categoria_pedido_usuario_id_usuario` INT NOT NULL,
  PRIMARY KEY (`pedido_id_pedido`, `pedido_usuario_id_usuario`, `produto_id_produto`, `produto_categoria_id_categoria`, `produto_categoria_pedido_id_pedido`, `produto_categoria_pedido_usuario_id_usuario`),
  INDEX `fk_pedido_has_produto_produto1_idx` (`produto_id_produto` ASC, `produto_categoria_id_categoria` ASC, `produto_categoria_pedido_id_pedido` ASC, `produto_categoria_pedido_usuario_id_usuario` ASC),
  INDEX `fk_pedido_has_produto_pedido1_idx` (`pedido_id_pedido` ASC, `pedido_usuario_id_usuario` ASC),
  CONSTRAINT `fk_pedido_has_produto_pedido1`
    FOREIGN KEY (`pedido_id_pedido` , `pedido_usuario_id_usuario`)
    REFERENCES `projeto`.`pedido` (`id_pedido` , `usuario_id_usuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_pedido_has_produto_produto1`
    FOREIGN KEY (`produto_id_produto` , `produto_categoria_id_categoria` , `produto_categoria_pedido_id_pedido` , `produto_categoria_pedido_usuario_id_usuario`)
    REFERENCES `projeto`.`produto` (`id_produto` , `categoria_id_categoria` , `categoria_pedido_id_pedido` , `categoria_pedido_usuario_id_usuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

insert into pedido_has_produto values
('1','1','5','1','1','1'),
('2','2','6','2','2','2');

SELECT pedido.id_pedido AS Pedido, produto.nome_produto AS Produto
FROM pedido_has_produto
INNER JOIN pedido
ON pedido_has_produto.pedido_id_pedido = pedido.id_pedido
INNER JOIN produto
ON pedido_has_produto.produto_id_produto = produto.id_produto;

describe pedido_has_produto;

select * from pedido_has_produto;

-- -----------------------------------------------------
-- Table `projeto`.`pedido_has_excecao`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `projeto`.`pedido_has_excecao` (
  `pedido_id_pedido` INT NOT NULL,
  `pedido_usuario_id_usuario` INT NOT NULL,
  `excecao_id_excecao` INT NOT NULL,
  `excecao_produto_id_produto` INT NOT NULL,
  `excecao_produto_categoria_id_categoria` INT NOT NULL,
  `excecao_produto_categoria_pedido_id_pedido` INT NOT NULL,
  `excecao_produto_categoria_pedido_usuario_id_usuario` INT NOT NULL,
  PRIMARY KEY (`pedido_id_pedido`, `pedido_usuario_id_usuario`, `excecao_id_excecao`, `excecao_produto_id_produto`, `excecao_produto_categoria_id_categoria`, `excecao_produto_categoria_pedido_id_pedido`, `excecao_produto_categoria_pedido_usuario_id_usuario`),
  INDEX `fk_pedido_has_excecao_excecao1_idx` (`excecao_id_excecao` ASC, `excecao_produto_id_produto` ASC, `excecao_produto_categoria_id_categoria` ASC, `excecao_produto_categoria_pedido_id_pedido` ASC, `excecao_produto_categoria_pedido_usuario_id_usuario` ASC),
  INDEX `fk_pedido_has_excecao_pedido1_idx` (`pedido_id_pedido` ASC, `pedido_usuario_id_usuario` ASC),
  CONSTRAINT `fk_pedido_has_excecao_pedido1`
    FOREIGN KEY (`pedido_id_pedido` , `pedido_usuario_id_usuario`)
    REFERENCES `projeto`.`pedido` (`id_pedido` , `usuario_id_usuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_pedido_has_excecao_excecao1`
    FOREIGN KEY (`excecao_id_excecao` , `excecao_produto_id_produto` , `excecao_produto_categoria_id_categoria` , `excecao_produto_categoria_pedido_id_pedido` , `excecao_produto_categoria_pedido_usuario_id_usuario`)
    REFERENCES `projeto`.`excecao` (`id_excecao` , `produto_id_produto` , `produto_categoria_id_categoria` , `produto_categoria_pedido_id_pedido` , `produto_categoria_pedido_usuario_id_usuario`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

insert into pedido_has_excecao values
('1','1','3','5','1','1','1'),
('2','2','4','6','2','2','2');

SELECT excecao.nome_excecao AS Excecao, produto.nome_produto AS Produto, pedido.id_pedido AS Pedido
FROM pedido_has_excecao
INNER JOIN excecao
ON pedido_has_excecao.excecao_id_excecao = excecao.id_excecao
INNER JOIN produto
ON pedido_has_excecao.excecao_produto_id_produto = produto.id_produto
INNER JOIN pedido
ON pedido_has_excecao.pedido_id_pedido = pedido.id_pedido;

describe pedido_has_excecao;

select * from pedido_has_excecao;
