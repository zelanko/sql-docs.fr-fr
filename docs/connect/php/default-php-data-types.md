---
title: Types de données PHP par défaut | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3f5210d54fdd5a0a693f9cb7fdf8a7d4fc0f183
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928027"
---
# <a name="default-php-data-types"></a>Types de données PHP par défaut
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lors de la récupération des données à partir du serveur, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convertit les données en un type de données PHP par défaut si aucun type de données PHP n’a été spécifié par l’utilisateur.  
  
Quand les données sont retournées à l’aide du pilote PDO_SQLSRV, le type de données est soit int, soit string.  
  
Le reste de cette rubrique traite des types de données par défaut qui utilisent le pilote SQLSRV.  
  
Le tableau suivant répertorie le type de données SQL Server (type des données récupérées à partir du serveur), le type de données PHP par défaut (type de données vers lequel les données sont converties) et l’encodage par défaut pour les flux et les chaînes. Pour savoir comment spécifier des types de données en récupérant des données du serveur, consultez [Guide pratique pour spécifier des types de données PHP](../../connect/php/how-to-specify-php-data-types.md).  
  
|Type SQL Server|Type PHP par défaut|Encodage par défaut|  
|-------------------|--------------------|--------------------|  
|bigint|String|Caractère 8 bits<sup>1</sup>|  
|binary|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|bit|Integer|Caractère 8 bits<sup>1</sup>|  
|char|String|Caractère 8 bits<sup>1</sup>|  
|date<sup>4</sup>|Datetime|Non applicable|  
|datetime<sup>4</sup>|Datetime|Non applicable|  
|datetime2<sup>4</sup>|Datetime|Non applicable|  
|datetimeoffset<sup>4</sup>|Datetime|Non applicable|  
|Décimal|String|Caractère 8 bits<sup>1</sup>|  
|float|Float|Caractère 8 bits<sup>1</sup>|  
|Geography|Flux|Binaire<sup>3</sup>|  
|geometry|Flux|Binaire<sup>3</sup>|  
|image<sup>5</sup>|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|int|Integer|Caractère 8 bits<sup>1</sup>|  
|money|String|Caractère 8 bits<sup>1</sup>|  
|NCHAR|String|Caractère 8 bits<sup>1</sup>|  
|numeric|String|Caractère 8 bits<sup>1</sup>|  
|NVARCHAR|String|Caractère 8 bits<sup>1</sup>|  
|nvarchar(MAX)|Flux<sup>2</sup>|Caractère 8 bits<sup>1</sup>|  
|ntext<sup>6</sup>|Flux<sup>2</sup>|Caractère 8 bits<sup>1</sup>|  
|real|Float|Caractère 8 bits<sup>1</sup>|  
|smalldatetime|Datetime|Caractère 8 bits<sup>1</sup>|  
|SMALLINT|Integer|Caractère 8 bits<sup>1</sup>|  
|SMALLMONEY|String|Caractère 8 bits<sup>1</sup>|  
|sql_variant<sup>7</sup>|String|Caractère 8 bits<sup>1</sup>|  
|text<sup>8</sup>|Flux<sup>2</sup>|Caractère 8 bits<sup>1</sup>|  
|time<sup>4</sup>|Datetime|Non applicable|  
|timestamp|String|Caractère 8 bits<sup>1</sup>|  
|TINYINT|Integer|Caractère 8 bits<sup>1</sup>|  
|UDT|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|UNIQUEIDENTIFIER|Chaîne<sup>9</sup>|Caractère 8 bits<sup>1</sup>|  
|varbinary|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|varbinary(MAX)|Flux<sup>2</sup>|Binaire<sup>3</sup>|  
|varchar|String|Caractère 8 bits<sup>1</sup>|  
|varchar(MAX)|Flux<sup>2</sup>|Caractère 8 bits<sup>1</sup>|
|Xml|Flux<sup>2</sup>|Caractère 8 bits<sup>1</sup>|  
  

1.  Les données sont retournées sous forme de caractères 8 bits comme spécifié dans la page de codes des paramètres régionaux Windows définis sur le système. Les caractères multioctets ou les caractères non mappés dans cette page de codes sont remplacés par un point d’interrogation (?) à un octet.  
  
2.  Si [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) ou [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) est utilisé pour récupérer des données dont le type PHP par défaut est Flux, les données sont retournées sous la forme d’une chaîne avec le même encodage que le flux. Par exemple, si un type binaire SQL Server est récupéré à l’aide de **sqlsrv_fetch_array**, le type de retour par défaut est une chaîne binaire.  
  
3.  Les données sont retournées à partir du serveur sous la forme d’un flux d’octets bruts sans encodage ni traduction.  

4.  Les types de date et d’heure peuvent être récupérés sous forme de chaînes. Pour plus d’informations, consultez [Procédure : Récupérer des types date et heure sous forme de chaînes à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Il s’agit d’un type hérité mappé sur le type varbinary(max).

6. Il s’agit d’un type hérité mappé sur le type nvarchar(max).

7.  sql_variant n’est pas pris en charge dans les paramètres de sortie ni bidirectionnels.

8.  Il s’agit d’un type hérité mappé sur le type varchar(max).  
  
9.  Les UNIQUEIDENTIFIER sont des GUID représentés par l’expression régulière suivante :  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>Autres nouveaux types et fonctionnalités SQL Server 2008  
Les types de données qui sont nouveaux dans SQL Server 2008 et qui existent en dehors des colonnes (par exemple, les paramètres table) ne sont pas pris en charge dans [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Le tableau suivant résume la prise en charge PHP pour les nouvelles fonctionnalités SQL Server 2008.  
  
|Fonctionnalité|Prise en charge PHP|  
|-----------|---------------|  
|Paramètre table|Non|  
|Colonnes éparses|Partiel|  
|Compression de bits Null|Oui|  
|Types CLR volumineux définis par l’utilisateur (UDT)|Oui|  
|Nom de principal du service|Non|  
|MERGE|Oui|  
|FILESTREAM|Partiel|  
  
Une prise en charge partielle des types signifie que vous ne pouvez pas interroger par programme le type de la colonne.  
  
## <a name="see-also"></a>Voir aussi  
[Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Conversion de types de données](../../connect/php/converting-data-types.md)

[Types PHP](https://php.net/manual/en/language.types.php)

[Types de données (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
