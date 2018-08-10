-- MySQL dump 10.16  Distrib 10.1.29-MariaDB, for debian-linux-gnu (x86_64)
--
-- Host: localhost    Database: paeents
-- ------------------------------------------------------
-- Server version	10.1.29-MariaDB-6

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `PAEENTS_PRODUCT`
--

DROP TABLE IF EXISTS `PAEENTS_PRODUCT`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `PAEENTS_PRODUCT` (
  `PRODUCT_ID` char(32) NOT NULL,
  `PRODUCT_NAME` varchar(20) NOT NULL,
  `PRODUCT_CATEGORY` varchar(255) NOT NULL,
  `PRODUCT_PHOTO` varchar(100) NOT NULL,
  `PRODUCT_COUNT` int(11) DEFAULT NULL,
  `PRODUCT_THUMBNAIL` varchar(100) NOT NULL,
  `PRODUCT_PRICE` int(11) NOT NULL,
  `PRODUCT_ORDER` int(11) NOT NULL,
  `PRODUCT_COLOR` varchar(10) NOT NULL,
  `PRODUCT_SIZE` varchar(12) NOT NULL,
  `PRODUCT_INTRODUCTION` text NOT NULL,
  `PRODUCT_CREATE_TIME` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`PRODUCT_ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `PAEENTS_PRODUCT`
--

LOCK TABLES `PAEENTS_PRODUCT` WRITE;
/*!40000 ALTER TABLE `PAEENTS_PRODUCT` DISABLE KEYS */;
INSERT INTO `PAEENTS_PRODUCT` VALUES ('hfFRCo3Ce7xfKmLlS83BHpdysYVugYCJ','燕麦','vNK6QckQbjYTWafX','http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/a9b0cd25303440f584b8f80533b4702f.png',2100,'http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/2066b924956f44ab86ef9622b3c60303.png',5000,125,'#AAAACC','1222','121','2018-07-24 01:40:31'),('kbs02g0PYj6fjqXZruWrNzSly4PYbEB0','奶粉','vNK6QckQbjYTWafX','http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/02e497a9292045c3b79e42b653ad65ac.png',1900,'http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/8d1d9d0c53ec47a3a6b528b8bacdab4b.png',200,125,'阿达','大大','达到','2018-07-24 01:42:16'),('oDcBaCL1wQJsXtpMdwljqbrnb0I9fUkb','相机','cqcUvhqauRHd1qWX','http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/b8af9ad6f380418d95e73159bd28fb6d.png',20,'http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/a91723039610429e8c8e6b414049ae23.png',2000,12,'156','115','12','2018-07-24 01:29:52'),('w6FEntRTaKoLrdSpl6eJZIpe5I9upvW8','护肤品','vNK6QckQbjYTWafX','http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/25bb9742a96444fda2ec5e2413b1c9d6.png',2100,'http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/c53c214f680c47c5b395bc29fa0f0214.png',500,1501,'1561','1115','121','2018-07-24 01:38:50'),('wyoiDZfd6AYVTU45LNNieP8OjZPeOMk5','饮料','cqcUvhqauRHd1qWX','http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/8f7f9501a2cc45e7a3202d2b34bdcf44.png',200,'http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/8816586c0f39468f9590421b896ff22f.png',1020,15,'156','115','12','2018-07-24 01:45:01'),('yTnog6GAncyuQCnDOkMEFTrKBCjr7qVk','帽子','cqcUvhqauRHd1qWX','http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/08c05b59c03549f1b3ec6edc3de76cbe.png',200,'http://paeents.oss-cn-shanghai.aliyuncs.com/20180724/83bd061646174277b6c5f7e3939f23e6.png',500,150,'156','115','12','2018-07-24 01:35:18');
/*!40000 ALTER TABLE `PAEENTS_PRODUCT` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2018-07-24  9:59:03

-- drop create update select
