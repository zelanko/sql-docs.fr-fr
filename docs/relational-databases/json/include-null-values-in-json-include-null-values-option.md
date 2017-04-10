---
title: "Inclure des valeurs&#160;Null dans une sortie&#160;JSON avec l’option INCLUDE_NULL_VALUES (SQL&#160;Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "INCLUDE_NULL_VALUES (POUR JSON)"
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 13
---
# Inclure des valeurs&#160;Null dans une sortie&#160;JSON avec l’option INCLUDE_NULL_VALUES (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Pour inclure des valeurs Null dans la sortie JSON de la clause **FOR JSON**, indiquez l’option **INCLUDE_NULL_VALUES**.  
  
 Si vous ne spécifiez pas l’option **INCLUDE_NULL_VALUES**, la sortie JSON n’inclut pas les propriétés des valeurs Null dans les résultats de la requête.  
  
## Exemples  
 L’exemple suivant montre la sortie de la clause **FOR JSON** avec et sans l’option **INCLUDE_NULL_VALUES**.  
  
|Sans l’option **INCLUDE_NULL_VALUES**|Avec l’option **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Voici un autre exemple de clause **FOR JSON** avec l’option **INCLUDE_NULL_VALUES**.  
  
 **Requête**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES  
```  
  
 **Résultat**  
  
```json  
[   
   {"name": "John",  "surname": null },  
   {"name": "Jane",  "surname": "Doe"}  
]  
```  
  
## Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  