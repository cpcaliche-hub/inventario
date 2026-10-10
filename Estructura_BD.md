
-- MySQL dump 10.13  Distrib 8.0.42, for macos15 (arm64)
--
-- Host: 172.17.1.21    Database: sirisinv
-- ------------------------------------------------------
-- Server version	8.0.13

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `actas_bajas`
--

DROP TABLE IF EXISTS `actas_bajas`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `actas_bajas` (
  `actabaja_id` int(11) NOT NULL AUTO_INCREMENT,
  `numero` varchar(45) DEFAULT NULL,
  `fechahora` datetime DEFAULT NULL,
  `user_id` int(11) DEFAULT NULL,
  `head1` mediumtext,
  `head2` mediumtext,
  `body1` mediumtext,
  `body2` mediumtext,
  `body3` mediumtext,
  `body4` mediumtext,
  `body5` mediumtext,
  `foot1` mediumtext,
  `foot2` mediumtext,
  `foot3` mediumtext,
  `foot4` mediumtext,
  PRIMARY KEY (`actabaja_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`sistemas`@`%`*/ /*!50003 TRIGGER `actas_bajas_BEFORE_INSERT` BEFORE INSERT ON `actas_bajas` FOR EACH ROW BEGIN
	SET @consec = 0;
	SELECT consec + 1  INTO @consec FROM `documentos_contables` where documentocontable_id=2;
	SET NEW.numero = CONCAT(REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
	UPDATE documentos_contables set consec = @consec where documentocontable_id=2;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `actas_entrega_funcionario`
--

DROP TABLE IF EXISTS `actas_entrega_funcionario`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `actas_entrega_funcionario` (
  `actaentregafuncionario_id` int(11) NOT NULL AUTO_INCREMENT,
  `numero` varchar(45) DEFAULT NULL,
  `fechahora` datetime DEFAULT NULL,
  `responsable_id` int(11) DEFAULT NULL,
  `nombre` varchar(256) DEFAULT NULL,
  `identificacion` varchar(256) DEFAULT NULL,
  `cargo` varchar(256) DEFAULT NULL,
  `dependencia` varchar(256) DEFAULT NULL,
  `sede` mediumtext,
  `head1` mediumtext,
  `head2` mediumtext,
  `body1` mediumtext,
  `body2` mediumtext,
  `body3` mediumtext,
  `body4` mediumtext,
  `body5` mediumtext,
  `foot1` mediumtext,
  `foot2` mediumtext,
  `foot3` mediumtext,
  `foot4` mediumtext,
  PRIMARY KEY (`actaentregafuncionario_id`),
  KEY `fk_actentfun_idx` (`responsable_id`),
  CONSTRAINT `fk_actentfun` FOREIGN KEY (`responsable_id`) REFERENCES `responsables` (`responsable_id`)
) ENGINE=InnoDB AUTO_INCREMENT=248 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`sistemas`@`%`*/ /*!50003 TRIGGER `actas_entrega_funcionario_BEFORE_INSERT` BEFORE INSERT ON `actas_entrega_funcionario` FOR EACH ROW BEGIN
	SET @consec = 0;
	SELECT consec + 1  INTO @consec FROM `documentos_contables` where documentocontable_id=1;
	SET NEW.numero = CONCAT(REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
	UPDATE documentos_contables set consec = @consec where documentocontable_id=1;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `actividad_economica`
--

DROP TABLE IF EXISTS `actividad_economica`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `actividad_economica` (
  `actividadeconomica_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(10) NOT NULL,
  `descripcion` varchar(512) NOT NULL,
  PRIMARY KEY (`actividadeconomica_id`),
  UNIQUE KEY `IDX_ef1a6d6c0bcb4b1ef3a0f41578` (`codigo`)
) ENGINE=InnoDB AUTO_INCREMENT=552 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `activo_localiza`
--

DROP TABLE IF EXISTS `activo_localiza`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `activo_localiza` (
  `activolocaliza_id` int(11) NOT NULL AUTO_INCREMENT,
  `activo_id` int(11) DEFAULT NULL,
  `dependencia_id` int(11) DEFAULT NULL,
  `desde` date DEFAULT NULL,
  `hasta` date DEFAULT NULL,
  `responsable_id` int(11) DEFAULT NULL,
  `observacion` varchar(1024) DEFAULT NULL,
  PRIMARY KEY (`activolocaliza_id`),
  KEY `fk_actloc1_idx` (`activo_id`),
  KEY `fk_actloc2_idx` (`dependencia_id`),
  KEY `fk_actloc3_idx` (`responsable_id`),
  CONSTRAINT `fk_actloc1` FOREIGN KEY (`activo_id`) REFERENCES `activos` (`activo_id`),
  CONSTRAINT `fk_actloc2` FOREIGN KEY (`dependencia_id`) REFERENCES `dependencias` (`dependencia_id`),
  CONSTRAINT `fk_actloc3` FOREIGN KEY (`responsable_id`) REFERENCES `responsables` (`responsable_id`)
) ENGINE=InnoDB AUTO_INCREMENT=528 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `activos`
--

DROP TABLE IF EXISTS `activos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `activos` (
  `activo_id` int(11) NOT NULL AUTO_INCREMENT,
  `item_id` int(11) NOT NULL,
  `placa` varchar(80) DEFAULT NULL,
  `serial` varchar(80) DEFAULT NULL,
  `fecha_adquiere` date DEFAULT NULL,
  `fecha_disponible` date DEFAULT NULL,
  `costo` decimal(18,2) DEFAULT '0.00',
  `responsable_id` int(11) DEFAULT NULL,
  `dependencia_id` int(11) DEFAULT NULL,
  `imagen` varchar(256) DEFAULT NULL,
  `contabiliza` int(11) NOT NULL DEFAULT '0',
  `estado` varchar(1) DEFAULT 'R' COMMENT 'R=Registrado\nI=Inventario\nB=Baja',
  `fecha_localiza` date DEFAULT NULL,
  `recepcion_id` int(11) DEFAULT NULL,
  `proveedor_id` int(11) DEFAULT NULL,
  `causacion` int(11) DEFAULT '0',
  `causacion_entrega` int(11) DEFAULT '0',
  `observacion` varchar(512) DEFAULT NULL,
  `user_baja_id` int(11) DEFAULT NULL,
  `fecha_baja` datetime DEFAULT NULL,
  `causa_baja` varchar(1) DEFAULT NULL COMMENT 'D=Deterioro, P=Perdida, O=Obsoleto',
  `observa_baja` varchar(512) DEFAULT NULL,
  PRIMARY KEY (`activo_id`),
  UNIQUE KEY `placa_UNIQUE` (`placa`),
  KEY `fk_actitem_idx` (`item_id`),
  KEY `fk_actres_idx` (`responsable_id`),
  KEY `fk_actdep_idx` (`dependencia_id`),
  KEY `fk_recact_idx` (`recepcion_id`),
  KEY `fk_prvact_idx` (`proveedor_id`),
  CONSTRAINT `fk_actdep` FOREIGN KEY (`dependencia_id`) REFERENCES `dependencias` (`dependencia_id`),
  CONSTRAINT `fk_actitem` FOREIGN KEY (`item_id`) REFERENCES `items` (`item_id`),
  CONSTRAINT `fk_actres` FOREIGN KEY (`responsable_id`) REFERENCES `responsables` (`responsable_id`),
  CONSTRAINT `fk_prvact` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`),
  CONSTRAINT `fk_recact` FOREIGN KEY (`recepcion_id`) REFERENCES `recepciones` (`recepcion_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1500 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`sistemas`@`%`*/ /*!50003 TRIGGER `activos_BEFORE_UPDATE` BEFORE UPDATE ON `activos` FOR EACH ROW BEGIN
	IF OLD.`dependencia_id` is null and not NEW.dependencia_id is null THEN
		SET NEW.fecha_localiza = DATE(NOW());
    END IF;
    IF (not OLD.dependencia_id is null  AND NEW.dependencia_id <> OLD.dependencia_id) or (not OLD.responsable_id is null  AND NEW.responsable_id <> OLD.responsable_id) THEN
        insert into activo_localiza (activo_id, dependencia_id, desde, hasta, responsable_id, observacion) values (NEW.activo_id,OLD.dependencia_id,OLD.fecha_localiza, Now(), OLD.responsable_id, OLD.observacion);
        SET NEW.fecha_localiza = DATE(NOW());
    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `catalogo_contable`
--

DROP TABLE IF EXISTS `catalogo_contable`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `catalogo_contable` (
  `catalogo_id` int(11) NOT NULL AUTO_INCREMENT,
  `idpadre` int(11) DEFAULT NULL,
  `codigo` varchar(10) NOT NULL,
  `descripcion` varchar(256) NOT NULL,
  `vidautil` int(11) DEFAULT NULL,
  PRIMARY KEY (`catalogo_id`),
  UNIQUE KEY `codigo_UNIQUE` (`codigo`)
) ENGINE=InnoDB AUTO_INCREMENT=125 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `categorias`
--

DROP TABLE IF EXISTS `categorias`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `categorias` (
  `categoria_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(3) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  PRIMARY KEY (`categoria_id`),
  UNIQUE KEY `codigo` (`codigo`),
  UNIQUE KEY `nombre` (`nombre`)
) ENGINE=InnoDB AUTO_INCREMENT=295 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `clasificacion_tributaria`
--

DROP TABLE IF EXISTS `clasificacion_tributaria`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `clasificacion_tributaria` (
  `clasificaciontributaria_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(10) NOT NULL,
  `descripcion` varchar(30) NOT NULL,
  PRIMARY KEY (`clasificaciontributaria_id`),
  UNIQUE KEY `codigo` (`codigo`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='Clasificación Tributaria';
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `clientes`
--

DROP TABLE IF EXISTS `clientes`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `clientes` (
  `cliente_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(20) NOT NULL,
  `tercero_id` int(11) NOT NULL,
  `actividadeconomica_id` int(11) DEFAULT NULL,
  `nombre_comercial` varchar(80) DEFAULT NULL,
  `direccion1` varchar(80) DEFAULT NULL,
  `direccion2` varchar(80) DEFAULT NULL,
  `direccion3` varchar(80) DEFAULT NULL,
  `email` varchar(80) DEFAULT NULL,
  `telefono` varchar(80) DEFAULT NULL,
  `celular` varchar(80) DEFAULT NULL,
  `fecha_creacion` datetime NOT NULL,
  `contacto_cliente` varchar(80) DEFAULT NULL,
  `activo` tinyint(1) NOT NULL,
  `nombre_contacto1` varchar(80) DEFAULT NULL,
  `cargo1` varchar(80) DEFAULT NULL,
  `email_receptor1` varchar(30) DEFAULT NULL,
  `telefono_contacto1` varchar(20) DEFAULT NULL,
  `nombre_contacto2` varchar(80) DEFAULT NULL,
  `cargo2` varchar(80) DEFAULT NULL,
  `email_receptor2` varchar(30) DEFAULT NULL,
  `telefono_contacto2` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`cliente_id`),
  UNIQUE KEY `codigo_UNIQUE` (`codigo`),
  KEY `tercero_id` (`tercero_id`),
  KEY `actividadeconomica_id` (`actividadeconomica_id`),
  CONSTRAINT `clientes_ibfk_1` FOREIGN KEY (`tercero_id`) REFERENCES `terceros` (`tercero_id`),
  CONSTRAINT `clientes_ibfk_5` FOREIGN KEY (`actividadeconomica_id`) REFERENCES `actividad_economica` (`actividadeconomica_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `clientes_contactos`
--

DROP TABLE IF EXISTS `clientes_contactos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `clientes_contactos` (
  `clientecontacto_id` int(11) NOT NULL AUTO_INCREMENT,
  `cliente_id` int(11) NOT NULL,
  `nombre` varchar(80) DEFAULT NULL,
  `direccion` varchar(80) DEFAULT NULL,
  `email` varchar(80) DEFAULT NULL,
  `observacion` varchar(100) DEFAULT NULL,
  `tipo` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`clientecontacto_id`),
  KEY `cliente_id` (`cliente_id`),
  CONSTRAINT `clientes_contactos_ibfk_1` FOREIGN KEY (`cliente_id`) REFERENCES `clientes` (`cliente_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `compras`
--

DROP TABLE IF EXISTS `compras`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `compras` (
  `compra_id` int(11) NOT NULL AUTO_INCREMENT,
  `proveedor_id` int(11) NOT NULL,
  `fechapedido` datetime NOT NULL,
  `fechavence` datetime DEFAULT NULL,
  `fechaentrega` datetime DEFAULT NULL,
  `estado` varchar(1) DEFAULT NULL COMMENT 'E=ELABORACION\\nP=SIN INGRESAR\\nI=INGRESO PARCIAL\\nC=ORDEN CERRADA\\nA=ANULADA',
  `orden` varchar(255) DEFAULT NULL,
  `factura` varchar(30) DEFAULT NULL,
  `formapago` varchar(30) DEFAULT NULL,
  `direccion_despacho` varchar(80) DEFAULT NULL,
  `observacion` varchar(200) DEFAULT NULL,
  `descuento` decimal(10,2) DEFAULT NULL,
  `valor_gravado` decimal(10,2) DEFAULT NULL,
  `valor_excluido` decimal(10,2) DEFAULT NULL,
  `userid_confirma` int(11) DEFAULT NULL,
  `anulada` int(11) NOT NULL DEFAULT '0',
  `fecha_anula` datetime DEFAULT NULL,
  `observa_anula` varchar(512) DEFAULT NULL,
  `userid_anula` int(11) DEFAULT NULL,
  `order_type` enum('A','P','S') NOT NULL DEFAULT 'A',
  `certified` int(11) NOT NULL DEFAULT '0',
  `date_certified` datetime DEFAULT NULL,
  PRIMARY KEY (`compra_id`),
  UNIQUE KEY `IDX_efa1364f79a92a1f3679f5328c` (`orden`),
  KEY `FK_d7b3950fea313d15e46e0c59286` (`proveedor_id`),
  CONSTRAINT `FK_d7b3950fea313d15e46e0c59286` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`)
) ENGINE=InnoDB AUTO_INCREMENT=251 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `compras_BEFORE_UPDATE` BEFORE UPDATE ON `compras` FOR EACH ROW BEGIN
	-- SE DESACTIVA GENERACION DE NUMERO DE ORDEN DE ACUERDO A TICKET 20230886 
    
    /*IF NEW.`estado`= 'P' AND OLD.`estado`= 'E' AND NEW.orden is null THEN
        SET @consec = 0;
        SELECT consec_orden_pedido + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.orden = CONCAT('OC',REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_orden_pedido = @consec;
    END IF;*/
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `compras_detalle`
--

DROP TABLE IF EXISTS `compras_detalle`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `compras_detalle` (
  `compra_detalle_id` int(11) NOT NULL AUTO_INCREMENT,
  `compra_id` int(11) NOT NULL,
  `item_id` int(11) NOT NULL,
  `cantidad_pedida` int(11) NOT NULL,
  `cantidad_recibida` int(11) NOT NULL DEFAULT '0',
  `costo` decimal(10,2) NOT NULL DEFAULT '0.00',
  PRIMARY KEY (`compra_detalle_id`),
  KEY `FK_89e165a0311661237ff520a5d4f` (`compra_id`),
  CONSTRAINT `FK_89e165a0311661237ff520a5d4f` FOREIGN KEY (`compra_id`) REFERENCES `compras` (`compra_id`)
) ENGINE=InnoDB AUTO_INCREMENT=383 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `compras_detalle_products`
--

DROP TABLE IF EXISTS `compras_detalle_products`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `compras_detalle_products` (
  `id` varchar(36) NOT NULL,
  `compra_id` int(11) NOT NULL,
  `amount` int(11) NOT NULL,
  `price` decimal(10,2) NOT NULL DEFAULT '0.00',
  `product_id` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `FK_04a6ee4a167f4e57734ca2a5fe8` (`compra_id`),
  KEY `FK_9d4c10f4db86659923aa6a077ac` (`product_id`),
  CONSTRAINT `FK_04a6ee4a167f4e57734ca2a5fe8` FOREIGN KEY (`compra_id`) REFERENCES `compras` (`compra_id`),
  CONSTRAINT `FK_9d4c10f4db86659923aa6a077ac` FOREIGN KEY (`product_id`) REFERENCES `products` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `compras_detalle_services`
--

DROP TABLE IF EXISTS `compras_detalle_services`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `compras_detalle_services` (
  `id` varchar(36) NOT NULL,
  `compra_id` int(11) NOT NULL,
  `amount` int(11) NOT NULL,
  `price` decimal(10,2) NOT NULL DEFAULT '0.00',
  `service_id` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `FK_b059eb2e54e77dde8475ccff0ab` (`compra_id`),
  KEY `FK_86b2717ad675784fe972e27f67b` (`service_id`),
  CONSTRAINT `FK_86b2717ad675784fe972e27f67b` FOREIGN KEY (`service_id`) REFERENCES `services_item` (`id`),
  CONSTRAINT `FK_b059eb2e54e77dde8475ccff0ab` FOREIGN KEY (`compra_id`) REFERENCES `compras` (`compra_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `conceptos_devol`
--

DROP TABLE IF EXISTS `conceptos_devol`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `conceptos_devol` (
  `conceptodevol_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(256) NOT NULL,
  PRIMARY KEY (`conceptodevol_id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `conceptos_notascli`
--

DROP TABLE IF EXISTS `conceptos_notascli`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `conceptos_notascli` (
  `conceptonotacli_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  `tipo` varchar(1) NOT NULL COMMENT 'C=CREDITO\nD=DEBITO',
  PRIMARY KEY (`conceptonotacli_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `conceptos_notasprv`
--

DROP TABLE IF EXISTS `conceptos_notasprv`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `conceptos_notasprv` (
  `conceptonotaprv_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  `tipo` varchar(1) NOT NULL COMMENT 'C=CREDITO\nD=DEBITO',
  PRIMARY KEY (`conceptonotaprv_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `config`
--

DROP TABLE IF EXISTS `config`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `config` (
  `config_id` int(11) NOT NULL AUTO_INCREMENT,
  `logo` varchar(255) DEFAULT NULL,
  `consec_orden_pedido` int(11) NOT NULL DEFAULT '0',
  `consec_mov_ent` int(11) NOT NULL DEFAULT '0',
  `consec_mov_sal` int(11) NOT NULL DEFAULT '0',
  `verimagen` int(11) NOT NULL DEFAULT '0',
  `consec_recepcion` int(11) NOT NULL DEFAULT '0',
  `coditemauto` int(11) DEFAULT '0',
  `consec_coditem` int(11) NOT NULL DEFAULT '0',
  `consec_dc` int(11) NOT NULL DEFAULT '0' COMMENT 'Consecutivo Devolución en compras',
  `consec_fc` int(11) NOT NULL DEFAULT '0',
  `consec_ad` int(11) NOT NULL DEFAULT '0',
  `consec_ac` int(11) NOT NULL DEFAULT '0',
  `consec_ni` int(11) NOT NULL DEFAULT '0',
  `consec_op` int(11) NOT NULL DEFAULT '0',
  `telefono` varchar(20) DEFAULT NULL,
  `celular` varchar(20) DEFAULT NULL,
  `email` varchar(128) DEFAULT NULL,
  `porcreteiva` decimal(10,2) DEFAULT '0.00',
  PRIMARY KEY (`config_id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `departamentos`
--

DROP TABLE IF EXISTS `departamentos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `departamentos` (
  `departamento_id` int(11) NOT NULL AUTO_INCREMENT,
  `pais_id` int(11) DEFAULT NULL,
  `codigo` varchar(2) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  PRIMARY KEY (`departamento_id`),
  KEY `FK_02ca67340ff9b21adc3bf532dfd` (`pais_id`),
  CONSTRAINT `FK_02ca67340ff9b21adc3bf532dfd` FOREIGN KEY (`pais_id`) REFERENCES `paises` (`pais_id`)
) ENGINE=InnoDB AUTO_INCREMENT=34 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `dependencias`
--

DROP TABLE IF EXISTS `dependencias`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `dependencias` (
  `dependencia_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(6) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  `responsable` varchar(256) NOT NULL,
  `localizacion_id` int(11) NOT NULL,
  `cargo_responsable` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`dependencia_id`),
  KEY `FK_3a97b8409fe517d78d17ce88e35` (`localizacion_id`),
  CONSTRAINT `FK_3a97b8409fe517d78d17ce88e35` FOREIGN KEY (`localizacion_id`) REFERENCES `localizacion` (`localizacion_id`)
) ENGINE=InnoDB AUTO_INCREMENT=151 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `detalle_actbaja`
--

DROP TABLE IF EXISTS `detalle_actbaja`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `detalle_actbaja` (
  `detalleactbaja_id` int(11) NOT NULL AUTO_INCREMENT,
  `activo_id` int(11) DEFAULT NULL,
  `actabaja_id` int(11) DEFAULT NULL,
  `descripcion` varchar(512) DEFAULT NULL,
  `marca` varchar(256) DEFAULT NULL,
  `serial` varchar(45) DEFAULT NULL,
  `placa` varchar(45) DEFAULT NULL,
  `observa_baja` varchar(512) DEFAULT NULL,
  `causa_baja` varchar(1) DEFAULT NULL,
  PRIMARY KEY (`detalleactbaja_id`),
  KEY `fk_detactbaja1_idx` (`activo_id`),
  KEY `fk_detactbaja2_idx` (`actabaja_id`),
  CONSTRAINT `fk_detactbaja1_idx` FOREIGN KEY (`activo_id`) REFERENCES `activos` (`activo_id`),
  CONSTRAINT `fk_detactbaja2_idx` FOREIGN KEY (`actabaja_id`) REFERENCES `actas_bajas` (`actabaja_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `detalle_actentfun`
--

DROP TABLE IF EXISTS `detalle_actentfun`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `detalle_actentfun` (
  `detalleactentfun_id` int(11) NOT NULL AUTO_INCREMENT,
  `activo_id` int(11) DEFAULT NULL,
  `actaentregafuncionario_id` int(11) DEFAULT NULL,
  `descripcion` varchar(512) DEFAULT NULL,
  `marca` varchar(256) DEFAULT NULL,
  `serial` varchar(45) DEFAULT NULL,
  `placa` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`detalleactentfun_id`),
  KEY `fk_detactentfun1_idx` (`activo_id`),
  KEY `fk_detactentfun2_idx` (`actaentregafuncionario_id`),
  CONSTRAINT `fk_detactentfun1` FOREIGN KEY (`activo_id`) REFERENCES `activos` (`activo_id`),
  CONSTRAINT `fk_detactentfun2` FOREIGN KEY (`actaentregafuncionario_id`) REFERENCES `actas_entrega_funcionario` (`actaentregafuncionario_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1088 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `devol_compras`
--

DROP TABLE IF EXISTS `devol_compras`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `devol_compras` (
  `devolcompra_id` int(11) NOT NULL AUTO_INCREMENT,
  `proveedor_id` int(11) NOT NULL,
  `fechadevol` datetime NOT NULL,
  `estado` varchar(1) DEFAULT NULL COMMENT '0=NO CONFIRMADA\n1= CONFIRMADA',
  `nrodcto` varchar(255) DEFAULT NULL,
  `observacion` varchar(200) DEFAULT NULL,
  `descuento` decimal(10,2) DEFAULT NULL,
  `iva` decimal(10,2) DEFAULT NULL,
  `valor_gravado` decimal(10,2) DEFAULT NULL,
  `valor_excluido` decimal(10,2) DEFAULT NULL,
  `userid_confirma` int(11) DEFAULT NULL,
  `conceptodevol_id` int(11) DEFAULT NULL,
  `saldo` decimal(10,2) NOT NULL DEFAULT '0.00',
  `factura` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`devolcompra_id`),
  KEY `proveedor_id` (`proveedor_id`),
  KEY `conceptodevol_id` (`conceptodevol_id`),
  CONSTRAINT `concdevol_ibfk_1` FOREIGN KEY (`conceptodevol_id`) REFERENCES `conceptos_devol` (`conceptodevol_id`),
  CONSTRAINT `devolcompras_ibfk_1` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `devol_compras_BEFORE_UPDATE` BEFORE UPDATE ON `devol_compras` FOR EACH ROW BEGIN

	IF NEW.`estado`= '1' AND OLD.`estado`= '0' THEN
        SET @consec = 0;
     
		SET @val=0;
		SELECT count(*) INTO @val FROM v_devolsinstock WHERE v_devolsinstock.devolcompra_id = NEW.devolcompra_id;
		IF @val=0 THEN
			CALL confirmar_devol_out(NEW.`devolcompra_id`);
			SELECT consec_dc + 1  INTO @consec FROM `config` LIMIT 1;
			SET NEW.nrodcto = CONCAT('DC',REPEAT('0',6-LENGTH(CAST(@consec AS CHAR))),@consec);
			UPDATE config set consec_dc = @consec;
		ELSE
			SIGNAL SQLSTATE '45000'
			SET MESSAGE_TEXT= 'NO Confirmado. Verifique Stock de los Productos';
		END IF;

    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `devolcompras_detalle`
--

DROP TABLE IF EXISTS `devolcompras_detalle`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `devolcompras_detalle` (
  `devolcompra_detalle_id` int(11) NOT NULL AUTO_INCREMENT,
  `devolcompra_id` int(11) NOT NULL,
  `producto_id` int(11) NOT NULL,
  `cantidad` int(11) NOT NULL,
  `costo` decimal(10,2) DEFAULT NULL,
  `descuento` decimal(10,2) DEFAULT NULL,
  `impuesto` decimal(10,2) DEFAULT NULL,
  `valor_excluido` decimal(10,2) DEFAULT NULL,
  `valor_gravado` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`devolcompra_detalle_id`),
  UNIQUE KEY `devolcompras_detalle_producto_id_compra_id_unique` (`devolcompra_detalle_id`,`producto_id`),
  KEY `producto_id` (`producto_id`),
  KEY `devolcompras_detalle_ibfk_1` (`devolcompra_id`),
  CONSTRAINT `devolcompras_detalle_ibfk_1` FOREIGN KEY (`devolcompra_id`) REFERENCES `devol_compras` (`devolcompra_id`) ON UPDATE CASCADE,
  CONSTRAINT `devolcompras_detalle_ibfk_2` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=54 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `documentos_contables`
--

DROP TABLE IF EXISTS `documentos_contables`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `documentos_contables` (
  `documentocontable_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(2) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  `consec` int(11) NOT NULL DEFAULT '0',
  PRIMARY KEY (`documentocontable_id`),
  UNIQUE KEY `codigo` (`codigo`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `estado_orden`
--

DROP TABLE IF EXISTS `estado_orden`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `estado_orden` (
  `estado` varchar(1) NOT NULL,
  `orden` int(11) DEFAULT NULL,
  PRIMARY KEY (`estado`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `factura_compra`
--

DROP TABLE IF EXISTS `factura_compra`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `factura_compra` (
  `facturacompra_id` int(11) NOT NULL AUTO_INCREMENT,
  `nrodocumento` varchar(20) DEFAULT NULL,
  `proveedor_id` int(11) NOT NULL,
  `nrofactura` varchar(20) DEFAULT NULL,
  `fechafactura` datetime NOT NULL,
  `fechavence` datetime DEFAULT NULL,
  `cufe` varchar(45) DEFAULT NULL,
  `vr_excluido` decimal(18,2) NOT NULL DEFAULT '0.00',
  `vr_gravado` decimal(18,2) NOT NULL DEFAULT '0.00',
  `iva` decimal(18,2) NOT NULL DEFAULT '0.00',
  `vr_descuento` decimal(18,2) NOT NULL DEFAULT '0.00',
  `vr_excluido_otros` decimal(18,2) NOT NULL DEFAULT '0.00',
  `vr_gravado_otros` decimal(18,2) NOT NULL DEFAULT '0.00',
  `iva_otros` decimal(18,2) NOT NULL DEFAULT '0.00',
  `retefuente` decimal(18,2) NOT NULL DEFAULT '0.00',
  `reteiva` decimal(18,2) NOT NULL DEFAULT '0.00',
  `reteica` decimal(18,2) NOT NULL DEFAULT '0.00',
  `userid_confirma` int(11) DEFAULT NULL,
  `observa_otros` varchar(256) DEFAULT NULL,
  `nota_credito_otros` int(11) DEFAULT '0',
  `formapago` varchar(1) NOT NULL COMMENT 'T=CONTADO\nR=CREDITO',
  `ctaotros_id` int(11) DEFAULT NULL,
  `vr_pagar` decimal(18,2) NOT NULL DEFAULT '0.00',
  `saldo` decimal(18,2) NOT NULL DEFAULT '0.00',
  `subtotal` decimal(18,2) NOT NULL DEFAULT '0.00',
  `retefuente_ss` decimal(18,2) NOT NULL DEFAULT '0.00',
  `reteica_ss` decimal(18,2) NOT NULL DEFAULT '0.00',
  `reteiva_ss` decimal(18,2) NOT NULL DEFAULT '0.00',
  `anulada` int(11) DEFAULT '0',
  `generaplano` int(11) DEFAULT '0',
  PRIMARY KEY (`facturacompra_id`),
  KEY `fk_proveedor_idx` (`proveedor_id`),
  CONSTRAINT `fk_proveedor` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`)
) ENGINE=InnoDB AUTO_INCREMENT=119 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `factura_compra_BEFORE_INSERT` BEFORE INSERT ON `factura_compra` FOR EACH ROW BEGIN
		SET @consec = 0;
		SELECT consec_fc + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.nrodocumento = CONCAT('FC',REPEAT('0',6-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_fc = @consec;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`sistemas`@`%`*/ /*!50003 TRIGGER `factura_compra_BEFORE_UPDATE` BEFORE UPDATE ON `factura_compra` FOR EACH ROW BEGIN
	IF NEW.`anulada`= 1 AND OLD.`anulada`= 0 THEN
		DELETE FROM factura_recepcion WHERE facturacompra_id= NEW.facturacompra_id;
    END IF;
    
    IF NEW.`generaplano`= 1 AND OLD.`generaplano`= 0 THEN
		insert into interfaz_siigo 
         SELECT
			0,
			`facturacompra_id`,
            'F',
			'N' AS `tipo_comprobante`,
			'042' AS `codigo_comprobante`,
			concat(repeat('0',11-length(nrofactura)),nrofactura) as `nro_documento`,
			concat(REPEAT('0',5-LENGTH(CAST( @n := @n + 1 AS CHAR))),@n) as `secuencia`,
			concat(repeat('0',13-length(identificacion)),identificacion)  as `nit`,
			'000' as `sucursal`,
			concat(codigo_cuenta,repeat('0',10-length(codigo_cuenta))) as `codigo_cuenta_contable`,
			'0000000000000' as `codigo_producto`,
			DATE_FORMAT(CURDATE(),'%Y%m%d') as `fecha_documento`,
			if(substring(codigo_cuenta,1,1)='1' or substring(codigo_cuenta,1,6)='5', '1432','0000') as `centro_de_costo`,
			'000' as `sub_centro_de_costo`,
			concat(descripcion_cuenta,repeat(' ',50-length(descripcion_cuenta))) as `descripcion`,
			if(tipo='D', 'D', 'C') AS `registro`,
			concat( repeat('0',15-length(concat( cast(floor(valor) as char), substring(cast(valor-floor(valor) as char),3,2)))), concat( cast(floor(valor) as char), substring(cast(valor-floor(valor) as char),3,2))) as `valor_movimiento`,
			if(substring(codigo_cuenta,1,6)='243608', concat( repeat('0',15-length(concat( cast(floor(subtotal) as char), substring(cast(subtotal-floor(subtotal) as char),3,2)))), concat( cast(floor(subtotal) as char), substring(cast(subtotal-floor(subtotal) as char),3,2))) ,'000000000000000') as `base_retencion`,
			'0001' as `codigo_vendedor`,
			'0001' as `codigo_ciudad`,
			'001' as `codigo_zona`,
			'0001' as `codigo_bodega`,
			'000' as `codigo_ubicacion`,
			'000000000000000' as `cantidad`,
			 if(substring(codigo_cuenta,1,4)='2490','N','0') AS `tipo_comprobante_cruce`,
			 if(substring(codigo_cuenta,1,4)='2490','042',REPEAT('0',3)) AS `codigo_comprobante_cruce`,
			 if(substring(codigo_cuenta,1,4)='2490',concat(repeat('0',11-length(nrofactura)),nrofactura),REPEAT('0',11)) AS `nro_dcto_cruce`,
			 if(substring(codigo_cuenta,1,4)='2490',concat(REPEAT('0',3-LENGTH(CAST( @n := @n AS CHAR))),@n),'000') AS `secuencia_dcto_cruce`,
			DATE_FORMAT(CURDATE(),'%Y%m%d') AS `fecha_vencimiento`,
			'0000' AS `codigo_forma_de_pago`,
			'00' AS `codigo_banco` 
		FROM sirisinv.v_causacion_group,(SELECT @n := 0) m 

		WHERE facturacompra_id=NEW.facturacompra_id;
        
        update activos set causacion=1 where recepcion_id in(
		SELECT recepcion_id FROM sirisinv.factura_recepcion where facturacompra_id=NEW.facturacompra_id);

    END IF;
    
	IF NEW.`generaplano`= 0 AND OLD.`generaplano`= 1 THEN
		DELETE FROM interfaz_siigo where transaccion_id = NEW.facturacompra_id and tipo='F';
        update activos set causacion=0 where recepcion_id in(
		SELECT recepcion_id FROM sirisinv.factura_recepcion where facturacompra_id=NEW.facturacompra_id);
	END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `factura_recepcion`
--

DROP TABLE IF EXISTS `factura_recepcion`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `factura_recepcion` (
  `facturarecepcion_id` int(11) NOT NULL AUTO_INCREMENT,
  `facturacompra_id` int(11) NOT NULL,
  `recepcion_id` int(11) NOT NULL,
  PRIMARY KEY (`facturarecepcion_id`),
  KEY `fk_factura_idx` (`facturacompra_id`),
  KEY `fk_recepcion_idx` (`recepcion_id`),
  CONSTRAINT `fk_factura` FOREIGN KEY (`facturacompra_id`) REFERENCES `factura_compra` (`facturacompra_id`) ON DELETE CASCADE,
  CONSTRAINT `fk_recepcion_fac` FOREIGN KEY (`recepcion_id`) REFERENCES `recepciones` (`recepcion_id`)
) ENGINE=InnoDB AUTO_INCREMENT=121 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `financiero`
--

DROP TABLE IF EXISTS `financiero`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `financiero` (
  `financiero_id` int(11) NOT NULL AUTO_INCREMENT,
  `tercero_id` int(11) NOT NULL,
  `fecha` datetime NOT NULL,
  `dcto` varchar(45) NOT NULL,
  `secuencia` varchar(3) NOT NULL,
  `cuenta` varchar(8) NOT NULL,
  `tipo` varchar(1) NOT NULL,
  `descripcion` varchar(256) NOT NULL,
  `valor` decimal(18,2) NOT NULL,
  `vence` datetime NOT NULL,
  `dcto_cruce` varchar(45) NOT NULL,
  `secuencia_cruce` varchar(3) NOT NULL,
  PRIMARY KEY (`financiero_id`),
  KEY `fk_fintercero_idx` (`tercero_id`),
  KEY `uq_keyfin` (`tercero_id`,`dcto`,`secuencia`),
  CONSTRAINT `fk_fintercero` FOREIGN KEY (`tercero_id`) REFERENCES `terceros` (`tercero_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `genericos`
--

DROP TABLE IF EXISTS `genericos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `genericos` (
  `generico_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  PRIMARY KEY (`generico_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `impuestos`
--

DROP TABLE IF EXISTS `impuestos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `impuestos` (
  `impuesto_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(2) NOT NULL,
  `descripcion` varchar(80) NOT NULL,
  `porcentaje` decimal(10,6) NOT NULL,
  PRIMARY KEY (`impuesto_id`),
  UNIQUE KEY `idxunique_codigo_porcentaje` (`codigo`,`porcentaje`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `interfaz_siigo`
--

DROP TABLE IF EXISTS `interfaz_siigo`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `interfaz_siigo` (
  `interfaz_siigo_id` int(11) NOT NULL AUTO_INCREMENT,
  `transaccion_id` int(11) NOT NULL,
  `tipo` varchar(1) NOT NULL COMMENT 'F=FACTURA, B=BAJA, D=DEPRECIACION',
  `tipo_comprobante` varchar(1) NOT NULL,
  `codigo_comprobante` varchar(3) NOT NULL,
  `nro_documento` varchar(11) NOT NULL,
  `secuencia` varchar(5) NOT NULL,
  `nit` varchar(13) NOT NULL,
  `sucursal` varchar(3) NOT NULL,
  `codigo_cuenta_contable` varchar(10) NOT NULL,
  `codigo_producto` varchar(13) NOT NULL,
  `fecha_documento` varchar(50) NOT NULL,
  `centro_de_costo` varchar(4) NOT NULL,
  `sub_centro_de_costo` varchar(3) NOT NULL,
  `descripcion` varchar(50) NOT NULL,
  `registro` varchar(1) NOT NULL,
  `valor_movimiento` varchar(15) NOT NULL,
  `base_retencion` varchar(15) NOT NULL,
  `codigo_vendedor` varchar(4) NOT NULL,
  `codigo_ciudad` varchar(4) NOT NULL,
  `codigo_zona` varchar(3) NOT NULL,
  `codigo_bodega` varchar(4) NOT NULL,
  `codigo_ubicacion` varchar(3) NOT NULL,
  `cantidad` varchar(15) NOT NULL,
  `tipo_comprobante_cruce` varchar(1) NOT NULL,
  `codigo_comprobante_cruce` varchar(3) NOT NULL,
  `nro_dcto_cruce` varchar(11) NOT NULL,
  `secuencia_dcto_cruce` varchar(3) NOT NULL,
  `fecha_vencimiento` varchar(50) NOT NULL,
  `codigo_forma_de_pago` varchar(4) NOT NULL,
  `codigo_banco` varchar(2) NOT NULL,
  PRIMARY KEY (`interfaz_siigo_id`)
) ENGINE=InnoDB AUTO_INCREMENT=378 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `inventory_documents`
--

DROP TABLE IF EXISTS `inventory_documents`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `inventory_documents` (
  `id` varchar(36) NOT NULL,
  `document_number` varchar(5) DEFAULT NULL,
  `dateDocument` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `dependencia_id` int(11) DEFAULT NULL,
  `responsable_id` int(11) DEFAULT NULL,
  `proveedor_id` int(11) DEFAULT NULL,
  `type_movement_id` varchar(255) NOT NULL,
  `signed` tinyint(4) NOT NULL DEFAULT '0',
  `digitized_signature` blob,
  PRIMARY KEY (`id`),
  UNIQUE KEY `IDX_4695edb3c3ac43ebe9eeaae2f4` (`document_number`),
  KEY `FK_4031be9a1318508e9c7f23ed65f` (`dependencia_id`),
  KEY `FK_02d09f0a285f83416034c54fa61` (`responsable_id`),
  KEY `FK_5336c9b2645a4fbce7f53b31831` (`proveedor_id`),
  KEY `FK_cc8d0782bba3313bbc84e531b67` (`type_movement_id`),
  CONSTRAINT `FK_02d09f0a285f83416034c54fa61` FOREIGN KEY (`responsable_id`) REFERENCES `responsables` (`responsable_id`),
  CONSTRAINT `FK_4031be9a1318508e9c7f23ed65f` FOREIGN KEY (`dependencia_id`) REFERENCES `dependencias` (`dependencia_id`),
  CONSTRAINT `FK_5336c9b2645a4fbce7f53b31831` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`),
  CONSTRAINT `FK_cc8d0782bba3313bbc84e531b67` FOREIGN KEY (`type_movement_id`) REFERENCES `type_movement` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `inventory_movements`
--

DROP TABLE IF EXISTS `inventory_movements`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `inventory_movements` (
  `id` varchar(36) NOT NULL,
  `amountUnit` int(11) NOT NULL DEFAULT '0',
  `amountFraction` int(11) NOT NULL DEFAULT '0',
  `product_id` varchar(255) NOT NULL,
  `inventory_document_id` varchar(255) NOT NULL,
  `cost_price` decimal(10,2) NOT NULL DEFAULT '0.00',
  PRIMARY KEY (`id`),
  KEY `FK_5c3bec1682252c36fa161587738` (`product_id`),
  KEY `FK_752e3f94583c2b7ae80a7a494b4` (`inventory_document_id`),
  CONSTRAINT `FK_5c3bec1682252c36fa161587738` FOREIGN KEY (`product_id`) REFERENCES `products` (`id`),
  CONSTRAINT `FK_752e3f94583c2b7ae80a7a494b4` FOREIGN KEY (`inventory_document_id`) REFERENCES `inventory_documents` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `items`
--

DROP TABLE IF EXISTS `items`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `items` (
  `item_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(15) DEFAULT NULL,
  `descripcion` varchar(40) NOT NULL,
  `descripcion_adicional` varchar(40) DEFAULT NULL,
  `tipo_item` varchar(1) NOT NULL COMMENT 'A=Activo\nC=Consumo',
  `marca_id` int(11) NOT NULL,
  `subcategoria_id` int(11) NOT NULL,
  `userid_create` int(11) NOT NULL,
  `userid_update` int(11) DEFAULT NULL,
  `cantidad_stock` int(11) DEFAULT '0',
  `stockmin` int(11) DEFAULT NULL,
  `stockmax` int(11) DEFAULT NULL,
  `costo` decimal(10,2) DEFAULT NULL,
  `bloqueo` tinyint(1) DEFAULT '0',
  `fecha_ultima_compra` datetime DEFAULT NULL,
  `fecha_creacion` datetime NOT NULL,
  `costo_ultimo` decimal(10,2) DEFAULT NULL,
  `proveedor_id` int(11) DEFAULT NULL,
  `activo_catalogo_id` int(11) DEFAULT NULL,
  `gasto_catalogo_id` int(11) DEFAULT NULL,
  `valor_residual` int(11) DEFAULT NULL,
  `barcode` varchar(80) DEFAULT NULL,
  PRIMARY KEY (`item_id`),
  UNIQUE KEY `codigo_interno` (`codigo`),
  KEY `marca_id` (`marca_id`),
  KEY `subcategoria_id` (`subcategoria_id`),
  KEY `items_ibfk_3_idx` (`activo_catalogo_id`),
  KEY `items_ibfk_3_idx1` (`gasto_catalogo_id`),
  CONSTRAINT `items_ibfk_1` FOREIGN KEY (`marca_id`) REFERENCES `marcas` (`marca_id`),
  CONSTRAINT `items_ibfk_2` FOREIGN KEY (`subcategoria_id`) REFERENCES `subcategorias` (`subcategoria_id`),
  CONSTRAINT `items_ibfk_3` FOREIGN KEY (`activo_catalogo_id`) REFERENCES `catalogo_contable` (`catalogo_id`),
  CONSTRAINT `items_ibfk_4` FOREIGN KEY (`gasto_catalogo_id`) REFERENCES `catalogo_contable` (`catalogo_id`)
) ENGINE=InnoDB AUTO_INCREMENT=729 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `productos_BEFORE_INSERT` BEFORE INSERT ON `items` FOR EACH ROW BEGIN
	SET @auto = 0;
    SELECT coditemauto into @auto  FROM `config` LIMIT 1;
    IF (@auto=1) THEN
		SET @consec = 0;
		SELECT consec_coditem + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.codigo = CONCAT(REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_coditem = @consec;
    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `jobs_title`
--

DROP TABLE IF EXISTS `jobs_title`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `jobs_title` (
  `description` varchar(255) NOT NULL,
  `id` varchar(36) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `IDX_e4687dcd2bbac9a22a8e0a714e` (`description`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `localizacion`
--

DROP TABLE IF EXISTS `localizacion`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `localizacion` (
  `localizacion_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(3) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  `direccion` varchar(256) DEFAULT NULL,
  `municipio_id` int(11) DEFAULT NULL,
  `lat` varchar(128) DEFAULT NULL,
  `lng` varchar(128) DEFAULT NULL,
  PRIMARY KEY (`localizacion_id`),
  KEY `FK_1d2a5647efc235e79bed15adac9` (`municipio_id`),
  CONSTRAINT `FK_1d2a5647efc235e79bed15adac9` FOREIGN KEY (`municipio_id`) REFERENCES `municipios` (`municipio_id`)
) ENGINE=InnoDB AUTO_INCREMENT=116 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `marcas`
--

DROP TABLE IF EXISTS `marcas`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `marcas` (
  `marca_id` int(11) NOT NULL AUTO_INCREMENT,
  `nombre` varchar(80) NOT NULL,
  PRIMARY KEY (`marca_id`),
  UNIQUE KEY `nombre_UNIQUE` (`nombre`)
) ENGINE=InnoDB AUTO_INCREMENT=201 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `mediciones`
--

DROP TABLE IF EXISTS `mediciones`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `mediciones` (
  `medicion_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(256) NOT NULL,
  PRIMARY KEY (`medicion_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `menus`
--

DROP TABLE IF EXISTS `menus`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `menus` (
  `menu_id` int(11) NOT NULL AUTO_INCREMENT,
  `orden` int(11) NOT NULL,
  `titulo` varchar(80) NOT NULL,
  `type` varchar(80) NOT NULL,
  `icono` varchar(80) NOT NULL,
  PRIMARY KEY (`menu_id`)
) ENGINE=InnoDB AUTO_INCREMENT=9 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `modalidad_factura`
--

DROP TABLE IF EXISTS `modalidad_factura`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `modalidad_factura` (
  `modalidadfactura_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  PRIMARY KEY (`modalidadfactura_id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `monedas`
--

DROP TABLE IF EXISTS `monedas`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `monedas` (
  `moneda_id` int(11) NOT NULL AUTO_INCREMENT,
  `simbolo` varchar(45) NOT NULL,
  `nombre` varchar(45) NOT NULL,
  PRIMARY KEY (`moneda_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `movimientos_inventario`
--

DROP TABLE IF EXISTS `movimientos_inventario`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `movimientos_inventario` (
  `movinventario_id` int(11) NOT NULL AUTO_INCREMENT,
  `tipoajuste_id` int(11) NOT NULL,
  `tercero_id` int(11) NOT NULL,
  `user_id` int(11) NOT NULL,
  `numero` varchar(20) DEFAULT NULL,
  `fechahora` datetime NOT NULL,
  `observacion` varchar(150) DEFAULT NULL,
  `estado` varchar(1) DEFAULT NULL,
  PRIMARY KEY (`movinventario_id`),
  KEY `tipoajuste_id` (`tipoajuste_id`),
  KEY `movimientos_inventario_ibfk_2_idx` (`tercero_id`),
  CONSTRAINT `movimientos_inventario_ibfk_1` FOREIGN KEY (`tipoajuste_id`) REFERENCES `tipos_ajuste` (`tipoajuste_id`),
  CONSTRAINT `movimientos_inventario_ibfk_2` FOREIGN KEY (`tercero_id`) REFERENCES `terceros` (`tercero_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `movimientos_inventario_BEFORE_UPDATE` BEFORE UPDATE ON `movimientos_inventario` FOR EACH ROW BEGIN
	IF NEW.`estado`= '1' AND OLD.`estado`= '0' THEN
		SET @mvto = 0;
        SET @consec = 0;
        SELECT mvto  INTO @mvto FROM `tipos_ajuste` WHERE tipoajuste_id = NEW.`tipoajuste_id`;
		IF @mvto= 1 THEN
			CALL confirmar_ajuste_in(NEW.`movinventario_id`);
			SELECT consec_mov_ent + 1  INTO @consec FROM `config` LIMIT 1;
            SET NEW.numero = CONCAT('AE',REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
            UPDATE config set consec_mov_ent = @consec;
        ELSE
			SET @val=0;
            SELECT count(*) INTO @val FROM v_salidasinstock WHERE v_salidasinstock.movinventario_id = NEW.movinventario_id;
            IF @val=0 THEN
				CALL confirmar_ajuste_out(NEW.`movinventario_id`);
                SELECT consec_mov_sal + 1  INTO @consec FROM `config` LIMIT 1;
                SET NEW.numero = CONCAT('AS',REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
				UPDATE config set consec_mov_sal = @consec;
			ELSE
				SIGNAL SQLSTATE '45000'
				SET MESSAGE_TEXT= 'NO Confirmado. Verifique Stock de los Productos';
			END IF;
        END IF;
    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `movinventario_detalle`
--

DROP TABLE IF EXISTS `movinventario_detalle`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `movinventario_detalle` (
  `movinventariodetalle_id` int(11) NOT NULL AUTO_INCREMENT,
  `movinventario_id` int(11) NOT NULL,
  `activo_id` int(11) NOT NULL,
  `cantidad` int(11) NOT NULL,
  `costo_adquiere` decimal(10,2) NOT NULL,
  `depreciacion` decimal(10,2) DEFAULT NULL,
  `vr_libros` decimal(10,2) DEFAULT NULL,
  `observacion` varchar(512) DEFAULT NULL,
  PRIMARY KEY (`movinventariodetalle_id`),
  UNIQUE KEY `movinventario_detalle_movinventario_id_producto_id_unique` (`movinventario_id`,`activo_id`),
  KEY `movinventario_detalle_ibfk_2_idx` (`activo_id`),
  CONSTRAINT `movinventario_detalle_ibfk_1` FOREIGN KEY (`movinventario_id`) REFERENCES `movimientos_inventario` (`movinventario_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `movinventario_detalle_ibfk_2` FOREIGN KEY (`activo_id`) REFERENCES `activos` (`activo_id`) ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `municipios`
--

DROP TABLE IF EXISTS `municipios`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `municipios` (
  `municipio_id` int(11) NOT NULL AUTO_INCREMENT,
  `departamento_id` int(11) DEFAULT NULL,
  `codigo` varchar(5) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  PRIMARY KEY (`municipio_id`),
  KEY `FK_cfc60523878116f625631f0e251` (`departamento_id`),
  CONSTRAINT `FK_cfc60523878116f625631f0e251` FOREIGN KEY (`departamento_id`) REFERENCES `departamentos` (`departamento_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1155 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `notasprv`
--

DROP TABLE IF EXISTS `notasprv`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `notasprv` (
  `notasprv_id` int(11) NOT NULL AUTO_INCREMENT,
  `nrodcto` varchar(45) DEFAULT NULL,
  `fechanota` datetime NOT NULL,
  `fechavence` datetime DEFAULT NULL,
  `proveedor_id` int(11) NOT NULL,
  `tipo` varchar(1) NOT NULL COMMENT 'D=Debito\nC=Credito',
  `cufe` varchar(45) DEFAULT NULL,
  `vr_excluido` decimal(18,2) NOT NULL DEFAULT '0.00',
  `vr_gravado` decimal(18,2) NOT NULL DEFAULT '0.00',
  `iva` decimal(18,2) NOT NULL DEFAULT '0.00',
  `retefuente` decimal(18,2) NOT NULL DEFAULT '0.00',
  `reteiva` decimal(18,2) NOT NULL DEFAULT '0.00',
  `reteica` decimal(18,2) NOT NULL DEFAULT '0.00',
  `vr_total` decimal(18,2) NOT NULL DEFAULT '0.00',
  `saldo` decimal(18,2) NOT NULL DEFAULT '0.00',
  `userid_confirma` int(11) DEFAULT NULL,
  `observa` varchar(256) DEFAULT NULL,
  `conceptonotaprv_id` int(11) NOT NULL,
  PRIMARY KEY (`notasprv_id`),
  KEY `fk_notaprv_idx` (`proveedor_id`),
  KEY `fk_notaconcepto_idx` (`conceptonotaprv_id`),
  CONSTRAINT `fk_notaconceptoprv` FOREIGN KEY (`conceptonotaprv_id`) REFERENCES `conceptos_notasprv` (`conceptonotaprv_id`),
  CONSTRAINT `fk_notaprv` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `notasprv_BEFORE_INSERT` BEFORE INSERT ON `notasprv` FOR EACH ROW BEGIN
	SET @consec = 0;
    IF (NEW.tipo='D') THEN
		SELECT consec_ad + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.nrodcto = CONCAT('AD',REPEAT('0',6-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_ad = @consec;
    ELSE
		SELECT consec_ac + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.nrodcto = CONCAT('AC',REPEAT('0',6-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_ac = @consec;
    END IF;
	
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `pagos_prv`
--

DROP TABLE IF EXISTS `pagos_prv`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `pagos_prv` (
  `pagoprv_id` int(11) NOT NULL AUTO_INCREMENT,
  `proveedor_id` int(11) NOT NULL,
  `fecha` datetime NOT NULL,
  `tipo` varchar(1) NOT NULL COMMENT 'P=PAGO\nC=CRUCE',
  `nrodcto` varchar(20) DEFAULT NULL,
  `valor` decimal(10,2) NOT NULL DEFAULT '0.00',
  `userid_confirma` int(11) DEFAULT NULL,
  `observacion` varchar(200) DEFAULT NULL,
  `forma_pago` varchar(1) DEFAULT NULL COMMENT 'E=Efectivo\nC=Cheque\nT=Transferencia',
  `cheque` varchar(45) DEFAULT NULL,
  `ach` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`pagoprv_id`),
  KEY `fk_pagoprv_idx` (`proveedor_id`),
  CONSTRAINT `fk_pagoprv` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pagos_prv_BEFORE_INSERT` BEFORE INSERT ON `pagos_prv` FOR EACH ROW BEGIN
		SET @consec = 0;
        if new.tipo = 'P' then
			SELECT consec_ce + 1  INTO @consec FROM `config` LIMIT 1;
			SET NEW.nrodcto = CONCAT('CE',REPEAT('0',6-LENGTH(CAST(@consec AS CHAR))),@consec);
			UPDATE config set consec_ce = @consec;
		else
			SELECT consec_ni + 1  INTO @consec FROM `config` LIMIT 1;
			SET NEW.nrodcto = CONCAT('NI',REPEAT('0',6-LENGTH(CAST(@consec AS CHAR))),@consec);
			UPDATE config set consec_ni = @consec;
        end if;
		
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `pagosprv_transac`
--

DROP TABLE IF EXISTS `pagosprv_transac`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `pagosprv_transac` (
  `pagoprvtransac_id` int(11) NOT NULL AUTO_INCREMENT,
  `pagoprv_id` int(11) NOT NULL,
  `tipo_dcto` varchar(2) NOT NULL COMMENT 'FC=Factura de Compra\nDC=Devolución a Proveedores\nAD=Nota Débito Proveedor\nAC=Nota Crédito Proveedor',
  `transac_id` int(11) NOT NULL,
  `subtotal` decimal(10,2) NOT NULL,
  `descuento` decimal(10,2) NOT NULL,
  `vr_pago` decimal(10,2) NOT NULL,
  PRIMARY KEY (`pagoprvtransac_id`),
  KEY `fk_pagotransac_idx` (`pagoprv_id`),
  CONSTRAINT `fk_pagotransac` FOREIGN KEY (`pagoprv_id`) REFERENCES `pagos_prv` (`pagoprv_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pagosprv_transac_AFTER_INSERT` AFTER INSERT ON `pagosprv_transac` FOR EACH ROW BEGIN
	IF NEW.tipo_dcto='FC' THEN
		UPDATE factura_compra set saldo = saldo - NEW.subtotal WHERE facturacompra_id = NEW.transac_id;
    END IF;
    IF NEW.tipo_dcto='DC' THEN
		UPDATE devol_compras set saldo = saldo - NEW.subtotal WHERE devolcompra_id = NEW.transac_id;
    END IF;
    IF NEW.tipo_dcto='AD' OR  NEW.tipo_dcto='AC' THEN
		UPDATE notasprv set saldo = saldo - NEW.subtotal WHERE notasprv_id = NEW.transac_id;
    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `paises`
--

DROP TABLE IF EXISTS `paises`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `paises` (
  `pais_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(255) NOT NULL,
  `nombre` varchar(255) NOT NULL,
  PRIMARY KEY (`pais_id`)
) ENGINE=InnoDB AUTO_INCREMENT=247 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `pedidos`
--

DROP TABLE IF EXISTS `pedidos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `pedidos` (
  `pedido_id` int(11) NOT NULL AUTO_INCREMENT,
  `orden` varchar(45) DEFAULT NULL,
  `cliente_id` int(11) NOT NULL,
  `user_id` int(11) NOT NULL,
  `vendedor_id` int(11) DEFAULT NULL,
  `fecha` datetime NOT NULL,
  `estado` varchar(1) DEFAULT NULL COMMENT 'E=Elaboración\nA=Anulado\nF=Facturado\nP=Pendiente\nV=Verificacion\nZ=Finalizado',
  `observacion` varchar(255) DEFAULT NULL,
  `subtotal` decimal(10,2) DEFAULT '0.00',
  `descuento` decimal(10,2) DEFAULT '0.00',
  `valor_gravado` decimal(10,2) DEFAULT '0.00',
  `valor_excluido` decimal(10,2) DEFAULT '0.00',
  `iva` decimal(10,2) DEFAULT '0.00',
  `direccion_despacho` varchar(80) DEFAULT NULL,
  `fecha_finaliza` datetime DEFAULT NULL,
  `user_verifica` int(11) DEFAULT NULL,
  PRIMARY KEY (`pedido_id`),
  KEY `cliente_id` (`cliente_id`),
  KEY `user_id` (`user_id`),
  CONSTRAINT `pedidos_ibfk_2` FOREIGN KEY (`cliente_id`) REFERENCES `clientes` (`cliente_id`),
  CONSTRAINT `pedidos_ibfk_3` FOREIGN KEY (`user_id`) REFERENCES `users` (`user_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pedidos_BEFORE_INSERT` BEFORE INSERT ON `pedidos` FOR EACH ROW BEGIN
	SET @consec = 0;
   
		SELECT consec_op + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.orden = CONCAT('OP',REPEAT('0',8-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_op = @consec;

END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `pedidos_detalle`
--

DROP TABLE IF EXISTS `pedidos_detalle`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `pedidos_detalle` (
  `pedidodetalle_id` int(11) NOT NULL AUTO_INCREMENT,
  `pedido_id` int(11) NOT NULL,
  `producto_id` int(11) NOT NULL,
  `impuesto_id` int(11) NOT NULL,
  `tipoprecio_id` int(11) NOT NULL,
  `cantidad` int(11) NOT NULL,
  `cantidad_fraccion` int(11) NOT NULL,
  `precio_unidad` decimal(10,2) NOT NULL,
  `precio_fraccion` decimal(10,2) NOT NULL,
  `descuento_unidad` decimal(10,2) NOT NULL DEFAULT '0.00',
  `descuento_fraccion` decimal(10,2) NOT NULL DEFAULT '0.00',
  `valor_gravado_unidad` decimal(10,2) NOT NULL DEFAULT '0.00',
  `valor_excluido_unidad` decimal(10,2) NOT NULL DEFAULT '0.00',
  `valor_gravado_fraccion` decimal(10,2) NOT NULL DEFAULT '0.00',
  `valor_excluido_fraccion` decimal(10,2) NOT NULL DEFAULT '0.00',
  `iva` decimal(10,2) NOT NULL,
  `factor_precio` decimal(10,2) NOT NULL,
  `serial` varchar(50) DEFAULT NULL,
  `costo` decimal(10,2) NOT NULL DEFAULT '0.00',
  `costo_fraccion` decimal(10,2) NOT NULL DEFAULT '0.00',
  `precio_unidad_antes_iva` decimal(10,2) NOT NULL DEFAULT '0.00',
  `precio_fraccion_antes_iva` decimal(10,2) NOT NULL DEFAULT '0.00',
  `total_gravado` decimal(10,2) DEFAULT '0.00',
  `total_excluido` decimal(10,2) GENERATED ALWAYS AS (((`valor_excluido_unidad` * `cantidad`) + (`valor_excluido_fraccion` * `cantidad_fraccion`))) VIRTUAL,
  `total_iva` decimal(10,2) GENERATED ALWAYS AS ((`total_gravado` * (`iva` / 100))) VIRTUAL,
  `fechahora` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `cantidad_verifica` int(11) NOT NULL DEFAULT '0',
  `cantidad_fraccion_verifica` int(11) NOT NULL DEFAULT '0',
  `cantidad_noenviada` int(11) NOT NULL DEFAULT '0',
  `cantidad_fraccion_noenviada` int(11) NOT NULL DEFAULT '0',
  PRIMARY KEY (`pedidodetalle_id`),
  UNIQUE KEY `pedidos_detalle_producto_id_pedido_id_unique` (`pedido_id`,`producto_id`),
  KEY `producto_id` (`producto_id`),
  CONSTRAINT `pedidos_detalle_ibfk_1` FOREIGN KEY (`pedido_id`) REFERENCES `pedidos` (`pedido_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `pedidos_detalle_ibfk_2` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pedidos_detalle_BEFORE_INSERT` BEFORE INSERT ON `pedidos_detalle` FOR EACH ROW BEGIN
	SET @stock = 0;
    SET @fraccion=0;
    SET @factura_sin_stock=0;
    SET @precioinciva=0;
    SET @base_gravable=0;
    SET @porc_excluido=0;
	SET @porc_gravable=0;
    SET @valor_excluido=0;
    SET @costo=0;
    SET@precioinciva=0;

    
    SELECT cantidad_stock*fraccion + fraccion_stock, fraccion, factura_sin_stock,base_gravable,valor_excluido,costo into @stock, @fraccion, @factura_sin_stock,@base_gravable,@valor_excluido, @costo from productos where producto_id=NEW.producto_id;
    
	SET @cant_salida= NEW.cantidad*@fraccion + NEW.cantidad_fraccion;
    
    IF @stock>=@cant_salida or @factura_sin_stock=1 THEN
		
        -- Actualiza Inventario
		update  productos AS T1
		SET T1.cantidad_stock = T1.cantidad_stock - NEW.cantidad - IF(T1.fraccion_stock - NEW.cantidad_fraccion<0,1,0), T1.fraccion_stock = IF(T1.fraccion_stock - NEW.cantidad_fraccion<0, T1.fraccion + (T1.fraccion_stock-NEW.cantidad_fraccion),T1.fraccion_stock-NEW.cantidad_fraccion)
		WHERE producto_id = NEW.producto_id;
        
        update  productos AS T1
		SET T1.cantidad_stock = T1.cantidad_stock + 1, T1.fraccion_stock = T1.fraccion_stock - T1.fraccion
		WHERE producto_id = NEW.producto_id AND T1.cantidad_stock<0 and T1.fraccion_stock>0 and NEW.cantidad_fraccion>0;
        
        SET @porc_gravable = @base_gravable/@costo;
		SET @porc_excluido = @valor_excluido/@costo;
		
         -- Calcular Valores
		SET NEW.valor_gravado_unidad = (NEW.precio_unidad*@porc_gravable) - (NEW.descuento_unidad*@porc_gravable);
        SET NEW.valor_excluido_unidad = (NEW.precio_unidad*@porc_excluido) - (NEW.descuento_unidad*@porc_excluido);
        
        SET NEW.valor_gravado_fraccion = (NEW.precio_fraccion*@porc_gravable) - (NEW.descuento_fraccion*@porc_gravable);
        SET NEW.valor_excluido_fraccion = (NEW.precio_fraccion*@porc_excluido) - (NEW.descuento_fraccion*@porc_excluido);
       
		 IF @precioinciva=1 THEN
			SET NEW.precio_unidad_antes_iva = (NEW.valor_gravado_unidad / (1+(NEW.iva/100))) + NEW.valor_excluido_unidad;
            SET NEW.precio_fraccion_antes_iva = (NEW.valor_gravado_fraccion / (1+(NEW.iva/100))) + NEW.valor_excluido_fraccion;
            SET NEW.total_gravado = (NEW.valor_gravado_unidad/ (1+(NEW.iva/100))*NEW.cantidad) + (NEW.valor_gravado_fraccion/ (1+(NEW.iva/100))*NEW.cantidad_fraccion);
		ELSE
			SET NEW.precio_unidad_antes_iva =  NEW.valor_gravado_unidad + NEW.valor_excluido_unidad;
            SET NEW.precio_fraccion_antes_iva = NEW.valor_gravado_fraccion + NEW.valor_excluido_fraccion;
			SET NEW.total_gravado = (NEW.valor_gravado_unidad*NEW.cantidad) + (NEW.valor_gravado_fraccion*NEW.cantidad_fraccion);
		END IF;
	else
		SIGNAL SQLSTATE '45000'
		SET MESSAGE_TEXT= 'NO Registrado. Verifique Stock de los Productos';
    END IF;

END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pedidos_detalle_AFTER_INSERT` AFTER INSERT ON `pedidos_detalle` FOR EACH ROW BEGIN
	call calcular_vr_pedido(NEW.pedido_id);	
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pedidos_detalle_BEFORE_UPDATE` BEFORE UPDATE ON `pedidos_detalle` FOR EACH ROW BEGIN
		IF (OLD.descuento_unidad<>New.descuento_unidad OR OLD.descuento_fraccion<>New.descuento_fraccion OR OLD.cantidad<>New.cantidad OR OLD.cantidad_fraccion<>New.cantidad_fraccion) THEN
    
			SET @precioinciva=0;
			SET @base_gravable=0;
			SET @valor_excluido=0;
			SET @porc_excluido=0;
			SET @porc_gravable=0;
			SET @costo=0;
			SET @precioinciva=0;
			
			SELECT precioinciva INTO @precioinciva FROM config LIMIT 1;
			
			SELECT base_gravable,valor_excluido,costo into @base_gravable,@valor_excluido, @costo from productos where producto_id=NEW.producto_id;
			
			SET @porc_gravable = @base_gravable/@costo;
			SET @porc_excluido = @valor_excluido/@costo;
			
			
			 -- Calcular Valores
			SET NEW.valor_gravado_unidad = (NEW.precio_unidad*@porc_gravable) - (NEW.descuento_unidad*@porc_gravable);
			SET NEW.valor_excluido_unidad = (NEW.precio_unidad*@porc_excluido) - (NEW.descuento_unidad*@porc_excluido);
			
			SET NEW.valor_gravado_fraccion = (NEW.precio_fraccion*@porc_gravable) - (NEW.descuento_fraccion*@porc_gravable);
			SET NEW.valor_excluido_fraccion = (NEW.precio_fraccion*@porc_excluido) - (NEW.descuento_fraccion*@porc_excluido);
		   
			 IF @precioinciva=1 THEN
				SET NEW.precio_unidad_antes_iva = (NEW.valor_gravado_unidad / (1+(NEW.iva/100))) + NEW.valor_excluido_unidad;
				SET NEW.precio_fraccion_antes_iva = (NEW.valor_gravado_fraccion / (1+(NEW.iva/100))) + NEW.valor_excluido_fraccion;
				SET NEW.total_gravado = (NEW.valor_gravado_unidad/ (1+(NEW.iva/100))*NEW.cantidad) + (NEW.valor_gravado_fraccion/ (1+(NEW.iva/100))*NEW.cantidad_fraccion);
			ELSE
				SET NEW.precio_unidad_antes_iva =  NEW.valor_gravado_unidad + NEW.valor_excluido_unidad;
				SET NEW.precio_fraccion_antes_iva = NEW.valor_gravado_fraccion + NEW.valor_excluido_fraccion;
				 SET NEW.total_gravado = (NEW.valor_gravado_unidad*NEW.cantidad) + (NEW.valor_gravado_fraccion*NEW.cantidad_fraccion);
			END IF;
        
       
	END IF;


END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pedidos_detalle_AFTER_UPDATE` AFTER UPDATE ON `pedidos_detalle` FOR EACH ROW BEGIN
	SET @stock = 0;
    SET @fraccion=0;
    SELECT cantidad_stock*fraccion + fraccion_stock, fraccion into @stock, @fraccion from productos where producto_id=NEW.producto_id;
    SET @cant_old = OLD.cantidad*@fraccion + OLD.cantidad_fraccion;
    SET @cant_new = NEW.cantidad*@fraccion + NEW.cantidad_fraccion;
    
    IF (@cant_old<@cant_new) then
		update  productos AS T1
		SET T1.cantidad_stock = T1.cantidad_stock - (NEW.cantidad-OLD.cantidad) - IF(T1.fraccion_stock - (NEW.cantidad_fraccion--OLD.cantidad_fraccion)<0,1,0), T1.fraccion_stock = IF(T1.fraccion_stock - (NEW.cantidad_fraccion-OLD.cantidad_fraccion)<0, T1.fraccion + (T1.fraccion_stock-(NEW.cantidad_fraccion-OLD.cantidad_fraccion)),T1.fraccion_stock-(NEW.cantidad_fraccion-OLD.cantidad_fraccion))
		WHERE producto_id = NEW.producto_id;
    else
		UPDATE productos AS T1
		SET T1.cantidad_stock = T1.cantidad_stock + (OLD.cantidad-NEW.cantidad) + TRUNCATE((T1.fraccion_stock + (OLD.cantidad_fraccion-NEW.cantidad_fraccion))/T1.fraccion,0), T1.fraccion_stock =  IF((T1.fraccion_stock + (OLD.cantidad_fraccion-NEW.cantidad_fraccion))>=T1.fraccion,(T1.fraccion_stock + (OLD.cantidad_fraccion-NEW.cantidad_fraccion) )MOD T1.fraccion,T1.fraccion_stock +(OLD.cantidad_fraccion-NEW.cantidad_fraccion))
		WHERE T1.producto_id = OLD.producto_id;
    end if;
    
	update  productos AS T1
	SET T1.cantidad_stock = T1.cantidad_stock + 1, T1.fraccion_stock = T1.fraccion_stock - T1.fraccion
	WHERE producto_id = NEW.producto_id AND T1.cantidad_stock<0 and T1.fraccion_stock>0 and NEW.cantidad_fraccion>0;
        
    call calcular_vr_pedido(NEW.pedido_id);
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `pedidos_detalle_AFTER_DELETE` AFTER DELETE ON `pedidos_detalle` FOR EACH ROW BEGIN
	UPDATE productos AS T1
	SET T1.cantidad_stock = T1.cantidad_stock + OLD.cantidad + TRUNCATE((T1.fraccion_stock + OLD.cantidad_fraccion)/T1.fraccion,0), T1.fraccion_stock =  IF((T1.fraccion_stock + OLD.cantidad_fraccion)>=T1.fraccion,(T1.fraccion_stock + OLD.cantidad_fraccion )MOD T1.fraccion,T1.fraccion_stock +OLD.cantidad_fraccion)
	WHERE T1.producto_id = OLD.producto_id;
    call calcular_vr_pedido(OLD.pedido_id);
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `plantillas`
--

DROP TABLE IF EXISTS `plantillas`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `plantillas` (
  `plantilla_id` int(11) NOT NULL AUTO_INCREMENT,
  `head1` mediumtext,
  `head2` mediumtext,
  `body1` mediumtext,
  `body2` mediumtext,
  `body3` mediumtext,
  `body4` mediumtext,
  `body5` mediumtext,
  `foot1` mediumtext,
  `foot2` mediumtext,
  `foot3` mediumtext,
  `foot4` mediumtext,
  `tipoacta_id` int(11) NOT NULL,
  PRIMARY KEY (`plantilla_id`),
  KEY `fk_plantilla1_idx` (`tipoacta_id`),
  CONSTRAINT `fk_plantilla1` FOREIGN KEY (`tipoacta_id`) REFERENCES `tipo_acta` (`tipoacta_id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `productos_codebar`
--

DROP TABLE IF EXISTS `productos_codebar`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `productos_codebar` (
  `productocodebar_id` int(11) NOT NULL AUTO_INCREMENT,
  `producto_id` int(11) NOT NULL,
  `codebar` varchar(80) NOT NULL,
  `cantidad` int(11) NOT NULL,
  PRIMARY KEY (`productocodebar_id`),
  KEY `producto_id` (`producto_id`),
  CONSTRAINT `productos_codebar_ibfk_1` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `productos_lote`
--

DROP TABLE IF EXISTS `productos_lote`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `productos_lote` (
  `productolote_id` int(11) NOT NULL AUTO_INCREMENT,
  `producto_id` int(11) NOT NULL,
  `lote` varchar(20) NOT NULL,
  `fecha_vencimiento` datetime NOT NULL,
  PRIMARY KEY (`productolote_id`),
  KEY `producto_id` (`producto_id`),
  CONSTRAINT `productos_lote_ibfk_1` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `productos_proveedor`
--

DROP TABLE IF EXISTS `productos_proveedor`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `productos_proveedor` (
  `productosprv_id` int(11) NOT NULL AUTO_INCREMENT,
  `producto_id` int(11) NOT NULL,
  `proveedor_id` int(11) NOT NULL,
  `precio` decimal(18,2) NOT NULL,
  PRIMARY KEY (`productosprv_id`),
  UNIQUE KEY `productos_proveedor_proveedor_id_producto_id_unique` (`producto_id`,`proveedor_id`),
  KEY `proveedor_id` (`proveedor_id`),
  CONSTRAINT `productos_proveedor_ibfk_1` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `productos_proveedor_ibfk_2` FOREIGN KEY (`proveedor_id`) REFERENCES `proveedores` (`proveedor_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `productos_serie`
--

DROP TABLE IF EXISTS `productos_serie`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `productos_serie` (
  `productolote_id` int(11) NOT NULL AUTO_INCREMENT,
  `producto_id` int(11) NOT NULL,
  `serie` varchar(20) NOT NULL,
  `estado` varchar(1) NOT NULL,
  PRIMARY KEY (`productolote_id`),
  KEY `producto_id` (`producto_id`),
  CONSTRAINT `productos_serie_ibfk_1` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `products`
--

DROP TABLE IF EXISTS `products`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `products` (
  `id` varchar(36) NOT NULL,
  `title` varchar(255) NOT NULL,
  `description` varchar(255) DEFAULT NULL,
  `fraction_value` int(11) NOT NULL DEFAULT '1',
  `stock_unit` int(11) NOT NULL DEFAULT '0',
  `stock_fraction` int(11) NOT NULL DEFAULT '0',
  `cost_price` decimal(10,2) NOT NULL DEFAULT '0.00',
  `stock_max_unit` int(11) NOT NULL DEFAULT '0',
  `stock_min_unit` int(11) NOT NULL DEFAULT '0',
  `unit_measure_id` varchar(255) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `IDX_c30f00a871de74c8e8c213acc4` (`title`),
  KEY `FK_bb0e040e578f7d310313af80f9f` (`unit_measure_id`),
  CONSTRAINT `FK_bb0e040e578f7d310313af80f9f` FOREIGN KEY (`unit_measure_id`) REFERENCES `units_measure` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `proveedores`
--

DROP TABLE IF EXISTS `proveedores`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `proveedores` (
  `proveedor_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(20) NOT NULL,
  `actividadeconomica_id` int(11) DEFAULT NULL,
  `tercero_id` int(11) DEFAULT NULL,
  `nombre_comercial` varchar(80) NOT NULL,
  `nombre_contacto` varchar(80) NOT NULL,
  `direccion1` varchar(80) DEFAULT NULL,
  `direccion2` varchar(80) DEFAULT NULL,
  `direccion3` varchar(80) DEFAULT NULL,
  `telefono` varchar(30) DEFAULT NULL,
  `celular` varchar(30) DEFAULT NULL,
  `email` varchar(128) DEFAULT NULL,
  `dias_pago` int(11) DEFAULT NULL,
  `dias_compra` int(11) DEFAULT NULL,
  `compras_acumula_anio` int(11) DEFAULT NULL,
  `compras_acumula_mes` int(11) DEFAULT NULL,
  `fecha_ultima_pago` datetime DEFAULT NULL,
  `fecha_ultima_devolucion` datetime DEFAULT NULL,
  `fecha_creacion` datetime NOT NULL,
  `banco_consignacion` varchar(80) DEFAULT NULL,
  `banco_cuenta` varchar(80) DEFAULT NULL,
  `activo` tinyint(4) NOT NULL DEFAULT '1',
  `precioiva` tinyint(4) NOT NULL DEFAULT '0',
  PRIMARY KEY (`proveedor_id`),
  UNIQUE KEY `IDX_e1ca43154ba84725850c5c13e6` (`codigo`),
  KEY `FK_c5efb8ba41d8b77224b673785b5` (`actividadeconomica_id`),
  KEY `FK_adedc07cbb9b2f73ddb862cdd9c` (`tercero_id`),
  CONSTRAINT `FK_adedc07cbb9b2f73ddb862cdd9c` FOREIGN KEY (`tercero_id`) REFERENCES `terceros` (`tercero_id`),
  CONSTRAINT `FK_c5efb8ba41d8b77224b673785b5` FOREIGN KEY (`actividadeconomica_id`) REFERENCES `actividad_economica` (`actividadeconomica_id`)
) ENGINE=InnoDB AUTO_INCREMENT=42 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `recepciones`
--

DROP TABLE IF EXISTS `recepciones`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `recepciones` (
  `recepcion_id` int(11) NOT NULL AUTO_INCREMENT,
  `compra_id` int(11) NOT NULL,
  `numero` varchar(10) DEFAULT NULL,
  `fecha` datetime DEFAULT NULL,
  `estado` int(11) DEFAULT NULL,
  `observacion` varchar(255) DEFAULT NULL,
  `userid_confirma` int(11) DEFAULT NULL,
  `metodo` varchar(1) DEFAULT NULL COMMENT 'T = Recepción Total\nP = Recepción Parcial',
  `factura` varchar(30) DEFAULT NULL,
  PRIMARY KEY (`recepcion_id`)
) ENGINE=InnoDB AUTO_INCREMENT=188 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `recepciones_AFTER_INSERT` AFTER INSERT ON `recepciones` FOR EACH ROW BEGIN
	DECLARE done INT DEFAULT FALSE;
    DECLARE ids INT;
    DECLARE cur CURSOR FOR 
    SELECT compras_detalle.compra_detalle_id
		FROM compras_detalle
            LEFT JOIN recepciones_detalle ON recepciones_detalle.compra_detalle_id = compras_detalle.compra_detalle_id
		WHERE compra_id=NEW.compra_id and  (recepcion_detalle_id is null or cantidad_recibida < cantidad_pedida);
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    IF NEW.metodo = 'T' THEN
		OPEN cur;
        ins_loop: LOOP
			
            FETCH cur INTO ids;
            IF done THEN
                LEAVE ins_loop;
            END IF;
            SET @cantidad = 0;
			SET @costo = 0;
            
            SELECT  cantidad_pedida - cantidad_recibida, compras_detalle.costo INTO  @cantidad, @costo
            FROM compras_detalle WHERE compra_detalle_id = ids;
            WHILE @cantidad > 0 DO  
				 INSERT INTO recepciones_detalle (recepcion_id, compra_detalle_id , cantidad , costo)
				 VALUES (NEW.recepcion_id, ids, 1 ,@costo);
                 set @cantidad = @cantidad - 1;
			end WHILE;
        END LOOP;
		CLOSE cur;
    END IF;
   
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `recepciones_BEFORE_UPDATE` BEFORE UPDATE ON `recepciones` FOR EACH ROW BEGIN
	IF NEW.`estado`= '1' AND OLD.`estado`= '0' THEN
		SET @consec = 0;
        SET @smlv=0;
        SET @proveedor_id='';

        select smlv into @smlv from reconocimiento where anio = year(NEW.fecha) limit 1;
        select proveedor_id into @proveedor_id from compras where compra_id=NEW.compra_id;
        
        
		INSERT INTO activos (item_id, fecha_adquiere, costo, dependencia_id, contabiliza, recepcion_id, proveedor_id) 
        SELECT item_id, NEW.fecha, costo, -1,IF(costo>=@smlv, 1,0), NEW.recepcion_id, @proveedor_id FROM v_recepcion_detalle WHERE recepcion_id = NEW.recepcion_id;
             
		UPDATE
			`compras_detalle`
			inner join v_compra_recepcion on `compras_detalle`.`compra_detalle_id` = v_compra_recepcion.compra_detalle_id
		SET
			`compras_detalle`.`cantidad_recibida` = `v_compra_recepcion`.`cantidad_recibida`
		where
			 v_compra_recepcion.recepcion_id = NEW.recepcion_id;
             
		SELECT consec_recepcion + 1  INTO @consec FROM `config` LIMIT 1;
		SET NEW.numero = CONCAT('RM',REPEAT('0',5-LENGTH(CAST(@consec AS CHAR))),@consec);
		UPDATE config set consec_recepcion = @consec;
       
        
        SET @pendiente = 0;
        SELECT count(*) INTO @pendiente FROM v_compra_recepcion where compra_id = NEW.compra_id and (diferencia is null or diferencia>0);
        IF (@pendiente>0) THEN
			SET NEW.metodo = 'P';
		else
			SET NEW.metodo = 'T';
        END IF;
    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `recepciones_detalle`
--

DROP TABLE IF EXISTS `recepciones_detalle`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `recepciones_detalle` (
  `recepcion_detalle_id` int(11) NOT NULL AUTO_INCREMENT,
  `recepcion_id` int(11) DEFAULT NULL,
  `compra_detalle_id` int(11) DEFAULT NULL,
  `cantidad` int(11) DEFAULT NULL,
  `costo` decimal(10,2) DEFAULT NULL,
  `observacion` varchar(256) DEFAULT NULL,
  PRIMARY KEY (`recepcion_detalle_id`),
  KEY `fk_recepcion_idx` (`recepcion_id`),
  KEY `fk_compra_detalle_idx` (`compra_detalle_id`),
  CONSTRAINT `fk_compra_detalle` FOREIGN KEY (`compra_detalle_id`) REFERENCES `compras_detalle` (`compra_detalle_id`),
  CONSTRAINT `fk_recepcion` FOREIGN KEY (`recepcion_id`) REFERENCES `recepciones` (`recepcion_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2070 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `reconocimiento`
--

DROP TABLE IF EXISTS `reconocimiento`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `reconocimiento` (
  `reconocimiento_id` int(11) NOT NULL AUTO_INCREMENT,
  `anio` int(11) NOT NULL,
  `smlv` decimal(18,2) NOT NULL,
  PRIMARY KEY (`reconocimiento_id`),
  UNIQUE KEY `anio_UNIQUE` (`anio`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `responsables`
--

DROP TABLE IF EXISTS `responsables`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `responsables` (
  `responsable_id` int(11) NOT NULL AUTO_INCREMENT,
  `identificacion` varchar(45) NOT NULL,
  `nombre` varchar(256) NOT NULL,
  `job_title_id` varchar(255) NOT NULL,
  `fecha_caducidad` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`responsable_id`),
  KEY `FK_ded555cd8975636bd9704069904` (`job_title_id`),
  CONSTRAINT `FK_ded555cd8975636bd9704069904` FOREIGN KEY (`job_title_id`) REFERENCES `jobs_title` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1409 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `retefuente`
--

DROP TABLE IF EXISTS `retefuente`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `retefuente` (
  `retefte_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(512) NOT NULL,
  `base` decimal(18,2) NOT NULL,
  `tarifa` decimal(18,2) NOT NULL,
  `estado` tinyint(4) NOT NULL DEFAULT '0',
  PRIMARY KEY (`retefte_id`)
) ENGINE=InnoDB AUTO_INCREMENT=51 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `reteiva`
--

DROP TABLE IF EXISTS `reteiva`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `reteiva` (
  `reteiva_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(512) NOT NULL,
  `base` decimal(18,2) NOT NULL,
  `tarifa` decimal(18,2) NOT NULL,
  `estado` tinyint(1) NOT NULL DEFAULT '0',
  PRIMARY KEY (`reteiva_id`)
) ENGINE=InnoDB AUTO_INCREMENT=52 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `roles`
--

DROP TABLE IF EXISTS `roles`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `roles` (
  `role_id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(80) NOT NULL,
  `descripcion` varchar(80) NOT NULL,
  PRIMARY KEY (`role_id`)
) ENGINE=InnoDB AUTO_INCREMENT=13 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `services_item`
--

DROP TABLE IF EXISTS `services_item`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `services_item` (
  `id` varchar(36) NOT NULL,
  `description` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `IDX_857ac6a479cc53e426486db529` (`description`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `solicitudes`
--

DROP TABLE IF EXISTS `solicitudes`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `solicitudes` (
  `solicitud_id` int(11) NOT NULL AUTO_INCREMENT,
  `dependencia_id` int(11) NOT NULL,
  `responsable_id` int(11) NOT NULL,
  `fecha_solicitud` datetime NOT NULL,
  `fecha_aprobacion_solicitud` datetime DEFAULT NULL,
  `estado` varchar(1) DEFAULT NULL COMMENT 'R=REGISTRADA\\nA=APROBADA\\nC=SOLICITUD CERRADA\\nA=ANULADA',
  `numero` varchar(255) DEFAULT NULL,
  `direccion_despacho` varchar(80) DEFAULT NULL,
  `observacion` varchar(200) DEFAULT NULL,
  `userid_confirma` int(11) DEFAULT NULL,
  PRIMARY KEY (`solicitud_id`),
  UNIQUE KEY `IDX_cf9b325c9e088004defbfb7621` (`numero`),
  KEY `FK_0cd6994f0df65f5984906c5fe8c` (`dependencia_id`),
  KEY `FK_3ab0adcf04c464c3d59aef8a9d8` (`responsable_id`),
  CONSTRAINT `FK_0cd6994f0df65f5984906c5fe8c` FOREIGN KEY (`dependencia_id`) REFERENCES `dependencias` (`dependencia_id`),
  CONSTRAINT `FK_3ab0adcf04c464c3d59aef8a9d8` FOREIGN KEY (`responsable_id`) REFERENCES `responsables` (`responsable_id`)
) ENGINE=InnoDB AUTO_INCREMENT=55 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `solicitudes_detalle_products`
--

DROP TABLE IF EXISTS `solicitudes_detalle_products`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `solicitudes_detalle_products` (
  `id` varchar(36) NOT NULL,
  `solicitud_id` int(11) NOT NULL,
  `requested_amount` int(11) NOT NULL,
  `approved_amount` int(11) NOT NULL DEFAULT '0',
  `requested_amount_fraction` int(11) NOT NULL,
  `approved_amount_fraction` int(11) NOT NULL DEFAULT '0',
  `product_id` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `FK_ac74c0dd29df723c14292064725` (`solicitud_id`),
  KEY `FK_cdc1c6dd4856b40a38ba49bce4e` (`product_id`),
  CONSTRAINT `FK_ac74c0dd29df723c14292064725` FOREIGN KEY (`solicitud_id`) REFERENCES `solicitudes` (`solicitud_id`),
  CONSTRAINT `FK_cdc1c6dd4856b40a38ba49bce4e` FOREIGN KEY (`product_id`) REFERENCES `products` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `subcategorias`
--

DROP TABLE IF EXISTS `subcategorias`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `subcategorias` (
  `subcategoria_id` int(11) NOT NULL AUTO_INCREMENT,
  `categoria_id` int(11) NOT NULL,
  `codigo` varchar(6) NOT NULL,
  `nombre` varchar(80) NOT NULL,
  PRIMARY KEY (`subcategoria_id`),
  UNIQUE KEY `codigo` (`codigo`),
  KEY `categoria_id` (`categoria_id`),
  CONSTRAINT `subcategorias_ibfk_1` FOREIGN KEY (`categoria_id`) REFERENCES `categorias` (`categoria_id`)
) ENGINE=InnoDB AUTO_INCREMENT=507 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `submenus`
--

DROP TABLE IF EXISTS `submenus`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `submenus` (
  `submenu_id` int(11) NOT NULL AUTO_INCREMENT,
  `menu_id` int(11) NOT NULL,
  `orden` int(11) NOT NULL,
  `titulo` varchar(80) NOT NULL,
  `url` varchar(150) NOT NULL,
  `ab` varchar(8) NOT NULL,
  PRIMARY KEY (`submenu_id`),
  KEY `menu_id` (`menu_id`),
  CONSTRAINT `submenus_ibfk_1` FOREIGN KEY (`menu_id`) REFERENCES `menus` (`menu_id`)
) ENGINE=InnoDB AUTO_INCREMENT=61 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `submenus_roles`
--

DROP TABLE IF EXISTS `submenus_roles`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `submenus_roles` (
  `submenu_role_id` int(11) NOT NULL AUTO_INCREMENT,
  `role_id` int(11) NOT NULL,
  `submenu_id` int(11) NOT NULL,
  PRIMARY KEY (`submenu_role_id`),
  UNIQUE KEY `submenus_roles_role_id_submenu_id_unique` (`role_id`,`submenu_id`),
  KEY `submenu_id` (`submenu_id`),
  CONSTRAINT `submenus_roles_ibfk_1` FOREIGN KEY (`role_id`) REFERENCES `roles` (`role_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `submenus_roles_ibfk_2` FOREIGN KEY (`submenu_id`) REFERENCES `submenus` (`submenu_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=67 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `sustancia_activa`
--

DROP TABLE IF EXISTS `sustancia_activa`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `sustancia_activa` (
  `sustancia_activa_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  PRIMARY KEY (`sustancia_activa_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `terceros`
--

DROP TABLE IF EXISTS `terceros`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `terceros` (
  `tercero_id` int(11) NOT NULL AUTO_INCREMENT,
  `tipodocumento_id` int(11) DEFAULT NULL,
  `tiporegimen_id` int(11) DEFAULT NULL,
  `tipopersona_id` int(11) DEFAULT NULL,
  `municipio_id` int(11) NOT NULL,
  `identificacion` varchar(12) NOT NULL,
  `digito_verificacion` varchar(1) NOT NULL,
  `apellido1` varchar(30) NOT NULL,
  `apellido2` varchar(30) DEFAULT NULL,
  `nombre1` varchar(30) NOT NULL,
  `nombre2` varchar(30) DEFAULT NULL,
  `razon_social1` varchar(80) NOT NULL,
  `razon_social2` varchar(80) DEFAULT NULL,
  `direccion1` varchar(100) NOT NULL,
  `direccion2` varchar(100) DEFAULT NULL,
  `fecha_creacion` datetime NOT NULL,
  `pais_id` int(11) DEFAULT NULL,
  `reteiva` int(11) DEFAULT NULL,
  `retefuente` int(11) DEFAULT NULL,
  `reteica` int(11) DEFAULT NULL,
  `porcreteica` decimal(18,2) DEFAULT NULL,
  `retefte_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`tercero_id`),
  KEY `FK_2492f01b40e5e182b3f3841e483` (`tipodocumento_id`),
  KEY `FK_e1da9c405572b1eac1d44d1f49d` (`tiporegimen_id`),
  KEY `FK_1ca0112cfeb1a893ecd961ebf4a` (`tipopersona_id`),
  CONSTRAINT `FK_1ca0112cfeb1a893ecd961ebf4a` FOREIGN KEY (`tipopersona_id`) REFERENCES `tipos_persona` (`tipopersona_id`),
  CONSTRAINT `FK_2492f01b40e5e182b3f3841e483` FOREIGN KEY (`tipodocumento_id`) REFERENCES `tipos_documento` (`tipodocumento_id`),
  CONSTRAINT `FK_e1da9c405572b1eac1d44d1f49d` FOREIGN KEY (`tiporegimen_id`) REFERENCES `tipos_regimen` (`tiporegimen_id`)
) ENGINE=InnoDB AUTO_INCREMENT=49 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipo_acta`
--

DROP TABLE IF EXISTS `tipo_acta`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipo_acta` (
  `tipoacta_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(256) DEFAULT NULL,
  PRIMARY KEY (`tipoacta_id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_ajuste`
--

DROP TABLE IF EXISTS `tipos_ajuste`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_ajuste` (
  `tipoajuste_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  `mvto` int(11) NOT NULL,
  `documentocontable_id` int(11) NOT NULL,
  PRIMARY KEY (`tipoajuste_id`),
  KEY `fk_tipdoc_idx` (`documentocontable_id`),
  CONSTRAINT `fk_tipdoc` FOREIGN KEY (`documentocontable_id`) REFERENCES `documentos_contables` (`documentocontable_id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_comision`
--

DROP TABLE IF EXISTS `tipos_comision`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_comision` (
  `tipocomision_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(1) NOT NULL,
  `descripcion` varchar(80) NOT NULL,
  PRIMARY KEY (`tipocomision_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_documento`
--

DROP TABLE IF EXISTS `tipos_documento`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_documento` (
  `tipodocumento_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(5) NOT NULL,
  `nombre` varchar(50) NOT NULL,
  PRIMARY KEY (`tipodocumento_id`),
  UNIQUE KEY `IDX_39b02d9b468ed1ce15e9b51e78` (`codigo`)
) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_pago`
--

DROP TABLE IF EXISTS `tipos_pago`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_pago` (
  `tipopago_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(80) NOT NULL,
  PRIMARY KEY (`tipopago_id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_persona`
--

DROP TABLE IF EXISTS `tipos_persona`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_persona` (
  `tipopersona_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(1) NOT NULL,
  `descripcion` varchar(30) NOT NULL,
  PRIMARY KEY (`tipopersona_id`),
  UNIQUE KEY `IDX_375e70b7b040b72bb43b488110` (`codigo`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_precio`
--

DROP TABLE IF EXISTS `tipos_precio`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_precio` (
  `tipoprecio_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(30) NOT NULL,
  `factor_precio` decimal(10,2) NOT NULL,
  PRIMARY KEY (`tipoprecio_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `tipos_precio_AFTER_INSERT` AFTER INSERT ON `tipos_precio` FOR EACH ROW BEGIN
	SET @pventaconiva = 0;
    SET @round_pventa_cen = 0;
    SET @tipo_round_cen = '';
    SET @tipo_round_mil = '';
    SET @valor_round_mil = 0;
    SET @round_pventa_mil = 0;
    
   SELECT precioinciva, round_pventa_cen, tipo_round_cen, tipo_round_mil, valor_round_mil, round_pventa_mil  INTO @pventaconiva, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil   FROM `config` LIMIT 1;
    
    IF (@pventaconiva=1) THEN
		INSERT INTO tiposprecio_productos (producto_id, tipoprecio_id , precio_venta , precio_fraccion, factor)
		SELECT 
		   producto_id,NEW.tipoprecio_id, calcularPVenta( costo , NEW.factor_precio, impuesto_porcentaje, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil, 0) as precio_venta, calcularPVenta( costo_fraccion , NEW.factor_precio, impuesto_porcentaje, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil, fraccion) as precio_fraccion, NEW.factor_precio
		FROM 
		   v_productos_dist;
	ELSE
		 INSERT INTO tiposprecio_productos (producto_id, tipoprecio_id , precio_venta , precio_fraccion, factor)
			SELECT 
			   producto_id,NEW.tipoprecio_id, calcularPVenta( costo , NEW.factor_precio, 0, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil, 0) as precio_venta, calcularPVenta( costo_fraccion , NEW.factor_precio, 0, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil, fraccion) as precio_fraccion, NEW.factor_precio
			FROM 
			   v_productos_dist;
    END IF;
   
       
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `tipos_regimen`
--

DROP TABLE IF EXISTS `tipos_regimen`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_regimen` (
  `tiporegimen_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(1) NOT NULL,
  `descripcion` varchar(30) NOT NULL,
  PRIMARY KEY (`tiporegimen_id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tipos_vendedor`
--

DROP TABLE IF EXISTS `tipos_vendedor`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tipos_vendedor` (
  `tipovendedor_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(5) NOT NULL,
  `descripcion` varchar(30) NOT NULL,
  PRIMARY KEY (`tipovendedor_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `tiposprecio_productos`
--

DROP TABLE IF EXISTS `tiposprecio_productos`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `tiposprecio_productos` (
  `tipoprecioproducto_id` int(11) NOT NULL AUTO_INCREMENT,
  `producto_id` int(11) NOT NULL,
  `tipoprecio_id` int(11) NOT NULL,
  `precio_venta` decimal(10,2) NOT NULL,
  `precio_fraccion` decimal(10,2) NOT NULL,
  `factor` decimal(10,2) NOT NULL,
  PRIMARY KEY (`tipoprecioproducto_id`),
  UNIQUE KEY `tiposprecio_productos_tipoprecio_id_producto_id_unique` (`producto_id`,`tipoprecio_id`),
  KEY `tipoprecio_id` (`tipoprecio_id`),
  CONSTRAINT `tiposprecio_productos_ibfk_1` FOREIGN KEY (`producto_id`) REFERENCES `items` (`item_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `tiposprecio_productos_ibfk_2` FOREIGN KEY (`tipoprecio_id`) REFERENCES `tipos_precio` (`tipoprecio_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
/*!50003 CREATE*/ /*!50017 DEFINER=`root`@`localhost`*/ /*!50003 TRIGGER `tiposprecio_productos_BEFORE_UPDATE` BEFORE UPDATE ON `tiposprecio_productos` FOR EACH ROW BEGIN
	IF NEW.`factor` <> OLD.`factor` AND NEW.`precio_venta`= OLD.`precio_venta` AND NEW.`precio_fraccion`= OLD.`precio_fraccion` THEN
		SET @pventaconiva = 0;
		SET @round_pventa_cen = 0;
		SET @tipo_round_cen = '';
		SET @tipo_round_mil = '';
		SET @valor_round_mil = 0;
		SET @round_pventa_mil = 0;
    
		SELECT precioinciva, round_pventa_cen, tipo_round_cen, tipo_round_mil, valor_round_mil, round_pventa_mil  INTO @pventaconiva, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil   FROM `config` LIMIT 1;
		
        SET @costo = 0;
        SET @costo_fraccion = 0;
		SET @porcentaje = 0;
        SET @fraccion = 0;
        
        SELECT productos.costo, impuestos.porcentaje, productos.costo_fraccion, productos.fraccion into @costo, @porcentaje, @costo_fraccion, @fraccion from productos  
		INNER JOIN impuestos ON productos.impuesto_id=impuestos.impuesto_id
        WHERE productos.producto_id = NEW.producto_id;
            
        IF (@pventaconiva=1) THEN
			
			SET NEW.precio_venta=calcularPVenta( @costo , NEW.`factor`, @porcentaje, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil, @round_pventa_mil, 0); 
            SET NEW.precio_fraccion=calcularPVenta( @costo_fraccion ,NEW.`factor`,  @porcentaje, @round_pventa_cen,@tipo_round_cen,@tipo_round_mil, @valor_round_mil, @round_pventa_mil, @fraccion);

		ELSE
			SET NEW.precio_venta=calcularPVenta( @costo , NEW.`factor`, 0, @round_pventa_cen, @tipo_round_cen, @ipo_round_mil, @valor_round_mil, @round_pventa_mil, 0); 
            SET NEW.precio_fraccion=calcularPVenta(@costo_fraccion ,NEW.`factor`, 0, @round_pventa_cen, @tipo_round_cen, @tipo_round_mil, @valor_round_mil,@round_pventa_mil, @fraccion);
        END IF;
    END IF;
END */;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Table structure for table `type_movement`
--

DROP TABLE IF EXISTS `type_movement`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `type_movement` (
  `id` varchar(36) NOT NULL,
  `description` varchar(255) NOT NULL,
  `movementType` enum('I','O') NOT NULL,
  `destinataryType` enum('R','T') NOT NULL,
  `page_header` longblob,
  `footer` longblob,
  PRIMARY KEY (`id`),
  UNIQUE KEY `IDX_9ec3176d20e9b4a497841b874c` (`description`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `unidad_medida`
--

DROP TABLE IF EXISTS `unidad_medida`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `unidad_medida` (
  `unidadmedida_id` int(11) NOT NULL AUTO_INCREMENT,
  `codigo` varchar(4) NOT NULL,
  `descripcion` varchar(256) NOT NULL,
  PRIMARY KEY (`unidadmedida_id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `units_measure`
--

DROP TABLE IF EXISTS `units_measure`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `units_measure` (
  `id` varchar(36) NOT NULL,
  `description` varchar(255) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `IDX_ea02b1f850bebd0459de537fcb` (`description`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `users`
--

DROP TABLE IF EXISTS `users`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `users` (
  `user_id` int(11) NOT NULL AUTO_INCREMENT,
  `nombre` varchar(80) NOT NULL,
  `email` varchar(80) DEFAULT NULL,
  `password` varchar(80) NOT NULL,
  `img` varchar(100) DEFAULT NULL,
  `google` varchar(1) DEFAULT NULL,
  `activo` int(11) NOT NULL,
  PRIMARY KEY (`user_id`)
) ENGINE=InnoDB AUTO_INCREMENT=28 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `users_roles`
--

DROP TABLE IF EXISTS `users_roles`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `users_roles` (
  `user_role_id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) NOT NULL,
  `role_id` int(11) NOT NULL,
  PRIMARY KEY (`user_role_id`),
  UNIQUE KEY `users_roles_role_id_user_id_unique` (`user_id`,`role_id`),
  KEY `role_id` (`role_id`),
  CONSTRAINT `users_roles_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `users` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `users_roles_ibfk_2` FOREIGN KEY (`role_id`) REFERENCES `roles` (`role_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=169 DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Temporary view structure for view `v_actividad_economica`
--

DROP TABLE IF EXISTS `v_actividad_economica`;
/*!50001 DROP VIEW IF EXISTS `v_actividad_economica`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_actividad_economica` AS SELECT 
 1 AS `actividadeconomica_id`,
 1 AS `codigo`,
 1 AS `descripcion`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_activo_localiza`
--

DROP TABLE IF EXISTS `v_activo_localiza`;
/*!50001 DROP VIEW IF EXISTS `v_activo_localiza`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_activo_localiza` AS SELECT 
 1 AS `activolocaliza_id`,
 1 AS `activo_id`,
 1 AS `fecha_adquiere`,
 1 AS `fecha_disponible`,
 1 AS `dependencia_id_anterior`,
 1 AS `municipio_anterior`,
 1 AS `departamento_anterior`,
 1 AS `dependencia_anterior`,
 1 AS `desde`,
 1 AS `hasta`,
 1 AS `responsable_id_anterior`,
 1 AS `responsable_anterior`,
 1 AS `responsable_id_actual`,
 1 AS `dependencia_id`,
 1 AS `fecha_localiza`,
 1 AS `fecha_creacion`,
 1 AS `estado`,
 1 AS `responsable_actual`,
 1 AS `dependencia_actual`,
 1 AS `municipio_actual`,
 1 AS `departamento_actual`,
 1 AS `observacion`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_activos`
--

DROP TABLE IF EXISTS `v_activos`;
/*!50001 DROP VIEW IF EXISTS `v_activos`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_activos` AS SELECT 
 1 AS `activo_id`,
 1 AS `item_id`,
 1 AS `placa`,
 1 AS `serial`,
 1 AS `fecha_adquiere`,
 1 AS `fecha_disponible`,
 1 AS `costo_activo`,
 1 AS `responsable_id`,
 1 AS `dependencia_id`,
 1 AS `fecha_localiza`,
 1 AS `imagen`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `descripcion_adicional`,
 1 AS `tipo_item`,
 1 AS `marca_id`,
 1 AS `subcategoria_id`,
 1 AS `userid_create`,
 1 AS `userid_update`,
 1 AS `cantidad_stock`,
 1 AS `stockmin`,
 1 AS `stockmax`,
 1 AS `costo_item`,
 1 AS `bloqueo`,
 1 AS `fecha_ultima_compra`,
 1 AS `fecha_creacion`,
 1 AS `costo_ultimo`,
 1 AS `proveedor_id`,
 1 AS `marca`,
 1 AS `codsubcategoria`,
 1 AS `subcategoria`,
 1 AS `categoria_id`,
 1 AS `codcategoria`,
 1 AS `categoria`,
 1 AS `valor_residual`,
 1 AS `barcode`,
 1 AS `display`,
 1 AS `codcatalogoactivo`,
 1 AS `descatalogoactivo`,
 1 AS `codcatalogogasto`,
 1 AS `descatalogogasto`,
 1 AS `vidautil`,
 1 AS `contabiliza`,
 1 AS `estado`,
 1 AS `responsable`,
 1 AS `responsable_caducidad`,
 1 AS `dependencia`,
 1 AS `descripcion_completa`,
 1 AS `municipio`,
 1 AS `departamento`,
 1 AS `proveedor`,
 1 AS `recepcion_id`,
 1 AS `depreciacion_anual`,
 1 AS `depreciacion_mensual`,
 1 AS `tiempo_deprecia`,
 1 AS `costo_neto`,
 1 AS `causacion`,
 1 AS `orden`,
 1 AS `observacion`,
 1 AS `user_baja_id`,
 1 AS `fecha_baja`,
 1 AS `causa_baja`,
 1 AS `observa_baja`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_activos_baja_sin_acta`
--

DROP TABLE IF EXISTS `v_activos_baja_sin_acta`;
/*!50001 DROP VIEW IF EXISTS `v_activos_baja_sin_acta`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_activos_baja_sin_acta` AS SELECT 
 1 AS `activo_id`,
 1 AS `item_id`,
 1 AS `placa`,
 1 AS `serial`,
 1 AS `fecha_adquiere`,
 1 AS `fecha_disponible`,
 1 AS `costo_activo`,
 1 AS `responsable_id`,
 1 AS `dependencia_id`,
 1 AS `fecha_localiza`,
 1 AS `imagen`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `descripcion_adicional`,
 1 AS `tipo_item`,
 1 AS `marca_id`,
 1 AS `subcategoria_id`,
 1 AS `userid_create`,
 1 AS `userid_update`,
 1 AS `cantidad_stock`,
 1 AS `stockmin`,
 1 AS `stockmax`,
 1 AS `costo_item`,
 1 AS `bloqueo`,
 1 AS `fecha_ultima_compra`,
 1 AS `fecha_creacion`,
 1 AS `costo_ultimo`,
 1 AS `proveedor_id`,
 1 AS `marca`,
 1 AS `codsubcategoria`,
 1 AS `subcategoria`,
 1 AS `categoria_id`,
 1 AS `codcategoria`,
 1 AS `categoria`,
 1 AS `valor_residual`,
 1 AS `barcode`,
 1 AS `display`,
 1 AS `codcatalogoactivo`,
 1 AS `descatalogoactivo`,
 1 AS `codcatalogogasto`,
 1 AS `descatalogogasto`,
 1 AS `vidautil`,
 1 AS `contabiliza`,
 1 AS `estado`,
 1 AS `responsable`,
 1 AS `responsable_caducidad`,
 1 AS `dependencia`,
 1 AS `descripcion_completa`,
 1 AS `municipio`,
 1 AS `departamento`,
 1 AS `proveedor`,
 1 AS `recepcion_id`,
 1 AS `depreciacion_anual`,
 1 AS `depreciacion_mensual`,
 1 AS `tiempo_deprecia`,
 1 AS `costo_neto`,
 1 AS `causacion`,
 1 AS `orden`,
 1 AS `observacion`,
 1 AS `user_baja_id`,
 1 AS `fecha_baja`,
 1 AS `causa_baja`,
 1 AS `observa_baja`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_auxiliar`
--

DROP TABLE IF EXISTS `v_auxiliar`;
/*!50001 DROP VIEW IF EXISTS `v_auxiliar`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_auxiliar` AS SELECT 
 1 AS `catalogo_id`,
 1 AS `idpadre`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `vidautil`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_causacion`
--

DROP TABLE IF EXISTS `v_causacion`;
/*!50001 DROP VIEW IF EXISTS `v_causacion`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_causacion` AS SELECT 
 1 AS `item_id`,
 1 AS `facturacompra_id`,
 1 AS `nrofactura`,
 1 AS `fechafactura`,
 1 AS `tipo_doc`,
 1 AS `identificacion`,
 1 AS `nombre_comercial`,
 1 AS `codigo_cuenta`,
 1 AS `descripcion_cuenta`,
 1 AS `valor`,
 1 AS `tipo`,
 1 AS `subtotal`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_causacion_group`
--

DROP TABLE IF EXISTS `v_causacion_group`;
/*!50001 DROP VIEW IF EXISTS `v_causacion_group`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_causacion_group` AS SELECT 
 1 AS `facturacompra_id`,
 1 AS `nrofactura`,
 1 AS `fechafactura`,
 1 AS `tipo_doc`,
 1 AS `identificacion`,
 1 AS `nombre_comercial`,
 1 AS `codigo_cuenta`,
 1 AS `descripcion_cuenta`,
 1 AS `valor`,
 1 AS `tipo`,
 1 AS `subtotal`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_clases`
--

DROP TABLE IF EXISTS `v_clases`;
/*!50001 DROP VIEW IF EXISTS `v_clases`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_clases` AS SELECT 
 1 AS `catalogo_id`,
 1 AS `idpadre`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `vidautil`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_cliente`
--

DROP TABLE IF EXISTS `v_cliente`;
/*!50001 DROP VIEW IF EXISTS `v_cliente`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_cliente` AS SELECT 
 1 AS `cliente_id`,
 1 AS `identificacion`,
 1 AS `tipo_doc`,
 1 AS `display`,
 1 AS `codigo_persona`,
 1 AS `persona`,
 1 AS `codigo_regimen`,
 1 AS `regimen`,
 1 AS `nombre_comercial`,
 1 AS `contacto_cliente`,
 1 AS `direccion1`,
 1 AS `direccion2`,
 1 AS `direccion3`,
 1 AS `telefono`,
 1 AS `celular`,
 1 AS `email`,
 1 AS `activo`,
 1 AS `reteiva`,
 1 AS `retefuente`,
 1 AS `reteica`,
 1 AS `porcreteica`,
 1 AS `base`,
 1 AS `tarifa`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_compra`
--

DROP TABLE IF EXISTS `v_compra`;
/*!50001 DROP VIEW IF EXISTS `v_compra`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_compra` AS SELECT 
 1 AS `compra_id`,
 1 AS `proveedor_id`,
 1 AS `display`,
 1 AS `fechapedido`,
 1 AS `fechavence`,
 1 AS `fechaentrega`,
 1 AS `estado`,
 1 AS `orden`,
 1 AS `factura`,
 1 AS `formapago`,
 1 AS `direccion_despacho`,
 1 AS `observacion`,
 1 AS `descuento`,
 1 AS `valor_gravado`,
 1 AS `valor_excluido`,
 1 AS `nombre_comercial`,
 1 AS `nombre_contacto`,
 1 AS `direccion1`,
 1 AS `direccion2`,
 1 AS `direccion3`,
 1 AS `telefono`,
 1 AS `celular`,
 1 AS `email`,
 1 AS `banco_consignacion`,
 1 AS `banco_cuenta`,
 1 AS `tipo_doc`,
 1 AS `identificacion`,
 1 AS `ordendisplay`,
 1 AS `usuario`,
 1 AS `anulada`,
 1 AS `fecha_anula`,
 1 AS `observa_anula`,
 1 AS `userid_anula`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_compra_detalle`
--

DROP TABLE IF EXISTS `v_compra_detalle`;
/*!50001 DROP VIEW IF EXISTS `v_compra_detalle`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_compra_detalle` AS SELECT 
 1 AS `compra_id`,
 1 AS `compra_detalle_id`,
 1 AS `item_id`,
 1 AS `codigo_interno`,
 1 AS `item_descripcion`,
 1 AS `cantidad_pedida`,
 1 AS `cantidad_recibida`,
 1 AS `costo`,
 1 AS `total`,
 1 AS `codcatalogoactivo`,
 1 AS `descatalogoactivo`,
 1 AS `codcatalogogasto`,
 1 AS `descatalogogasto`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_compra_recepcion`
--

DROP TABLE IF EXISTS `v_compra_recepcion`;
/*!50001 DROP VIEW IF EXISTS `v_compra_recepcion`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_compra_recepcion` AS SELECT 
 1 AS `compra_id`,
 1 AS `compra_detalle_id`,
 1 AS `item_id`,
 1 AS `codigo_interno`,
 1 AS `item_descripcion`,
 1 AS `cantidad_pedida`,
 1 AS `costo`,
 1 AS `cantidad_recibida`,
 1 AS `diferencia`,
 1 AS `recepcion_id`,
 1 AS `total`,
 1 AS `facturacompra_id`,
 1 AS `codcatalogoactivo`,
 1 AS `descatalogoactivo`,
 1 AS `codcatalogogasto`,
 1 AS `descatalogogasto`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_compras_vacias`
--

DROP TABLE IF EXISTS `v_compras_vacias`;
/*!50001 DROP VIEW IF EXISTS `v_compras_vacias`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_compras_vacias` AS SELECT 
 1 AS `compra_id`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_config`
--

DROP TABLE IF EXISTS `v_config`;
/*!50001 DROP VIEW IF EXISTS `v_config`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_config` AS SELECT 
 1 AS `tercero_id`,
 1 AS `codigo_documento`,
 1 AS `tipo_documento`,
 1 AS `identificacion`,
 1 AS `digito_verificacion`,
 1 AS `apellido1`,
 1 AS `apellido2`,
 1 AS `nombre1`,
 1 AS `nombre2`,
 1 AS `razon_social1`,
 1 AS `razon_social2`,
 1 AS `direccion1`,
 1 AS `direccion2`,
 1 AS `codigo_regimen`,
 1 AS `regimen`,
 1 AS `codigo_persona`,
 1 AS `persona`,
 1 AS `codigo_municipio`,
 1 AS `municipio`,
 1 AS `codigo_departamento`,
 1 AS `departamento`,
 1 AS `codigo_pais`,
 1 AS `pais`,
 1 AS `nombre_tercero`,
 1 AS `idennombre`,
 1 AS `config_id`,
 1 AS `logo`,
 1 AS `consec_orden_pedido`,
 1 AS `consec_mov_ent`,
 1 AS `consec_mov_sal`,
 1 AS `reteiva`,
 1 AS `retefuente`,
 1 AS `reteica`,
 1 AS `verimagen`,
 1 AS `coditemauto`,
 1 AS `consec_recepcion`,
 1 AS `porcreteica`,
 1 AS `telefono`,
 1 AS `celular`,
 1 AS `email`,
 1 AS `porcreteiva`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_costo_recepcion`
--

DROP TABLE IF EXISTS `v_costo_recepcion`;
/*!50001 DROP VIEW IF EXISTS `v_costo_recepcion`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_costo_recepcion` AS SELECT 
 1 AS `recepcion_id`,
 1 AS `codigo_cuenta`,
 1 AS `cuenta`,
 1 AS `costo`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_cuentas`
--

DROP TABLE IF EXISTS `v_cuentas`;
/*!50001 DROP VIEW IF EXISTS `v_cuentas`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_cuentas` AS SELECT 
 1 AS `catalogo_id`,
 1 AS `idpadre`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `vidautil`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_dependencias`
--

DROP TABLE IF EXISTS `v_dependencias`;
/*!50001 DROP VIEW IF EXISTS `v_dependencias`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_dependencias` AS SELECT 
 1 AS `dependencia_id`,
 1 AS `dependencia`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_factura_compra`
--

DROP TABLE IF EXISTS `v_factura_compra`;
/*!50001 DROP VIEW IF EXISTS `v_factura_compra`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_factura_compra` AS SELECT 
 1 AS `facturacompra_id`,
 1 AS `formapago`,
 1 AS `nrodocumento`,
 1 AS `dcto`,
 1 AS `fechadcto`,
 1 AS `fechavence`,
 1 AS `proveedor_id`,
 1 AS `tipo_doc`,
 1 AS `identificacion`,
 1 AS `nombre_comercial`,
 1 AS `codigo_persona`,
 1 AS `persona`,
 1 AS `codigo_regimen`,
 1 AS `regimen`,
 1 AS `banco_consignacion`,
 1 AS `banco_cuenta`,
 1 AS `vr_pagar`,
 1 AS `saldo`,
 1 AS `subtotal`,
 1 AS `vr_excluido`,
 1 AS `vr_gravado`,
 1 AS `iva`,
 1 AS `vr_descuento`,
 1 AS `vr_excluido_otros`,
 1 AS `vr_gravado_otros`,
 1 AS `iva_otros`,
 1 AS `retefuente`,
 1 AS `reteiva`,
 1 AS `reteica`,
 1 AS `retefuente_ss`,
 1 AS `reteiva_ss`,
 1 AS `reteica_ss`,
 1 AS `estado`,
 1 AS `anulada`,
 1 AS `usuario`,
 1 AS `generaplano`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_grupos`
--

DROP TABLE IF EXISTS `v_grupos`;
/*!50001 DROP VIEW IF EXISTS `v_grupos`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_grupos` AS SELECT 
 1 AS `catalogo_id`,
 1 AS `idpadre`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `vidautil`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_items`
--

DROP TABLE IF EXISTS `v_items`;
/*!50001 DROP VIEW IF EXISTS `v_items`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_items` AS SELECT 
 1 AS `item_id`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `descripcion_adicional`,
 1 AS `tipo_item`,
 1 AS `marca_id`,
 1 AS `subcategoria_id`,
 1 AS `userid_create`,
 1 AS `userid_update`,
 1 AS `cantidad_stock`,
 1 AS `stockmin`,
 1 AS `stockmax`,
 1 AS `costo`,
 1 AS `bloqueo`,
 1 AS `fecha_ultima_compra`,
 1 AS `fecha_creacion`,
 1 AS `costo_ultimo`,
 1 AS `proveedor_id`,
 1 AS `marca`,
 1 AS `codsubcategoria`,
 1 AS `subcategoria`,
 1 AS `categoria_id`,
 1 AS `codcategoria`,
 1 AS `categoria`,
 1 AS `proveedor`,
 1 AS `valor_residual`,
 1 AS `barcode`,
 1 AS `display`,
 1 AS `codcatalogoactivo`,
 1 AS `descatalogoactivo`,
 1 AS `codcatalogogasto`,
 1 AS `descatalogogasto`,
 1 AS `vidautil`,
 1 AS `descripcion_completa`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_localizacion`
--

DROP TABLE IF EXISTS `v_localizacion`;
/*!50001 DROP VIEW IF EXISTS `v_localizacion`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_localizacion` AS SELECT 
 1 AS `localizacion_id`,
 1 AS `codigo`,
 1 AS `nombre`,
 1 AS `direccion`,
 1 AS `municipio_id`,
 1 AS `lat`,
 1 AS `lng`,
 1 AS `codigo_municipio`,
 1 AS `municipio`,
 1 AS `departamento_id`,
 1 AS `codigo_departamento`,
 1 AS `departamento`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_movinventario`
--

DROP TABLE IF EXISTS `v_movinventario`;
/*!50001 DROP VIEW IF EXISTS `v_movinventario`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_movinventario` AS SELECT 
 1 AS `movinventario_id`,
 1 AS `user_id`,
 1 AS `numero`,
 1 AS `tipo_ajuste`,
 1 AS `mvto`,
 1 AS `codigo_dcto`,
 1 AS `nombre_dcto`,
 1 AS `fechahora`,
 1 AS `observacion`,
 1 AS `estado`,
 1 AS `iden_tercero`,
 1 AS `nombre_tercero`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_movinventario_vacios`
--

DROP TABLE IF EXISTS `v_movinventario_vacios`;
/*!50001 DROP VIEW IF EXISTS `v_movinventario_vacios`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_movinventario_vacios` AS SELECT 
 1 AS `movinventario_id`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_proveedor`
--

DROP TABLE IF EXISTS `v_proveedor`;
/*!50001 DROP VIEW IF EXISTS `v_proveedor`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_proveedor` AS SELECT 
 1 AS `proveedor_id`,
 1 AS `identificacion`,
 1 AS `tipo_doc`,
 1 AS `display`,
 1 AS `codigo_persona`,
 1 AS `persona`,
 1 AS `codigo_regimen`,
 1 AS `regimen`,
 1 AS `nombre_comercial`,
 1 AS `nombre_contacto`,
 1 AS `direccion1`,
 1 AS `direccion2`,
 1 AS `direccion3`,
 1 AS `telefono`,
 1 AS `celular`,
 1 AS `email`,
 1 AS `banco_consignacion`,
 1 AS `banco_cuenta`,
 1 AS `activo`,
 1 AS `dias_pago`,
 1 AS `precioiva`,
 1 AS `retefuente`,
 1 AS `reteiva`,
 1 AS `reteica`,
 1 AS `base`,
 1 AS `tarifa`,
 1 AS `porcreteica`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_recepcion`
--

DROP TABLE IF EXISTS `v_recepcion`;
/*!50001 DROP VIEW IF EXISTS `v_recepcion`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_recepcion` AS SELECT 
 1 AS `recepcion_id`,
 1 AS `compra_id`,
 1 AS `numero`,
 1 AS `factura`,
 1 AS `fecha`,
 1 AS `estado`,
 1 AS `userid_confirma`,
 1 AS `proveedor_id`,
 1 AS `fechapedido`,
 1 AS `orden`,
 1 AS `tipo_doc`,
 1 AS `identificacion`,
 1 AS `nombre_comercial`,
 1 AS `metodo`,
 1 AS `convertida_fac`,
 1 AS `usuario`,
 1 AS `facturarecepcion_id`,
 1 AS `observacion`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_recepcion_detalle`
--

DROP TABLE IF EXISTS `v_recepcion_detalle`;
/*!50001 DROP VIEW IF EXISTS `v_recepcion_detalle`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_recepcion_detalle` AS SELECT 
 1 AS `recepcion_id`,
 1 AS `numero`,
 1 AS `factura`,
 1 AS `recepcion_detalle_id`,
 1 AS `compra_detalle_id`,
 1 AS `item_id`,
 1 AS `codigo_interno`,
 1 AS `item_descripcion`,
 1 AS `cantidad_pedida`,
 1 AS `cantidad_recibida`,
 1 AS `cantidad`,
 1 AS `costo`,
 1 AS `total`,
 1 AS `observacion`,
 1 AS `compra_id`,
 1 AS `estado`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_recepciones_vacias`
--

DROP TABLE IF EXISTS `v_recepciones_vacias`;
/*!50001 DROP VIEW IF EXISTS `v_recepciones_vacias`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_recepciones_vacias` AS SELECT 
 1 AS `recepcion_id`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_responsables`
--

DROP TABLE IF EXISTS `v_responsables`;
/*!50001 DROP VIEW IF EXISTS `v_responsables`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_responsables` AS SELECT 
 1 AS `responsable_id`,
 1 AS `identificacion`,
 1 AS `nombre`,
 1 AS `cargo`,
 1 AS `fecha_caducidad`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_subcuentas`
--

DROP TABLE IF EXISTS `v_subcuentas`;
/*!50001 DROP VIEW IF EXISTS `v_subcuentas`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_subcuentas` AS SELECT 
 1 AS `catalogo_id`,
 1 AS `idpadre`,
 1 AS `codigo`,
 1 AS `descripcion`,
 1 AS `vidautil`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_tercero`
--

DROP TABLE IF EXISTS `v_tercero`;
/*!50001 DROP VIEW IF EXISTS `v_tercero`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_tercero` AS SELECT 
 1 AS `tercero_id`,
 1 AS `codigo_documento`,
 1 AS `tipo_documento`,
 1 AS `identificacion`,
 1 AS `digito_verificacion`,
 1 AS `apellido1`,
 1 AS `apellido2`,
 1 AS `nombre1`,
 1 AS `nombre2`,
 1 AS `razon_social1`,
 1 AS `razon_social2`,
 1 AS `direccion1`,
 1 AS `direccion2`,
 1 AS `codigo_regimen`,
 1 AS `regimen`,
 1 AS `codigo_persona`,
 1 AS `persona`,
 1 AS `codigo_municipio`,
 1 AS `municipio`,
 1 AS `codigo_departamento`,
 1 AS `departamento`,
 1 AS `codigo_pais`,
 1 AS `pais`,
 1 AS `nombre`,
 1 AS `idennombre`,
 1 AS `C`,
 1 AS `P`,
 1 AS `reteiva`,
 1 AS `retefuente`,
 1 AS `reteica`,
 1 AS `porcreteica`,
 1 AS `base`,
 1 AS `tarifa`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_tipotercero`
--

DROP TABLE IF EXISTS `v_tipotercero`;
/*!50001 DROP VIEW IF EXISTS `v_tipotercero`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_tipotercero` AS SELECT 
 1 AS `tercero_id`,
 1 AS `tipo`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_tipotercero_pivot`
--

DROP TABLE IF EXISTS `v_tipotercero_pivot`;
/*!50001 DROP VIEW IF EXISTS `v_tipotercero_pivot`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_tipotercero_pivot` AS SELECT 
 1 AS `tercero_id`,
 1 AS `C`,
 1 AS `P`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_total_recepciones`
--

DROP TABLE IF EXISTS `v_total_recepciones`;
/*!50001 DROP VIEW IF EXISTS `v_total_recepciones`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_total_recepciones` AS SELECT 
 1 AS `orden`,
 1 AS `numero`,
 1 AS `factura`,
 1 AS `recepcion_id`,
 1 AS `proveedor_id`,
 1 AS `facturarecepcion_id`,
 1 AS `facturacompra_id`,
 1 AS `cantprod`,
 1 AS `total`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_usersmenus`
--

DROP TABLE IF EXISTS `v_usersmenus`;
/*!50001 DROP VIEW IF EXISTS `v_usersmenus`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_usersmenus` AS SELECT 
 1 AS `menu_id`,
 1 AS `orden`,
 1 AS `titulo`,
 1 AS `icono`,
 1 AS `user_id`,
 1 AS `usuario_nombre`*/;
SET character_set_client = @saved_cs_client;

--
-- Temporary view structure for view `v_usersubmenu`
--

DROP TABLE IF EXISTS `v_usersubmenu`;
/*!50001 DROP VIEW IF EXISTS `v_usersubmenu`*/;
SET @saved_cs_client     = @@character_set_client;
/*!50503 SET character_set_client = utf8mb4 */;
/*!50001 CREATE VIEW `v_usersubmenu` AS SELECT 
 1 AS `submenu_id`,
 1 AS `menu_id`,
 1 AS `orden`,
 1 AS `titulo`,
 1 AS `url`,
 1 AS `user_id`,
 1 AS `usuario_nombre`,
 1 AS `ab`*/;
SET character_set_client = @saved_cs_client;

--
-- Table structure for table `vendedores`
--

DROP TABLE IF EXISTS `vendedores`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `vendedores` (
  `vendedor_id` int(11) NOT NULL AUTO_INCREMENT,
  `tipovendedor_id` int(11) NOT NULL,
  `nombre` varchar(30) NOT NULL,
  `celular` varchar(30) NOT NULL,
  `porc_comision` decimal(18,2) NOT NULL,
  `cuota_ventas` decimal(18,2) NOT NULL,
  `fecha_creacion` datetime NOT NULL,
  PRIMARY KEY (`vendedor_id`),
  KEY `tipovendedor_id` (`tipovendedor_id`),
  CONSTRAINT `vendedores_ibfk_1` FOREIGN KEY (`tipovendedor_id`) REFERENCES `tipos_vendedor` (`tipovendedor_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Table structure for table `zonas`
--

DROP TABLE IF EXISTS `zonas`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `zonas` (
  `zona_id` int(11) NOT NULL AUTO_INCREMENT,
  `descripcion` varchar(30) NOT NULL,
  PRIMARY KEY (`zona_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping events for database 'sirisinv'
--

--
-- Dumping routines for database 'sirisinv'
--
/*!50003 DROP FUNCTION IF EXISTS `calcularPVenta` */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
CREATE DEFINER=`root`@`localhost` FUNCTION `calcularPVenta`(costo decimal(18,2), utilidad decimal(18,2), iva decimal(18,2), round_pventa_cen int(1), tipo_round_cen char(1), tipo_round_mil char(1), valor_round_mil decimal(10,2), round_pventa_mil int(1), fraccion int(11)) RETURNS decimal(18,2)
    NO SQL
BEGIN
	DECLARE pv INTEGER;
	DECLARE decena INTEGER;
    DECLARE centena INTEGER;
    DECLARE v_iva DECIMAL(18,2);
	DECLARE v_utilidad DECIMAL(18,2);
    SET v_iva = 1 + (iva/100);
    SET v_utilidad = 1 + (utilidad/100);
	IF costo > 0 THEN
        IF fraccion > 1 THEN
			SET @factor_adicional_fraccion = 0;
			SELECT factor_adicional_fraccion  INTO @factor_adicional_fraccion  FROM `config` LIMIT 1;
            SET PV = TRUNCATE(costo*v_utilidad*v_iva * (1 + (@factor_adicional_fraccion /100)),0);
		ELSE
			SET pv = TRUNCATE(costo*v_utilidad*v_iva, 0);
		END IF;
        
        IF round_pventa_cen = 1 THEN
			SET decena = SUBSTRING(CAST(pv AS CHAR), -2, LENGTH(CAST(pv AS CHAR)));
			IF pv >= 100  THEN
			  SET pv = pv - CONVERT(decena, signed integer);
			  if CONVERT(decena, signed integer) > 0 THEN
				IF tipo_round_cen = 'M' OR CONVERT(decena, signed integer)>=50 THEN
					SET pv = pv + 100;
                END IF;
			  END IF;
			ELSE 
			  return 100;
			END IF;
		END IF;
        
        IF round_pventa_mil = 1 THEN
              IF  costo >= valor_round_mil then
				SET centena = SUBSTRING(CAST(pv AS CHAR), -3, LENGTH(CAST(pv AS CHAR)));
                SET pv = pv - CONVERT(centena, signed integer);
                IF centena>0 then
					IF tipo_round_mil = 'M' OR CONVERT(centena, signed integer)>=500 then
						SET pv = pv + 1000;
					END IF;
				END IF;
              END IF;
		END IF;
		return pv;
	else
		return 0;
    END IF;
END ;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 DROP FUNCTION IF EXISTS `calcularPVentaFactorFraccion` */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8 */ ;
/*!50003 SET character_set_results = utf8 */ ;
/*!50003 SET collation_connection  = utf8_general_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
CREATE DEFINER=`root`@`localhost` FUNCTION `calcularPVentaFactorFraccion`(costo decimal(18,2), utilidad decimal(18,2), iva decimal(18,2), round_pventa_cen int(1), tipo_round_cen char(1), tipo_round_mil char(1), valor_round_mil decimal(10,2), round_pventa_mil int(1), fraccion int(11), factor_adicional_fraccion int(11)) RETURNS decimal(18,2)
    NO SQL
BEGIN
	DECLARE pv INTEGER;
	DECLARE decena INTEGER;
    DECLARE centena INTEGER;
    DECLARE v_iva DECIMAL(18,2);
	DECLARE v_utilidad DECIMAL(18,2);
    DECLARE v_factor_adicional_fraccion DECIMAL(18,2);
    SET v_iva = 1 + (iva/100);
    SET v_utilidad = 1 + (utilidad/100);
    SET v_factor_adicional_fraccion = 1 + (factor_adicional_fraccion/100);
	IF costo > 0 THEN
		
        IF fraccion > 1 THEN
			SET pv = TRUNCATE(costo*v_utilidad*v_iva*v_factor_adicional_fraccion, 0);
		ELSE
			SET pv = TRUNCATE(costo*v_utilidad*v_iva, 0);
		END IF;
        
        IF round_pventa_cen = 1 THEN
			SET decena = SUBSTRING(CAST(pv AS CHAR), -2, LENGTH(CAST(pv AS CHAR)));
			IF pv >= 100  THEN
			  SET pv = pv - CONVERT(decena, signed integer);
			  if CONVERT(decena, signed integer) > 0 THEN
				IF tipo_round_cen = 'M' OR CONVERT(decena, signed integer)>=50 THEN
					SET pv = pv + 100;
                END IF;
			  END IF;
			ELSE 
			  return 100;
			END IF;
		END IF;
        
        IF round_pventa_mil = 1 THEN
              IF  costo >= valor_round_mil then
				SET centena = SUBSTRING(CAST(pv AS CHAR), -3, LENGTH(CAST(pv AS CHAR)));
                SET pv = pv - CONVERT(centena, signed integer);
                IF centena>0 then
					IF tipo_round_mil = 'M' OR CONVERT(centena, signed integer)>=500 then
						SET pv = pv + 1000;
					END IF;
				END IF;
              END IF;
		END IF;
		return pv;
	else
		return 0;
    END IF;
END ;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 DROP PROCEDURE IF EXISTS `gen_barcode` */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
CREATE DEFINER=`sistemas`@`%` PROCEDURE `gen_barcode`(IN id INT)
BEGIN
	SET @aleatorio=CAST(CAST(rand()*1000000 AS UNSIGNED) as CHAR);
	SET @placa=CONCAT('2',id, REPEAT('0',12-(LENGTH(CAST(id AS CHAR)) + LENGTH(CAST(@aleatorio as char)))),@aleatorio);
    UPDATE activos set placa=@placa where activo_id=id;
END ;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 DROP PROCEDURE IF EXISTS `get_activos_deprecia` */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
CREATE DEFINER=`sistemas`@`%` PROCEDURE `get_activos_deprecia`(IN fecha_referencia DATE)
BEGIN
SELECT 
        `activos`.`activo_id` AS `activo_id`,
        `activos`.`item_id` AS `item_id`,
        `activos`.`placa` AS `placa`,
        `activos`.`serial` AS `serial`,
        `activos`.`fecha_adquiere` AS `fecha_adquiere`,
        `activos`.`fecha_disponible` AS `fecha_disponible`,
        `activos`.`costo` AS `costo_activo`,
        `activos`.`responsable_id` AS `responsable_id`,
        `activos`.`dependencia_id` AS `dependencia_id`,
        `activos`.`fecha_localiza` AS `fecha_localiza`,
        `activos`.`imagen` AS `imagen`,
        `v_items`.`codigo` AS `codigo`,
        `v_items`.`descripcion` AS `descripcion`,
        `v_items`.`descripcion_adicional` AS `descripcion_adicional`,
        `v_items`.`tipo_item` AS `tipo_item`,
        `v_items`.`marca_id` AS `marca_id`,
        `v_items`.`subcategoria_id` AS `subcategoria_id`,
        `v_items`.`userid_create` AS `userid_create`,
        `v_items`.`userid_update` AS `userid_update`,
        `v_items`.`cantidad_stock` AS `cantidad_stock`,
        `v_items`.`stockmin` AS `stockmin`,
        `v_items`.`stockmax` AS `stockmax`,
        `v_items`.`costo` AS `costo_item`,
        `v_items`.`bloqueo` AS `bloqueo`,
        `v_items`.`fecha_ultima_compra` AS `fecha_ultima_compra`,
        `v_items`.`fecha_creacion` AS `fecha_creacion`,
        `v_items`.`costo_ultimo` AS `costo_ultimo`,
        `v_items`.`proveedor_id` AS `proveedor_id`,
        `v_items`.`marca` AS `marca`,
        `v_items`.`codsubcategoria` AS `codsubcategoria`,
        `v_items`.`subcategoria` AS `subcategoria`,
        `v_items`.`categoria_id` AS `categoria_id`,
        `v_items`.`codcategoria` AS `codcategoria`,
        `v_items`.`categoria` AS `categoria`,
        `v_items`.`valor_residual` AS `valor_residual`,
        `v_items`.`barcode` AS `barcode`,
        CONCAT(COALESCE(`activos`.`placa`, 'N/R'),
                ' | ',
                CONVERT( `v_items`.`display` USING UTF8MB4)) AS `display`,
        `v_items`.`codcatalogoactivo` AS `codcatalogoactivo`,
        `v_items`.`descatalogoactivo` AS `descatalogoactivo`,
        `v_items`.`codcatalogogasto` AS `codcatalogogasto`,
        `v_items`.`descatalogogasto` AS `descatalogogasto`,
        `v_items`.`vidautil` AS `vidautil`,
        `activos`.`contabiliza` AS `contabiliza`,
        `activos`.`estado` AS `estado`,
        COALESCE(`responsables`.`nombre`, 'NO ASIGNADO') AS `responsable`,
        `responsables`.`fecha_caducidad` AS `responsable_caducidad`,
        CONCAT(`v_localizacion`.`nombre`,
                ' - ',
                `dependencias`.`nombre`) AS `dependencia`,
        `v_items`.`descripcion_completa` AS `descripcion_completa`,
        `v_localizacion`.`municipio` AS `municipio`,
        `v_localizacion`.`municipio` AS `departamento`,
        `v_proveedor`.`display` AS `proveedor`,
        `activos`.`recepcion_id` AS `recepcion_id`,
        IF(((`activos`.`costo` > 0)
                AND (`v_items`.`vidautil` > 0)),
            ROUND(((`activos`.`costo` - `v_items`.`valor_residual`) / `v_items`.`vidautil`),
                    2),
            0) AS `depreciacion_anual`,
        IF(((`activos`.`costo` > 0)
                AND (`v_items`.`vidautil` > 0)),
            ROUND((((`activos`.`costo` - `v_items`.`valor_residual`) / `v_items`.`vidautil`) / 12),
                    2),
            1) AS `depreciacion_mensual`,
		 ((TO_DAYS(fecha_referencia) - TO_DAYS(`activos`.`fecha_disponible`)) / 30) AS `tiempo_deprecia`,
         IF((((TO_DAYS(fecha_referencia) - TO_DAYS(`activos`.`fecha_disponible`)) / 30) IS NOT NULL and (TO_DAYS(fecha_referencia) - TO_DAYS(`activos`.`fecha_disponible`)) / 30>0),
            (`activos`.`costo` - IF(((`activos`.`costo` > 0)
                    AND (`v_items`.`vidautil` > 0)),
                ROUND((((`activos`.`costo` - `v_items`.`valor_residual`) / `v_items`.`vidautil`) / 12)*(TO_DAYS(fecha_referencia) - TO_DAYS(`activos`.`fecha_disponible`)) / 30,
                        2),
                0)),
            `activos`.`costo`) AS `costo_neto`
    FROM
        (((((`activos`
        JOIN `v_items` ON ((`activos`.`item_id` = `v_items`.`item_id`)))
        LEFT JOIN `dependencias` ON ((`dependencias`.`dependencia_id` = `activos`.`dependencia_id`)))
        LEFT JOIN `v_localizacion` ON ((`dependencias`.`localizacion_id` = `v_localizacion`.`localizacion_id`)))
        LEFT JOIN `v_proveedor` ON ((`activos`.`proveedor_id` = `v_proveedor`.`proveedor_id`)))
        LEFT JOIN `responsables` ON ((`responsables`.`responsable_id` = `activos`.`responsable_id`)));
END ;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;

--
-- Final view structure for view `v_actividad_economica`
--

/*!50001 DROP VIEW IF EXISTS `v_actividad_economica`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_actividad_economica` AS select `actividad_economica`.`actividadeconomica_id` AS `actividadeconomica_id`,`actividad_economica`.`codigo` AS `codigo`,concat(`actividad_economica`.`codigo`,' | ',`actividad_economica`.`descripcion`) AS `descripcion` from `actividad_economica` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_activo_localiza`
--

/*!50001 DROP VIEW IF EXISTS `v_activo_localiza`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_activo_localiza` AS select `activo_localiza`.`activolocaliza_id` AS `activolocaliza_id`,`activo_localiza`.`activo_id` AS `activo_id`,`v_activos`.`fecha_adquiere` AS `fecha_adquiere`,`v_activos`.`fecha_disponible` AS `fecha_disponible`,`activo_localiza`.`dependencia_id` AS `dependencia_id_anterior`,`v_localizacion`.`municipio` AS `municipio_anterior`,`v_localizacion`.`departamento` AS `departamento_anterior`,concat(`v_localizacion`.`nombre`,' - ',`dependencias`.`nombre`) AS `dependencia_anterior`,if(isnull(`activo_localiza`.`desde`),`v_activos`.`fecha_localiza`,`activo_localiza`.`desde`) AS `desde`,`activo_localiza`.`hasta` AS `hasta`,`activo_localiza`.`responsable_id` AS `responsable_id_anterior`,`responsables`.`nombre` AS `responsable_anterior`,`v_activos`.`responsable_id` AS `responsable_id_actual`,`v_activos`.`dependencia_id` AS `dependencia_id`,`v_activos`.`fecha_localiza` AS `fecha_localiza`,`v_activos`.`fecha_creacion` AS `fecha_creacion`,`v_activos`.`estado` AS `estado`,`v_activos`.`responsable` AS `responsable_actual`,`v_activos`.`dependencia` AS `dependencia_actual`,`v_activos`.`municipio` AS `municipio_actual`,`v_activos`.`departamento` AS `departamento_actual`,`activo_localiza`.`observacion` AS `observacion` from ((((`activo_localiza` join `v_activos` on((`v_activos`.`activo_id` = `activo_localiza`.`activo_id`))) join `dependencias` on((`dependencias`.`dependencia_id` = `activo_localiza`.`dependencia_id`))) join `v_localizacion` on((`dependencias`.`localizacion_id` = `v_localizacion`.`localizacion_id`))) join `responsables` on((`responsables`.`responsable_id` = `activo_localiza`.`responsable_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_activos`
--

/*!50001 DROP VIEW IF EXISTS `v_activos`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_activos` AS select `activos`.`activo_id` AS `activo_id`,`activos`.`item_id` AS `item_id`,`activos`.`placa` AS `placa`,`activos`.`serial` AS `serial`,`activos`.`fecha_adquiere` AS `fecha_adquiere`,`activos`.`fecha_disponible` AS `fecha_disponible`,`activos`.`costo` AS `costo_activo`,`activos`.`responsable_id` AS `responsable_id`,`activos`.`dependencia_id` AS `dependencia_id`,`activos`.`fecha_localiza` AS `fecha_localiza`,`activos`.`imagen` AS `imagen`,`v_items`.`codigo` AS `codigo`,`v_items`.`descripcion` AS `descripcion`,`v_items`.`descripcion_adicional` AS `descripcion_adicional`,`v_items`.`tipo_item` AS `tipo_item`,`v_items`.`marca_id` AS `marca_id`,`v_items`.`subcategoria_id` AS `subcategoria_id`,`v_items`.`userid_create` AS `userid_create`,`v_items`.`userid_update` AS `userid_update`,`v_items`.`cantidad_stock` AS `cantidad_stock`,`v_items`.`stockmin` AS `stockmin`,`v_items`.`stockmax` AS `stockmax`,`v_items`.`costo` AS `costo_item`,`v_items`.`bloqueo` AS `bloqueo`,`v_items`.`fecha_ultima_compra` AS `fecha_ultima_compra`,`v_items`.`fecha_creacion` AS `fecha_creacion`,`v_items`.`costo_ultimo` AS `costo_ultimo`,`v_items`.`proveedor_id` AS `proveedor_id`,`v_items`.`marca` AS `marca`,`v_items`.`codsubcategoria` AS `codsubcategoria`,`v_items`.`subcategoria` AS `subcategoria`,`v_items`.`categoria_id` AS `categoria_id`,`v_items`.`codcategoria` AS `codcategoria`,`v_items`.`categoria` AS `categoria`,`v_items`.`valor_residual` AS `valor_residual`,`v_items`.`barcode` AS `barcode`,concat(coalesce(`activos`.`placa`,'N/R'),' | ',convert(replace(`v_items`.`display`,',','') using utf8mb4)) AS `display`,`v_items`.`codcatalogoactivo` AS `codcatalogoactivo`,`v_items`.`descatalogoactivo` AS `descatalogoactivo`,`v_items`.`codcatalogogasto` AS `codcatalogogasto`,`v_items`.`descatalogogasto` AS `descatalogogasto`,`v_items`.`vidautil` AS `vidautil`,`activos`.`contabiliza` AS `contabiliza`,`activos`.`estado` AS `estado`,coalesce(`responsables`.`nombre`,'NO ASIGNADO') AS `responsable`,`responsables`.`fecha_caducidad` AS `responsable_caducidad`,concat(`v_localizacion`.`nombre`,' - ',`dependencias`.`nombre`) AS `dependencia`,`v_items`.`descripcion_completa` AS `descripcion_completa`,`v_localizacion`.`municipio` AS `municipio`,`v_localizacion`.`municipio` AS `departamento`,`v_proveedor`.`display` AS `proveedor`,`activos`.`recepcion_id` AS `recepcion_id`,if(((`activos`.`costo` > 0) and (`v_items`.`vidautil` > 0)),round(((`activos`.`costo` - `v_items`.`valor_residual`) / `v_items`.`vidautil`),2),0) AS `depreciacion_anual`,if(((`activos`.`costo` > 0) and (`v_items`.`vidautil` > 0)),round((((`activos`.`costo` - `v_items`.`valor_residual`) / `v_items`.`vidautil`) / 12),2),0) AS `depreciacion_mensual`,((to_days(now()) - to_days(`activos`.`fecha_disponible`)) / 30) AS `tiempo_deprecia`,if((((to_days(now()) - to_days(`activos`.`fecha_disponible`)) / 30) is not null),(`activos`.`costo` - if(((`activos`.`costo` > 0) and (`v_items`.`vidautil` > 0)),round((((((`activos`.`costo` - `v_items`.`valor_residual`) / `v_items`.`vidautil`) / 12) * (to_days(now()) - to_days(`activos`.`fecha_disponible`))) / 30),2),0)),`activos`.`costo`) AS `costo_neto`,`activos`.`causacion` AS `causacion`,`v_recepcion`.`orden` AS `orden`,`activos`.`observacion` AS `observacion`,`activos`.`user_baja_id` AS `user_baja_id`,`activos`.`fecha_baja` AS `fecha_baja`,`activos`.`causa_baja` AS `causa_baja`,`activos`.`observa_baja` AS `observa_baja` from ((((((`activos` join `v_items` on((`activos`.`item_id` = `v_items`.`item_id`))) left join `dependencias` on((`dependencias`.`dependencia_id` = `activos`.`dependencia_id`))) left join `v_localizacion` on((`dependencias`.`localizacion_id` = `v_localizacion`.`localizacion_id`))) left join `v_proveedor` on((`activos`.`proveedor_id` = `v_proveedor`.`proveedor_id`))) left join `responsables` on((`responsables`.`responsable_id` = `activos`.`responsable_id`))) left join `v_recepcion` on((`v_recepcion`.`recepcion_id` = `activos`.`recepcion_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_activos_baja_sin_acta`
--

/*!50001 DROP VIEW IF EXISTS `v_activos_baja_sin_acta`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_activos_baja_sin_acta` AS select `v_activos`.`activo_id` AS `activo_id`,`v_activos`.`item_id` AS `item_id`,`v_activos`.`placa` AS `placa`,`v_activos`.`serial` AS `serial`,`v_activos`.`fecha_adquiere` AS `fecha_adquiere`,`v_activos`.`fecha_disponible` AS `fecha_disponible`,`v_activos`.`costo_activo` AS `costo_activo`,`v_activos`.`responsable_id` AS `responsable_id`,`v_activos`.`dependencia_id` AS `dependencia_id`,`v_activos`.`fecha_localiza` AS `fecha_localiza`,`v_activos`.`imagen` AS `imagen`,`v_activos`.`codigo` AS `codigo`,`v_activos`.`descripcion` AS `descripcion`,`v_activos`.`descripcion_adicional` AS `descripcion_adicional`,`v_activos`.`tipo_item` AS `tipo_item`,`v_activos`.`marca_id` AS `marca_id`,`v_activos`.`subcategoria_id` AS `subcategoria_id`,`v_activos`.`userid_create` AS `userid_create`,`v_activos`.`userid_update` AS `userid_update`,`v_activos`.`cantidad_stock` AS `cantidad_stock`,`v_activos`.`stockmin` AS `stockmin`,`v_activos`.`stockmax` AS `stockmax`,`v_activos`.`costo_item` AS `costo_item`,`v_activos`.`bloqueo` AS `bloqueo`,`v_activos`.`fecha_ultima_compra` AS `fecha_ultima_compra`,`v_activos`.`fecha_creacion` AS `fecha_creacion`,`v_activos`.`costo_ultimo` AS `costo_ultimo`,`v_activos`.`proveedor_id` AS `proveedor_id`,`v_activos`.`marca` AS `marca`,`v_activos`.`codsubcategoria` AS `codsubcategoria`,`v_activos`.`subcategoria` AS `subcategoria`,`v_activos`.`categoria_id` AS `categoria_id`,`v_activos`.`codcategoria` AS `codcategoria`,`v_activos`.`categoria` AS `categoria`,`v_activos`.`valor_residual` AS `valor_residual`,`v_activos`.`barcode` AS `barcode`,`v_activos`.`display` AS `display`,`v_activos`.`codcatalogoactivo` AS `codcatalogoactivo`,`v_activos`.`descatalogoactivo` AS `descatalogoactivo`,`v_activos`.`codcatalogogasto` AS `codcatalogogasto`,`v_activos`.`descatalogogasto` AS `descatalogogasto`,`v_activos`.`vidautil` AS `vidautil`,`v_activos`.`contabiliza` AS `contabiliza`,`v_activos`.`estado` AS `estado`,`v_activos`.`responsable` AS `responsable`,`v_activos`.`responsable_caducidad` AS `responsable_caducidad`,`v_activos`.`dependencia` AS `dependencia`,`v_activos`.`descripcion_completa` AS `descripcion_completa`,`v_activos`.`municipio` AS `municipio`,`v_activos`.`departamento` AS `departamento`,`v_activos`.`proveedor` AS `proveedor`,`v_activos`.`recepcion_id` AS `recepcion_id`,`v_activos`.`depreciacion_anual` AS `depreciacion_anual`,`v_activos`.`depreciacion_mensual` AS `depreciacion_mensual`,`v_activos`.`tiempo_deprecia` AS `tiempo_deprecia`,`v_activos`.`costo_neto` AS `costo_neto`,`v_activos`.`causacion` AS `causacion`,`v_activos`.`orden` AS `orden`,`v_activos`.`observacion` AS `observacion`,`v_activos`.`user_baja_id` AS `user_baja_id`,`v_activos`.`fecha_baja` AS `fecha_baja`,`v_activos`.`causa_baja` AS `causa_baja`,`v_activos`.`observa_baja` AS `observa_baja` from `v_activos` where ((`v_activos`.`estado` = 'B') and (`v_activos`.`activo_id` in (select `detalle_actbaja`.`activo_id` from `detalle_actbaja`) is false)) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_auxiliar`
--

/*!50001 DROP VIEW IF EXISTS `v_auxiliar`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_auxiliar` AS select `catalogo_contable`.`catalogo_id` AS `catalogo_id`,`catalogo_contable`.`idpadre` AS `idpadre`,`catalogo_contable`.`codigo` AS `codigo`,`catalogo_contable`.`descripcion` AS `descripcion`,`catalogo_contable`.`vidautil` AS `vidautil` from `catalogo_contable` where (length(`catalogo_contable`.`codigo`) = 8) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_causacion`
--

/*!50001 DROP VIEW IF EXISTS `v_causacion`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_causacion` AS select distinct `v_compra_detalle`.`item_id` AS `item_id`,`factura_compra`.`facturacompra_id` AS `facturacompra_id`,`factura_compra`.`nrofactura` AS `nrofactura`,`factura_compra`.`fechafactura` AS `fechafactura`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,if((`v_compra_detalle`.`costo` >= `reconocimiento`.`smlv`),`v_compra_detalle`.`codcatalogoactivo`,`v_compra_detalle`.`codcatalogogasto`) AS `codigo_cuenta`,if((`v_compra_detalle`.`costo` >= `reconocimiento`.`smlv`),`v_compra_detalle`.`descatalogoactivo`,`v_compra_detalle`.`descatalogogasto`) AS `descripcion_cuenta`,`v_compra_detalle`.`total` AS `valor`,'D' AS `tipo`,`factura_compra`.`subtotal` AS `subtotal` from (((((`v_compra_detalle` left join `v_recepcion_detalle` on((`v_recepcion_detalle`.`compra_detalle_id` = `v_compra_detalle`.`compra_detalle_id`))) left join `factura_recepcion` on((`factura_recepcion`.`recepcion_id` = `v_recepcion_detalle`.`recepcion_id`))) join `factura_compra` on((`factura_compra`.`facturacompra_id` = `factura_recepcion`.`facturacompra_id`))) join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `factura_compra`.`proveedor_id`))) left join `reconocimiento` on((`reconocimiento`.`anio` = year(`factura_compra`.`fechafactura`)))) union all select 0 AS `item_id`,`factura_compra`.`facturacompra_id` AS `facturacompra_id`,`factura_compra`.`nrofactura` AS `nrofactura`,`factura_compra`.`fechafactura` AS `fechafactura`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,`catalogo_contable`.`codigo` AS `codigo_cuenta`,`catalogo_contable`.`descripcion` AS `descripcion_cuenta`,(`factura_compra`.`vr_excluido_otros` + `factura_compra`.`vr_gravado_otros`) AS `valor`,'D' AS `tipo`,`factura_compra`.`subtotal` AS `subtotal` from ((`factura_compra` join `catalogo_contable` on((`catalogo_contable`.`catalogo_id` = `factura_compra`.`ctaotros_id`))) join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `factura_compra`.`proveedor_id`))) where ((`factura_compra`.`vr_excluido_otros` > 0) or (`factura_compra`.`vr_gravado_otros` > 0)) union all select 0 AS `item_id`,`factura_compra`.`facturacompra_id` AS `facturacompra_id`,`factura_compra`.`nrofactura` AS `nrofactura`,`factura_compra`.`fechafactura` AS `fechafactura`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,if((((`factura_compra`.`retefuente` / `factura_compra`.`subtotal`) * 100) = 3.5),'24360805',if((((`factura_compra`.`retefuente` / `factura_compra`.`subtotal`) * 100) = 2.5),'24360801','24360801')) AS `codigo_cuenta`,if((((`factura_compra`.`retefuente` / `factura_compra`.`subtotal`) * 100) = 3.5),'COMPRAS 3.5%',if((((`factura_compra`.`retefuente` / `factura_compra`.`subtotal`) * 100) = 2.5),'COMPRAS 2.5%','COMPRAS 2.5%')) AS `descripcion_cuenta`,`factura_compra`.`retefuente` AS `valor`,'H' AS `tipo`,`factura_compra`.`subtotal` AS `subtotal` from (`factura_compra` join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `factura_compra`.`proveedor_id`))) where (`factura_compra`.`retefuente` > 0) union all select 0 AS `item_id`,`factura_compra`.`facturacompra_id` AS `facturacompra_id`,`factura_compra`.`nrofactura` AS `nrofactura`,`factura_compra`.`fechafactura` AS `fechafactura`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,'24362501' AS `codigo_cuenta`,'IMPUESTO A LAS VENTAS RETENIDO POR CONSI' AS `descripcion_cuenta`,`factura_compra`.`reteiva` AS `valor`,'H' AS `tipo`,`factura_compra`.`subtotal` AS `subtotal` from (`factura_compra` join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `factura_compra`.`proveedor_id`))) where (`factura_compra`.`reteiva` > 0) union all select 0 AS `item_id`,`factura_compra`.`facturacompra_id` AS `facturacompra_id`,`factura_compra`.`nrofactura` AS `nrofactura`,`factura_compra`.`fechafactura` AS `fechafactura`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,'-' AS `codigo_cuenta`,'RETEICA' AS `descripcion_cuenta`,`factura_compra`.`reteica` AS `valor`,'H' AS `tipo`,`factura_compra`.`subtotal` AS `subtotal` from (`factura_compra` join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `factura_compra`.`proveedor_id`))) where (`factura_compra`.`reteica` > 0) union all select 0 AS `item_id`,`factura_compra`.`facturacompra_id` AS `facturacompra_id`,`factura_compra`.`nrofactura` AS `nrofactura`,`factura_compra`.`fechafactura` AS `fechafactura`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,'24909003' AS `codigo_cuenta`,'OTRAS CUENTAS POR PAGAR  ' AS `descripcion_cuenta`,`factura_compra`.`vr_pagar` AS `valor`,'H' AS `tipo`,`factura_compra`.`subtotal` AS `subtotal` from (`factura_compra` join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `factura_compra`.`proveedor_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_causacion_group`
--

/*!50001 DROP VIEW IF EXISTS `v_causacion_group`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_causacion_group` AS select `v_causacion`.`facturacompra_id` AS `facturacompra_id`,`v_causacion`.`nrofactura` AS `nrofactura`,`v_causacion`.`fechafactura` AS `fechafactura`,`v_causacion`.`tipo_doc` AS `tipo_doc`,`v_causacion`.`identificacion` AS `identificacion`,`v_causacion`.`nombre_comercial` AS `nombre_comercial`,`v_causacion`.`codigo_cuenta` AS `codigo_cuenta`,`v_causacion`.`descripcion_cuenta` AS `descripcion_cuenta`,sum(`v_causacion`.`valor`) AS `valor`,`v_causacion`.`tipo` AS `tipo`,`v_causacion`.`subtotal` AS `subtotal` from `v_causacion` group by `v_causacion`.`facturacompra_id`,`v_causacion`.`nrofactura`,`v_causacion`.`fechafactura`,`v_causacion`.`tipo_doc`,`v_causacion`.`identificacion`,`v_causacion`.`nombre_comercial`,`v_causacion`.`codigo_cuenta`,`v_causacion`.`descripcion_cuenta`,`v_causacion`.`tipo`,`v_causacion`.`subtotal` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_clases`
--

/*!50001 DROP VIEW IF EXISTS `v_clases`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_clases` AS select `catalogo_contable`.`catalogo_id` AS `catalogo_id`,`catalogo_contable`.`idpadre` AS `idpadre`,`catalogo_contable`.`codigo` AS `codigo`,`catalogo_contable`.`descripcion` AS `descripcion`,`catalogo_contable`.`vidautil` AS `vidautil` from `catalogo_contable` where (length(`catalogo_contable`.`codigo`) = 1) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_cliente`
--

/*!50001 DROP VIEW IF EXISTS `v_cliente`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_cliente` AS select `clientes`.`cliente_id` AS `cliente_id`,`v_tercero`.`identificacion` AS `identificacion`,`v_tercero`.`tipo_documento` AS `tipo_doc`,concat('Codigo: ',`clientes`.`codigo`,' | ',`v_tercero`.`tipo_documento`,' ',`v_tercero`.`identificacion`,'  | ',`clientes`.`nombre_comercial`,'  | ',`v_tercero`.`nombre`,' | Ciudad: ',`v_tercero`.`municipio`,' ',`v_tercero`.`departamento`) AS `display`,`v_tercero`.`codigo_persona` AS `codigo_persona`,`v_tercero`.`persona` AS `persona`,`v_tercero`.`codigo_regimen` AS `codigo_regimen`,`v_tercero`.`regimen` AS `regimen`,`clientes`.`nombre_comercial` AS `nombre_comercial`,`clientes`.`contacto_cliente` AS `contacto_cliente`,`clientes`.`direccion1` AS `direccion1`,`clientes`.`direccion2` AS `direccion2`,`clientes`.`direccion3` AS `direccion3`,`clientes`.`telefono` AS `telefono`,`clientes`.`celular` AS `celular`,`clientes`.`email` AS `email`,`clientes`.`activo` AS `activo`,`v_tercero`.`reteiva` AS `reteiva`,`v_tercero`.`retefuente` AS `retefuente`,`v_tercero`.`reteica` AS `reteica`,`v_tercero`.`porcreteica` AS `porcreteica`,`v_tercero`.`base` AS `base`,`v_tercero`.`tarifa` AS `tarifa` from (`clientes` join `v_tercero` on((`v_tercero`.`tercero_id` = `clientes`.`tercero_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_compra`
--

/*!50001 DROP VIEW IF EXISTS `v_compra`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_compra` AS select `compras`.`compra_id` AS `compra_id`,`compras`.`proveedor_id` AS `proveedor_id`,concat(`compras`.`orden`,' | ',`v_proveedor`.`tipo_doc`,' ',`v_proveedor`.`identificacion`,' | ',`v_proveedor`.`nombre_comercial`) AS `display`,`compras`.`fechapedido` AS `fechapedido`,`compras`.`fechavence` AS `fechavence`,`compras`.`fechaentrega` AS `fechaentrega`,`compras`.`estado` AS `estado`,`compras`.`orden` AS `orden`,`compras`.`factura` AS `factura`,`compras`.`formapago` AS `formapago`,`compras`.`direccion_despacho` AS `direccion_despacho`,`compras`.`observacion` AS `observacion`,`compras`.`descuento` AS `descuento`,`compras`.`valor_gravado` AS `valor_gravado`,`compras`.`valor_excluido` AS `valor_excluido`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,`v_proveedor`.`nombre_contacto` AS `nombre_contacto`,`v_proveedor`.`direccion1` AS `direccion1`,`v_proveedor`.`direccion2` AS `direccion2`,`v_proveedor`.`direccion3` AS `direccion3`,`v_proveedor`.`telefono` AS `telefono`,`v_proveedor`.`celular` AS `celular`,`v_proveedor`.`email` AS `email`,`v_proveedor`.`banco_consignacion` AS `banco_consignacion`,`v_proveedor`.`banco_cuenta` AS `banco_cuenta`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`estado_orden`.`orden` AS `ordendisplay`,coalesce(`users`.`nombre`,'') AS `usuario`,`compras`.`anulada` AS `anulada`,`compras`.`fecha_anula` AS `fecha_anula`,`compras`.`observa_anula` AS `observa_anula`,`compras`.`userid_anula` AS `userid_anula` from (((`compras` join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `compras`.`proveedor_id`))) join `estado_orden` on((`estado_orden`.`estado` = convert(`compras`.`estado` using utf8mb4)))) left join `users` on((`users`.`user_id` = `compras`.`userid_confirma`))) order by `estado_orden`.`orden` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_compra_detalle`
--

/*!50001 DROP VIEW IF EXISTS `v_compra_detalle`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_compra_detalle` AS select `compras_detalle`.`compra_id` AS `compra_id`,`compras_detalle`.`compra_detalle_id` AS `compra_detalle_id`,`item`.`item_id` AS `item_id`,`item`.`codigo` AS `codigo_interno`,`item`.`descripcion_completa` AS `item_descripcion`,`compras_detalle`.`cantidad_pedida` AS `cantidad_pedida`,`compras_detalle`.`cantidad_recibida` AS `cantidad_recibida`,`compras_detalle`.`costo` AS `costo`,(`compras_detalle`.`costo` * `compras_detalle`.`cantidad_pedida`) AS `total`,`item`.`codcatalogoactivo` AS `codcatalogoactivo`,`item`.`descatalogoactivo` AS `descatalogoactivo`,`item`.`codcatalogogasto` AS `codcatalogogasto`,`item`.`descatalogogasto` AS `descatalogogasto` from (`compras_detalle` join `v_items` `item` on((`item`.`item_id` = `compras_detalle`.`item_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_compra_recepcion`
--

/*!50001 DROP VIEW IF EXISTS `v_compra_recepcion`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_compra_recepcion` AS select `v_compra_detalle`.`compra_id` AS `compra_id`,`v_compra_detalle`.`compra_detalle_id` AS `compra_detalle_id`,`v_compra_detalle`.`item_id` AS `item_id`,`v_compra_detalle`.`codigo_interno` AS `codigo_interno`,`v_compra_detalle`.`item_descripcion` AS `item_descripcion`,`v_compra_detalle`.`cantidad_pedida` AS `cantidad_pedida`,`v_compra_detalle`.`costo` AS `costo`,sum(coalesce(`v_recepcion_detalle`.`cantidad`,0)) AS `cantidad_recibida`,(`v_compra_detalle`.`cantidad_pedida` - sum(coalesce(`v_recepcion_detalle`.`cantidad`,0))) AS `diferencia`,`v_recepcion_detalle`.`recepcion_id` AS `recepcion_id`,`v_compra_detalle`.`total` AS `total`,`factura_recepcion`.`facturacompra_id` AS `facturacompra_id`,`v_compra_detalle`.`codcatalogoactivo` AS `codcatalogoactivo`,`v_compra_detalle`.`descatalogoactivo` AS `descatalogoactivo`,`v_compra_detalle`.`codcatalogogasto` AS `codcatalogogasto`,`v_compra_detalle`.`descatalogogasto` AS `descatalogogasto` from ((`v_compra_detalle` left join `v_recepcion_detalle` on((`v_recepcion_detalle`.`compra_detalle_id` = `v_compra_detalle`.`compra_detalle_id`))) left join `factura_recepcion` on((`factura_recepcion`.`recepcion_id` = `v_recepcion_detalle`.`recepcion_id`))) group by `v_compra_detalle`.`compra_id`,`v_compra_detalle`.`compra_detalle_id`,`v_compra_detalle`.`item_id`,`v_compra_detalle`.`codigo_interno`,`v_compra_detalle`.`item_descripcion`,`v_compra_detalle`.`cantidad_pedida`,`v_compra_detalle`.`costo`,`v_recepcion_detalle`.`recepcion_id`,`v_compra_detalle`.`total`,`factura_recepcion`.`facturacompra_id`,`v_compra_detalle`.`codcatalogoactivo`,`v_compra_detalle`.`descatalogoactivo`,`v_compra_detalle`.`codcatalogogasto`,`v_compra_detalle`.`descatalogogasto` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_compras_vacias`
--

/*!50001 DROP VIEW IF EXISTS `v_compras_vacias`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_compras_vacias` AS select `compras`.`compra_id` AS `compra_id` from (`compras` left join `compras_detalle` on((`compras`.`compra_id` = `compras_detalle`.`compra_id`))) where isnull(`compras_detalle`.`compra_id`) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_config`
--

/*!50001 DROP VIEW IF EXISTS `v_config`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_config` AS select `v_tercero`.`tercero_id` AS `tercero_id`,`v_tercero`.`codigo_documento` AS `codigo_documento`,`v_tercero`.`tipo_documento` AS `tipo_documento`,`v_tercero`.`identificacion` AS `identificacion`,`v_tercero`.`digito_verificacion` AS `digito_verificacion`,`v_tercero`.`apellido1` AS `apellido1`,`v_tercero`.`apellido2` AS `apellido2`,`v_tercero`.`nombre1` AS `nombre1`,`v_tercero`.`nombre2` AS `nombre2`,`v_tercero`.`razon_social1` AS `razon_social1`,`v_tercero`.`razon_social2` AS `razon_social2`,`v_tercero`.`direccion1` AS `direccion1`,`v_tercero`.`direccion2` AS `direccion2`,`v_tercero`.`codigo_regimen` AS `codigo_regimen`,`v_tercero`.`regimen` AS `regimen`,`v_tercero`.`codigo_persona` AS `codigo_persona`,`v_tercero`.`persona` AS `persona`,`v_tercero`.`codigo_municipio` AS `codigo_municipio`,`v_tercero`.`municipio` AS `municipio`,`v_tercero`.`codigo_departamento` AS `codigo_departamento`,`v_tercero`.`departamento` AS `departamento`,`v_tercero`.`codigo_pais` AS `codigo_pais`,`v_tercero`.`pais` AS `pais`,`v_tercero`.`nombre` AS `nombre_tercero`,`v_tercero`.`idennombre` AS `idennombre`,`config`.`config_id` AS `config_id`,`config`.`logo` AS `logo`,`config`.`consec_orden_pedido` AS `consec_orden_pedido`,`config`.`consec_mov_ent` AS `consec_mov_ent`,`config`.`consec_mov_sal` AS `consec_mov_sal`,`v_tercero`.`reteiva` AS `reteiva`,`v_tercero`.`retefuente` AS `retefuente`,`v_tercero`.`reteica` AS `reteica`,`config`.`verimagen` AS `verimagen`,`config`.`coditemauto` AS `coditemauto`,`config`.`consec_recepcion` AS `consec_recepcion`,`v_tercero`.`porcreteica` AS `porcreteica`,`config`.`telefono` AS `telefono`,`config`.`celular` AS `celular`,`config`.`email` AS `email`,`config`.`porcreteiva` AS `porcreteiva` from (`config` join `v_tercero`) where (`v_tercero`.`tercero_id` = -(1)) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_costo_recepcion`
--

/*!50001 DROP VIEW IF EXISTS `v_costo_recepcion`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_costo_recepcion` AS select `v_activos`.`recepcion_id` AS `recepcion_id`,if((`v_activos`.`contabiliza` = 1),`v_activos`.`codcatalogoactivo`,`v_activos`.`codcatalogogasto`) AS `codigo_cuenta`,if((`v_activos`.`contabiliza` = 1),`v_activos`.`descatalogoactivo`,`v_activos`.`descatalogogasto`) AS `cuenta`,sum(`v_activos`.`costo_activo`) AS `costo` from `v_activos` where (`v_activos`.`recepcion_id` is not null) group by `v_activos`.`recepcion_id`,`v_activos`.`contabiliza`,`v_activos`.`codcatalogoactivo`,`v_activos`.`codcatalogogasto`,`v_activos`.`descatalogoactivo`,`v_activos`.`descatalogogasto` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_cuentas`
--

/*!50001 DROP VIEW IF EXISTS `v_cuentas`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_cuentas` AS select `catalogo_contable`.`catalogo_id` AS `catalogo_id`,`catalogo_contable`.`idpadre` AS `idpadre`,`catalogo_contable`.`codigo` AS `codigo`,`catalogo_contable`.`descripcion` AS `descripcion`,`catalogo_contable`.`vidautil` AS `vidautil` from `catalogo_contable` where (length(`catalogo_contable`.`codigo`) = 4) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_dependencias`
--

/*!50001 DROP VIEW IF EXISTS `v_dependencias`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_dependencias` AS select `dependencias`.`dependencia_id` AS `dependencia_id`,concat(`dependencias`.`nombre`,' | ',`v_localizacion`.`municipio`,' - ',`v_localizacion`.`departamento`) AS `dependencia` from (`dependencias` join `v_localizacion` on((`dependencias`.`localizacion_id` = `v_localizacion`.`localizacion_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_factura_compra`
--

/*!50001 DROP VIEW IF EXISTS `v_factura_compra`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_factura_compra` AS select `factura_compra`.`facturacompra_id` AS `facturacompra_id`,if((`factura_compra`.`formapago` = 'R'),'CREDITO','CONTADO') AS `formapago`,`factura_compra`.`nrodocumento` AS `nrodocumento`,`factura_compra`.`nrofactura` AS `dcto`,`factura_compra`.`fechafactura` AS `fechadcto`,`factura_compra`.`fechavence` AS `fechavence`,`factura_compra`.`proveedor_id` AS `proveedor_id`,`v_proveedor`.`tipo_doc` AS `tipo_doc`,`v_proveedor`.`identificacion` AS `identificacion`,`v_proveedor`.`nombre_comercial` AS `nombre_comercial`,`v_proveedor`.`codigo_persona` AS `codigo_persona`,`v_proveedor`.`persona` AS `persona`,`v_proveedor`.`codigo_regimen` AS `codigo_regimen`,`v_proveedor`.`regimen` AS `regimen`,`v_proveedor`.`banco_consignacion` AS `banco_consignacion`,`v_proveedor`.`banco_cuenta` AS `banco_cuenta`,`factura_compra`.`vr_pagar` AS `vr_pagar`,`factura_compra`.`saldo` AS `saldo`,`factura_compra`.`subtotal` AS `subtotal`,`factura_compra`.`vr_excluido` AS `vr_excluido`,`factura_compra`.`vr_gravado` AS `vr_gravado`,`factura_compra`.`iva` AS `iva`,`factura_compra`.`vr_descuento` AS `vr_descuento`,`factura_compra`.`vr_excluido_otros` AS `vr_excluido_otros`,`factura_compra`.`vr_gravado_otros` AS `vr_gravado_otros`,`factura_compra`.`iva_otros` AS `iva_otros`,`factura_compra`.`retefuente` AS `retefuente`,`factura_compra`.`reteiva` AS `reteiva`,`factura_compra`.`reteica` AS `reteica`,`factura_compra`.`retefuente_ss` AS `retefuente_ss`,`factura_compra`.`reteiva_ss` AS `reteiva_ss`,`factura_compra`.`reteica_ss` AS `reteica_ss`,if((`factura_compra`.`saldo` > 0),'PENDIENTE','CANCELADO') AS `estado`,`factura_compra`.`anulada` AS `anulada`,coalesce(`users`.`nombre`,'') AS `usuario`,`factura_compra`.`generaplano` AS `generaplano` from ((`factura_compra` join `v_proveedor` on((`factura_compra`.`proveedor_id` = `v_proveedor`.`proveedor_id`))) left join `users` on((`users`.`user_id` = `factura_compra`.`userid_confirma`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_grupos`
--

/*!50001 DROP VIEW IF EXISTS `v_grupos`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_grupos` AS select `catalogo_contable`.`catalogo_id` AS `catalogo_id`,`catalogo_contable`.`idpadre` AS `idpadre`,`catalogo_contable`.`codigo` AS `codigo`,`catalogo_contable`.`descripcion` AS `descripcion`,`catalogo_contable`.`vidautil` AS `vidautil` from `catalogo_contable` where (length(`catalogo_contable`.`codigo`) = 2) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_items`
--

/*!50001 DROP VIEW IF EXISTS `v_items`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_items` AS select `items`.`item_id` AS `item_id`,`items`.`codigo` AS `codigo`,`items`.`descripcion` AS `descripcion`,`items`.`descripcion_adicional` AS `descripcion_adicional`,`items`.`tipo_item` AS `tipo_item`,`items`.`marca_id` AS `marca_id`,`items`.`subcategoria_id` AS `subcategoria_id`,`items`.`userid_create` AS `userid_create`,`items`.`userid_update` AS `userid_update`,`items`.`cantidad_stock` AS `cantidad_stock`,`items`.`stockmin` AS `stockmin`,`items`.`stockmax` AS `stockmax`,`items`.`costo` AS `costo`,`items`.`bloqueo` AS `bloqueo`,`items`.`fecha_ultima_compra` AS `fecha_ultima_compra`,`items`.`fecha_creacion` AS `fecha_creacion`,`items`.`costo_ultimo` AS `costo_ultimo`,`items`.`proveedor_id` AS `proveedor_id`,`marcas`.`nombre` AS `marca`,`subcategorias`.`codigo` AS `codsubcategoria`,`subcategorias`.`nombre` AS `subcategoria`,`categorias`.`categoria_id` AS `categoria_id`,`categorias`.`codigo` AS `codcategoria`,`categorias`.`nombre` AS `categoria`,`v_proveedor`.`display` AS `proveedor`,`items`.`valor_residual` AS `valor_residual`,`items`.`barcode` AS `barcode`,concat(`items`.`codigo`,' | ',`categorias`.`nombre`,' ',`subcategorias`.`nombre`,' ',`marcas`.`nombre`,' ',`items`.`descripcion`,' ',coalesce(`items`.`descripcion_adicional`,'')) AS `display`,`catalogo_activo`.`codigo` AS `codcatalogoactivo`,`catalogo_activo`.`descripcion` AS `descatalogoactivo`,`catalogo_gasto`.`codigo` AS `codcatalogogasto`,`catalogo_gasto`.`descripcion` AS `descatalogogasto`,coalesce(`catalogo_activo`.`vidautil`,0) AS `vidautil`,concat(`categorias`.`nombre`,' ',`subcategorias`.`nombre`,' ',`marcas`.`nombre`,' ',`items`.`descripcion`,' ',coalesce(`items`.`descripcion_adicional`,'')) AS `descripcion_completa` from ((((((`items` join `marcas` on((`marcas`.`marca_id` = `items`.`marca_id`))) join `subcategorias` on((`subcategorias`.`subcategoria_id` = `items`.`subcategoria_id`))) join `categorias` on((`categorias`.`categoria_id` = `subcategorias`.`categoria_id`))) left join `v_proveedor` on((`v_proveedor`.`proveedor_id` = `items`.`proveedor_id`))) left join `catalogo_contable` `catalogo_activo` on((`catalogo_activo`.`catalogo_id` = `items`.`activo_catalogo_id`))) left join `catalogo_contable` `catalogo_gasto` on((`catalogo_gasto`.`catalogo_id` = `items`.`gasto_catalogo_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_localizacion`
--

/*!50001 DROP VIEW IF EXISTS `v_localizacion`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_localizacion` AS select `localizacion`.`localizacion_id` AS `localizacion_id`,`localizacion`.`codigo` AS `codigo`,`localizacion`.`nombre` AS `nombre`,`localizacion`.`direccion` AS `direccion`,`localizacion`.`municipio_id` AS `municipio_id`,`localizacion`.`lat` AS `lat`,`localizacion`.`lng` AS `lng`,`municipios`.`codigo` AS `codigo_municipio`,`municipios`.`nombre` AS `municipio`,`municipios`.`departamento_id` AS `departamento_id`,`departamentos`.`codigo` AS `codigo_departamento`,`departamentos`.`nombre` AS `departamento` from ((`localizacion` join `municipios` on((`municipios`.`municipio_id` = `localizacion`.`municipio_id`))) join `departamentos` on((`departamentos`.`departamento_id` = `municipios`.`departamento_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_movinventario`
--

/*!50001 DROP VIEW IF EXISTS `v_movinventario`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_movinventario` AS select `movimientos_inventario`.`movinventario_id` AS `movinventario_id`,`movimientos_inventario`.`user_id` AS `user_id`,`movimientos_inventario`.`numero` AS `numero`,`tipos_ajuste`.`descripcion` AS `tipo_ajuste`,`tipos_ajuste`.`mvto` AS `mvto`,`documentos_contables`.`codigo` AS `codigo_dcto`,`documentos_contables`.`nombre` AS `nombre_dcto`,`movimientos_inventario`.`fechahora` AS `fechahora`,`movimientos_inventario`.`observacion` AS `observacion`,`movimientos_inventario`.`estado` AS `estado`,`v_tercero`.`identificacion` AS `iden_tercero`,`v_tercero`.`nombre` AS `nombre_tercero` from (((`movimientos_inventario` join `tipos_ajuste` on((`movimientos_inventario`.`tipoajuste_id` = `tipos_ajuste`.`tipoajuste_id`))) join `documentos_contables` on((`tipos_ajuste`.`documentocontable_id` = `documentos_contables`.`documentocontable_id`))) join `v_tercero` on((`movimientos_inventario`.`tercero_id` = `v_tercero`.`tercero_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_movinventario_vacios`
--

/*!50001 DROP VIEW IF EXISTS `v_movinventario_vacios`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_movinventario_vacios` AS select `movimientos_inventario`.`movinventario_id` AS `movinventario_id` from (`movimientos_inventario` left join `movinventario_detalle` on((`movimientos_inventario`.`movinventario_id` = `movinventario_detalle`.`movinventario_id`))) where isnull(`movinventario_detalle`.`movinventario_id`) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_proveedor`
--

/*!50001 DROP VIEW IF EXISTS `v_proveedor`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_proveedor` AS select `proveedores`.`proveedor_id` AS `proveedor_id`,`v_tercero`.`identificacion` AS `identificacion`,`v_tercero`.`tipo_documento` AS `tipo_doc`,concat(`proveedores`.`codigo`,' | ',`v_tercero`.`identificacion`,'  | ',`v_tercero`.`nombre`,'  | ',`proveedores`.`nombre_comercial`) AS `display`,`v_tercero`.`codigo_persona` AS `codigo_persona`,`v_tercero`.`persona` AS `persona`,`v_tercero`.`codigo_regimen` AS `codigo_regimen`,`v_tercero`.`regimen` AS `regimen`,`proveedores`.`nombre_comercial` AS `nombre_comercial`,`proveedores`.`nombre_contacto` AS `nombre_contacto`,`proveedores`.`direccion1` AS `direccion1`,`proveedores`.`direccion2` AS `direccion2`,`proveedores`.`direccion3` AS `direccion3`,`proveedores`.`telefono` AS `telefono`,`proveedores`.`celular` AS `celular`,`proveedores`.`email` AS `email`,`proveedores`.`banco_consignacion` AS `banco_consignacion`,`proveedores`.`banco_cuenta` AS `banco_cuenta`,`proveedores`.`activo` AS `activo`,`proveedores`.`dias_pago` AS `dias_pago`,`proveedores`.`precioiva` AS `precioiva`,`v_tercero`.`retefuente` AS `retefuente`,`v_tercero`.`reteiva` AS `reteiva`,`v_tercero`.`reteica` AS `reteica`,`v_tercero`.`base` AS `base`,`v_tercero`.`tarifa` AS `tarifa`,`v_tercero`.`porcreteica` AS `porcreteica` from (`proveedores` join `v_tercero` on((`v_tercero`.`tercero_id` = `proveedores`.`tercero_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_recepcion`
--

/*!50001 DROP VIEW IF EXISTS `v_recepcion`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_recepcion` AS select `recepciones`.`recepcion_id` AS `recepcion_id`,`recepciones`.`compra_id` AS `compra_id`,`recepciones`.`numero` AS `numero`,`recepciones`.`factura` AS `factura`,`recepciones`.`fecha` AS `fecha`,`recepciones`.`estado` AS `estado`,`recepciones`.`userid_confirma` AS `userid_confirma`,`v_compra`.`proveedor_id` AS `proveedor_id`,`v_compra`.`fechapedido` AS `fechapedido`,`v_compra`.`orden` AS `orden`,`v_compra`.`tipo_doc` AS `tipo_doc`,`v_compra`.`identificacion` AS `identificacion`,`v_compra`.`nombre_comercial` AS `nombre_comercial`,`recepciones`.`metodo` AS `metodo`,if(isnull(`factura_recepcion`.`facturarecepcion_id`),'NO','SI') AS `convertida_fac`,coalesce(`users`.`nombre`,'') AS `usuario`,`factura_recepcion`.`facturarecepcion_id` AS `facturarecepcion_id`,`recepciones`.`observacion` AS `observacion` from (((`recepciones` join `v_compra` on((`v_compra`.`compra_id` = `recepciones`.`compra_id`))) left join `factura_recepcion` on((`factura_recepcion`.`recepcion_id` = `recepciones`.`recepcion_id`))) left join `users` on((`users`.`user_id` = `recepciones`.`userid_confirma`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_recepcion_detalle`
--

/*!50001 DROP VIEW IF EXISTS `v_recepcion_detalle`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_recepcion_detalle` AS select `recepciones_detalle`.`recepcion_id` AS `recepcion_id`,`recepciones`.`numero` AS `numero`,`recepciones`.`factura` AS `factura`,`recepciones_detalle`.`recepcion_detalle_id` AS `recepcion_detalle_id`,`recepciones_detalle`.`compra_detalle_id` AS `compra_detalle_id`,`item`.`item_id` AS `item_id`,`item`.`codigo` AS `codigo_interno`,`item`.`descripcion_completa` AS `item_descripcion`,`compras_detalle`.`cantidad_pedida` AS `cantidad_pedida`,`compras_detalle`.`cantidad_recibida` AS `cantidad_recibida`,`recepciones_detalle`.`cantidad` AS `cantidad`,`recepciones_detalle`.`costo` AS `costo`,(`recepciones_detalle`.`costo` * `recepciones_detalle`.`cantidad`) AS `total`,`recepciones_detalle`.`observacion` AS `observacion`,`compras_detalle`.`compra_id` AS `compra_id`,`recepciones`.`estado` AS `estado` from (((`recepciones_detalle` join `compras_detalle` on((`compras_detalle`.`compra_detalle_id` = `recepciones_detalle`.`compra_detalle_id`))) join `v_items` `item` on((`item`.`item_id` = `compras_detalle`.`item_id`))) join `recepciones` on((`recepciones`.`recepcion_id` = `recepciones_detalle`.`recepcion_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_recepciones_vacias`
--

/*!50001 DROP VIEW IF EXISTS `v_recepciones_vacias`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_recepciones_vacias` AS select `recepciones`.`recepcion_id` AS `recepcion_id` from (`recepciones` left join `recepciones_detalle` on((`recepciones`.`recepcion_id` = `recepciones_detalle`.`recepcion_id`))) where isnull(`recepciones_detalle`.`recepcion_id`) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_responsables`
--

/*!50001 DROP VIEW IF EXISTS `v_responsables`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_responsables` AS select `responsables`.`responsable_id` AS `responsable_id`,`responsables`.`identificacion` AS `identificacion`,`responsables`.`nombre` AS `nombre`,`jobs_title`.`description` AS `cargo`,`responsables`.`fecha_caducidad` AS `fecha_caducidad` from (`responsables` join `jobs_title` on((`jobs_title`.`id` = `responsables`.`job_title_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_subcuentas`
--

/*!50001 DROP VIEW IF EXISTS `v_subcuentas`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_subcuentas` AS select `catalogo_contable`.`catalogo_id` AS `catalogo_id`,`catalogo_contable`.`idpadre` AS `idpadre`,`catalogo_contable`.`codigo` AS `codigo`,`catalogo_contable`.`descripcion` AS `descripcion`,`catalogo_contable`.`vidautil` AS `vidautil` from `catalogo_contable` where (length(`catalogo_contable`.`codigo`) = 6) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_tercero`
--

/*!50001 DROP VIEW IF EXISTS `v_tercero`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_tercero` AS select `terceros`.`tercero_id` AS `tercero_id`,`tipos_documento`.`codigo` AS `codigo_documento`,`tipos_documento`.`nombre` AS `tipo_documento`,`terceros`.`identificacion` AS `identificacion`,`terceros`.`digito_verificacion` AS `digito_verificacion`,`terceros`.`apellido1` AS `apellido1`,`terceros`.`apellido2` AS `apellido2`,`terceros`.`nombre1` AS `nombre1`,`terceros`.`nombre2` AS `nombre2`,`terceros`.`razon_social1` AS `razon_social1`,`terceros`.`razon_social2` AS `razon_social2`,`terceros`.`direccion1` AS `direccion1`,`terceros`.`direccion2` AS `direccion2`,`tipos_regimen`.`codigo` AS `codigo_regimen`,`tipos_regimen`.`descripcion` AS `regimen`,`tipos_persona`.`codigo` AS `codigo_persona`,`tipos_persona`.`descripcion` AS `persona`,`municipios`.`codigo` AS `codigo_municipio`,`municipios`.`nombre` AS `municipio`,`departamentos`.`codigo` AS `codigo_departamento`,`departamentos`.`nombre` AS `departamento`,`paises`.`codigo` AS `codigo_pais`,`paises`.`nombre` AS `pais`,if((`terceros`.`tipopersona_id` = 2),concat(`terceros`.`razon_social1`,' ',coalesce(`terceros`.`razon_social2`,'')),concat(`terceros`.`apellido1`,' ',coalesce(`terceros`.`apellido2`,''),' ',`terceros`.`nombre1`,' ',coalesce(`terceros`.`nombre2`,''))) AS `nombre`,concat(`terceros`.`identificacion`,' | ',if((`terceros`.`tipopersona_id` = 2),concat(`terceros`.`razon_social1`,' ',coalesce(`terceros`.`razon_social2`,'')),concat(`terceros`.`apellido1`,' ',coalesce(`terceros`.`apellido2`,''),' ',`terceros`.`nombre1`,' ',coalesce(`terceros`.`nombre2`,'')))) AS `idennombre`,`v_tipotercero_pivot`.`C` AS `C`,`v_tipotercero_pivot`.`P` AS `P`,`terceros`.`reteiva` AS `reteiva`,`terceros`.`retefuente` AS `retefuente`,`terceros`.`reteica` AS `reteica`,`terceros`.`porcreteica` AS `porcreteica`,`retefuente`.`base` AS `base`,`retefuente`.`tarifa` AS `tarifa` from ((((((((`terceros` join `tipos_documento` on((`tipos_documento`.`tipodocumento_id` = `terceros`.`tipodocumento_id`))) join `tipos_regimen` on((`tipos_regimen`.`tiporegimen_id` = `terceros`.`tiporegimen_id`))) join `tipos_persona` on((`tipos_persona`.`tipopersona_id` = `terceros`.`tipopersona_id`))) join `municipios` on((`municipios`.`municipio_id` = `terceros`.`municipio_id`))) join `departamentos` on((`departamentos`.`departamento_id` = `municipios`.`departamento_id`))) join `paises` on((`paises`.`pais_id` = `terceros`.`pais_id`))) left join `retefuente` on((`retefuente`.`retefte_id` = `terceros`.`retefte_id`))) left join `v_tipotercero_pivot` on((`v_tipotercero_pivot`.`tercero_id` = `terceros`.`tercero_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_tipotercero`
--

/*!50001 DROP VIEW IF EXISTS `v_tipotercero`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_tipotercero` AS select distinct `clientes`.`tercero_id` AS `tercero_id`,'C' AS `tipo` from `clientes` union select distinct `proveedores`.`tercero_id` AS `tercero_id`,'P' AS `tipo` from `proveedores` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_tipotercero_pivot`
--

/*!50001 DROP VIEW IF EXISTS `v_tipotercero_pivot`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_tipotercero_pivot` AS select `t1`.`tercero_id` AS `tercero_id`,(select 1 AS `aplica` from `v_tipotercero` where ((`v_tipotercero`.`tipo` = 'C') and (`v_tipotercero`.`tercero_id` = `t1`.`tercero_id`))) AS `C`,(select 1 AS `aplica` from `v_tipotercero` where ((`v_tipotercero`.`tipo` = 'P') and (`v_tipotercero`.`tercero_id` = `t1`.`tercero_id`))) AS `P` from `v_tipotercero` `t1` group by `t1`.`tercero_id` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_total_recepciones`
--

/*!50001 DROP VIEW IF EXISTS `v_total_recepciones`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8mb4 */;
/*!50001 SET character_set_results     = utf8mb4 */;
/*!50001 SET collation_connection      = utf8mb4_0900_ai_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`sistemas`@`%` SQL SECURITY DEFINER */
/*!50001 VIEW `v_total_recepciones` AS select `compras`.`orden` AS `orden`,`v_recepcion_detalle`.`numero` AS `numero`,`v_recepcion_detalle`.`factura` AS `factura`,`v_recepcion_detalle`.`recepcion_id` AS `recepcion_id`,`compras`.`proveedor_id` AS `proveedor_id`,`factura_recepcion`.`facturarecepcion_id` AS `facturarecepcion_id`,`factura_recepcion`.`facturacompra_id` AS `facturacompra_id`,count(`v_recepcion_detalle`.`item_id`) AS `cantprod`,sum(`v_recepcion_detalle`.`total`) AS `total` from ((`v_recepcion_detalle` join `compras` on((`compras`.`compra_id` = `v_recepcion_detalle`.`compra_id`))) left join `factura_recepcion` on((`factura_recepcion`.`recepcion_id` = `v_recepcion_detalle`.`recepcion_id`))) where (`v_recepcion_detalle`.`estado` = 1) group by `compras`.`orden`,`v_recepcion_detalle`.`numero`,`v_recepcion_detalle`.`factura`,`v_recepcion_detalle`.`recepcion_id`,`compras`.`proveedor_id`,`factura_recepcion`.`facturarecepcion_id`,`factura_recepcion`.`facturacompra_id` */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_usersmenus`
--

/*!50001 DROP VIEW IF EXISTS `v_usersmenus`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_usersmenus` AS select distinct `m`.`menu_id` AS `menu_id`,`m`.`orden` AS `orden`,`m`.`titulo` AS `titulo`,`m`.`icono` AS `icono`,`u`.`user_id` AS `user_id`,`u`.`nombre` AS `usuario_nombre` from ((((`menus` `m` join `submenus` on((`m`.`menu_id` = `submenus`.`menu_id`))) join `submenus_roles` on((`submenus`.`submenu_id` = `submenus_roles`.`submenu_id`))) join `users_roles` on((`users_roles`.`role_id` = `submenus_roles`.`role_id`))) join `users` `u` on((`u`.`user_id` = `users_roles`.`user_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;

--
-- Final view structure for view `v_usersubmenu`
--

/*!50001 DROP VIEW IF EXISTS `v_usersubmenu`*/;
/*!50001 SET @saved_cs_client          = @@character_set_client */;
/*!50001 SET @saved_cs_results         = @@character_set_results */;
/*!50001 SET @saved_col_connection     = @@collation_connection */;
/*!50001 SET character_set_client      = utf8 */;
/*!50001 SET character_set_results     = utf8 */;
/*!50001 SET collation_connection      = utf8_general_ci */;
/*!50001 CREATE ALGORITHM=UNDEFINED */
/*!50013 DEFINER=`root`@`localhost` SQL SECURITY DEFINER */
/*!50001 VIEW `v_usersubmenu` AS select distinct `s`.`submenu_id` AS `submenu_id`,`m`.`menu_id` AS `menu_id`,`s`.`orden` AS `orden`,`s`.`titulo` AS `titulo`,`s`.`url` AS `url`,`u`.`user_id` AS `user_id`,`u`.`nombre` AS `usuario_nombre`,`s`.`ab` AS `ab` from ((((`submenus` `s` join `menus` `m` on((`m`.`menu_id` = `s`.`menu_id`))) join `submenus_roles` on((`s`.`submenu_id` = `submenus_roles`.`submenu_id`))) join `users_roles` on((`users_roles`.`role_id` = `submenus_roles`.`role_id`))) join `users` `u` on((`u`.`user_id` = `users_roles`.`user_id`))) */;
/*!50001 SET character_set_client      = @saved_cs_client */;
/*!50001 SET character_set_results     = @saved_cs_results */;
/*!50001 SET collation_connection      = @saved_col_connection */;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2026-09-07 10:53:17
