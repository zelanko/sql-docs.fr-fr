---
title: "Types de données PHP par défaut | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2db2186adfe8fc12a80c1459a0e5b768dfd9fe45
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="default-php-data-types"></a>Types de données PHP par défaut
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lors de la récupération des données à partir du serveur, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convertit les données en un type de données PHP par défaut si aucun type de données PHP n’a été spécifié par l’utilisateur.  
  
Quand les données sont retournées à l’aide du pilote PDO_SQLSRV, le type de données est soit int, soit string.  
  
Le reste de cette rubrique traite des types de données par défaut qui utilisent le pilote SQLSRV.  
  
Le tableau suivant répertorie le type de données SQL Server (type des données récupérées à partir du serveur), le type de données PHP par défaut (type de données vers lequel les données sont converties) et l’encodage par défaut pour les flux et les chaînes. Pour plus d’informations sur la manière de spécifier des types de données lors de la récupération de données à partir du serveur, consultez [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
|Type SQL Server|Type PHP par défaut|Encodage par défaut|  
|-------------------|--------------------|--------------------|  
|bigint|Chaîne|caractère 8 bits<sup>1</sup>|  
|binary|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|bit|Entier|caractère 8 bits<sup>1</sup>|  
|char|Chaîne|caractère 8 bits<sup>1</sup>|  
|date<sup>4</sup>|DateTime|Non applicable|  
|DateTime<sup>4</sup>|DateTime|Non applicable|  
|datetime2<sup>4</sup>|DateTime|Non applicable|  
|datetimeoffset<sup>4</sup>|DateTime|Non applicable|  
|decimal|Chaîne|caractère 8 bits<sup>1</sup>|  
|float|Float|caractère 8 bits<sup>1</sup>|  
|geography|Flux|Binaire<sup>3</sup>|  
|geometry|Flux|Binaire<sup>3</sup>|  
|image<sup>5</sup>|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|int|Entier|caractère 8 bits<sup>1</sup>|  
|money|Chaîne|caractère 8 bits<sup>1</sup>|  
|nchar|Chaîne|caractère 8 bits<sup>1</sup>|  
|numeric|Chaîne|caractère 8 bits<sup>1</sup>|  
|nvarchar|Chaîne|caractère 8 bits<sup>1</sup>|  
|nvarchar(MAX)|Flux<sup>2</sup>|caractère 8 bits<sup>1</sup>|  
|ntext<sup>6</sup>|Flux<sup>2</sup>|caractère 8 bits<sup>1</sup>|  
|real|Float|caractère 8 bits<sup>1</sup>|  
|smalldatetime|DateTime|caractère 8 bits<sup>1</sup>|  
|smallint|Entier|caractère 8 bits<sup>1</sup>|  
|smallmoney|Chaîne|caractère 8 bits<sup>1</sup>|  
|sql_variant<sup>7</sup>|Chaîne|caractère 8 bits<sup>1</sup>|  
|texte<sup>8</sup>|Flux<sup>2</sup>|caractère 8 bits<sup>1</sup>|  
|time<sup>4</sup>|DateTime|Non applicable|  
|timestamp|Chaîne|caractère 8 bits<sup>1</sup>|  
|tinyint|Entier|caractère 8 bits<sup>1</sup>|  
|UDT|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|uniqueidentifier|Chaîne<sup>9</sup>|caractère 8 bits<sup>1</sup>|  
|varbinary|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|varbinary(MAX)|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|varchar|Chaîne|caractère 8 bits<sup>1</sup>|  
|varchar(MAX)|Flux<sup>2</sup>|caractère 8 bits<sup>1</sup>|
|xml|Flux<sup>2</sup>|caractère 8 bits<sup>1</sup>|  
  

1.  Les données sont retournées sous forme de caractères 8 bits comme spécifié dans la page de codes des paramètres régionaux Windows définis sur le système. Les caractères multioctets ou les caractères non mappés dans cette page de codes sont remplacés par un point d’interrogation (?) à un octet.  
  
2.  Si [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) ou [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) est utilisé pour récupérer des données dont le type PHP par défaut est Flux, les données sont retournées sous la forme d’une chaîne avec le même encodage que le flux. Par exemple, si un type binaire SQL Server est récupéré à l’aide de **sqlsrv_fetch_array**, le type de retour par défaut est une chaîne binaire.  
  
3.  Les données sont retournées à partir du serveur sous la forme d’un flux d’octets bruts sans encodage ni traduction.  

4.  Les types de date et d’heure peuvent être récupérés sous forme de chaînes. Pour plus d’informations, consultez [Procédure : récupérer des types de date et heure sous forme de chaînes à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Il s’agit d’un type hérité mappé sur le type varbinary(max).

6. Il s’agit d’un type hérité mappé sur le type nvarchar(max).

7.  sql_variant n’est pas pris en charge dans les paramètres bidirectionnel ou de sortie.

8.  Il s’agit d’un type hérité mappé sur le type varchar(max).  
  
9.  Les UNIQUEIDENTIFIER sont des GUID représentés par l’expression régulière suivante :  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>Autres nouveaux types et fonctionnalités SQL Server 2008  
Types de données qui sont nouveaux dans SQL Server 2008 et qui existent en dehors des colonnes (tels que les paramètres table) ne sont pas pris en charge dans le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Le tableau ci-dessous résume la prise en charge PHP pour les nouvelles fonctionnalités SQL Server 2008.  
  
|Fonctionnalité|Prise en charge PHP|  
|-----------|---------------|  
|Paramètre table|Non|  
|Colonnes éparses|Partielle|  
|Compression de bits Null|Oui|  
|Types CLR volumineux définis par l’utilisateur (UDT)|Oui|  
|Nom de principal du service|Non|  
|MERGE|Oui|  
|FILESTREAM|Partielle|  
  
Une prise en charge partielle des types signifie que vous ne pouvez pas interroger par programme le type de la colonne.  
  
## <a name="see-also"></a>Voir aussi  
[Constantes &#40;pilotes Microsoft SQL Server pour PHP&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[Types PHP](http://go.microsoft.com/fwlink/?LinkId=109071)  
[Types de données (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  

