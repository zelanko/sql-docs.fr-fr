---
title: Supprimer les crochets de JSON - Option WITHOUT_ARRAY_WRAPPER | Microsoft Docs
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
- WITHOUT_ARRAY_WRAPPER
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 36e612b6c3759d968687d8ba35286c399de02a74
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="remove-square-brackets-from-json---withoutarraywrapper-option"></a>Supprimer les crochets de JSON - Option WITHOUT_ARRAY_WRAPPER
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Pour supprimer les crochets qui entourent par défaut la sortie JSON de la clause **FOR JSON** , spécifiez l’option **WITHOUT_ARRAY_WRAPPER** . Utilisez cette option avec les résultats d’une ligne unique pour générer un seul objet JSON en tant que sortie plutôt qu’un tableau avec un seul élément.

Si vous utilisez cette option avec un résultat de plusieurs lignes, le résultat n’est pas un JSON valide en raison de plusieurs éléments et les crochets manquants.  
  
## <a name="example-single-row-result"></a>Exemple (résultats à ligne unique)  
L’exemple suivant montre la sortie de la clause **FOR JSON** avec et sans l’option **WITHOUT_ARRAY_WRAPPER** .  
  
 **Requête**  
  
```sql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  

 **Résultat** avec l’option **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{
    "year": 2015,
    "month": 12,
    "day": 15
} 
```  
  
 **Résultat** (par défaut) sans le **WITHOUT_ARRAY_WRAPPER** option  
  
```json  
[{
    "year": 2015,
    "month": 12,
    "day": 15
}]
```  

## <a name="example-multiple-row-result"></a>Exemple (plusieurs lignes de résultat)
Voici un autre exemple de clause **FOR JSON** avec et sans l’option **WITHOUT_ARRAY_WRAPPER** . Cet exemple produit un résultat de plusieurs lignes. La sortie n’est pas un JSON valide en raison de plusieurs éléments et les crochets manquants.
  
 **Requête**  
  
```sql  
SELECT TOP 3 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  
  
 **Résultat** avec l’option **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
} 
```  
  
 **Résultat** (par défaut) sans le **WITHOUT_ARRAY_WRAPPER** option  
  
```json  
[{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.
  
## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

