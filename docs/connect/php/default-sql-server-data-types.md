---
title: Types de données SQL Server par défaut | Microsoft Docs
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
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c138e7eb5d2c4f6dbace0db59ce235e1c0a5f9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993661"
---
# <a name="default-sql-server-data-types"></a>Types de données SQL Server par défaut
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lors de l’envoi de données au serveur, le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convertit les données de leur type de données PHP vers un type de données SQL Server si aucun type de données SQL Server n’a été spécifié par l’utilisateur. Le tableau suivant indique le type de données PHP (type de données envoyé au serveur) et le type de données SQL Server par défaut (type de données vers lequel les données sont converties). Pour plus d’informations sur la spécification des types de données durant l’envoi de données au serveur, consultez [Procédure : spécifier des types de données SQL Server quand vous utilisez le pilote SQLSRV](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|Type de données PHP|Type SQL Server par défaut dans le pilote SQLSRV|Type SQL Server par défaut dans le pilote PDO_SQLSRV|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|non pris en charge|  
|Boolean|bit|bit|  
|Integer|int|int|  
|Float|float(24)|non pris en charge|  
|String (longueur inférieure à 8000 octets)|varchar(<string length>)|varchar(<string length>)|  
|String (longueur supérieure à 8000 octets)|varchar(max)|varchar(max)|  
|Ressource|Non pris en charge.|Non pris en charge.|  
|Flux (encodage : non binaire)|varchar(max)|varchar(max)|  
|Flux (encodage : binaire)|varbinary|varbinary|  
|Array|Non pris en charge.|Non pris en charge.|  
|Object|Non pris en charge.|Non pris en charge.|  
|DateTime (1)|DATETIME|Non pris en charge.|  
  
## <a name="see-also"></a>Voir aussi  
[Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Conversion de types de données](../../connect/php/converting-data-types.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)

[Types PHP](https://php.net/manual/language.types.php)

[Types de données (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/data-types/data-types-transact-sql)  
  
