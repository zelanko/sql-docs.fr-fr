---
title: Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: douglasl
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2350dc80c5223d6809ce13db5fea2af293e70744
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110133"
---
# <a name="include-null-values-in-json---includenullvalues-option"></a>Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
  
 **Result**  
  
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
  
### <a name="microsoft-blog-posts"></a>Billets de blog Microsoft  
  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez ces [billets de blog](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) sur la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database.  

### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour obtenir une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez les vidéos suivantes :

-   [SQL Server 2016 et prise en charge de JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Utilisation de JSON dans SQL Server 2016 et Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON : un pont entre les mondes relationnel et NoSQL](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)

## <a name="see-also"></a> Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
