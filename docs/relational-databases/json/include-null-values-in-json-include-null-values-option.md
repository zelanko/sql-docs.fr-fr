---
title: "Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 2cdb047169569041e3a8f7890d8215fd87284959
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="include-null-values-in-json---includenullvalues-option"></a>Inclure des valeurs Null dans l’option JSON - INCLUDE_NULL_VALUES
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.  

## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

