---
description: Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES
title: Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 400b6f6198f44cb48c533c27c324fe78d13aa324
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483391"
---
# <a name="include-null-values-in-json---include_null_values-option"></a>Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sqlserver2016-asdb.md)]

  Pour inclure des valeurs Null dans la sortie JSON de la clause **FOR JSON** , indiquez l’option **INCLUDE_NULL_VALUES** .  
  
 Si vous ne spécifiez pas l’option **INCLUDE_NULL_VALUES** , la sortie JSON n’inclut pas les propriétés des valeurs Null dans les résultats de la requête.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre la sortie de la clause **FOR JSON** avec et sans l’option **INCLUDE_NULL_VALUES** .  
  
|Sans l’option **INCLUDE_NULL_VALUES**|Avec l’option **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Voici un autre exemple de clause **FOR JSON** avec l’option **INCLUDE_NULL_VALUES** .  
  
 **Requête**  
  
```sql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES    
```  
  
 **Résultat**  
  
```json  
[{
    "name": "John",
    "surname": null
}, {
    "name": "Jane",
    "surname": "Doe"
}] 
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>En savoir plus sur JSON dans SQL Server et Azure SQL Database  
  
### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour obtenir une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez les vidéos suivantes :

-   [SQL Server 2016 et prise en charge de JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Utilisation de JSON dans SQL Server 2016 et Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON : un pont entre les mondes relationnel et NoSQL](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)

## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
