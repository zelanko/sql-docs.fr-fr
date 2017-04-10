---
title: "Ajouter un nœud racine &#224; la sortie JSON avec l’option ROOT (SQL&#160;Server) | Microsoft Docs"
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
  - "ROOT (FOR JSON)"
ms.assetid: b9afa74a-f59f-483e-a178-42be2e9882c9
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Ajouter un nœud racine &#224; la sortie JSON avec l’option ROOT (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Pour ajouter un élément de niveau supérieur unique à la sortie JSON de la clause **FOR JSON**, spécifiez l’option **ROOT**.  
  
 Si vous ne spécifiez pas l’option **ROOT** , la sortie JSON n’inclura pas d’élément racine.  
  
## Exemples  
 Le tableau ci-après présente la sortie de la clause **FOR JSON** avec et sans l’option **ROOT** .  
  
 Les exemples du tableau ci-dessous reposent sur l’hypothèse que l’argument *RootName* facultatif est vide. Si vous fournissez un nom pour l’élément racine, cette valeur remplace la valeur **root** dans les exemples.  
  
 Sans l’option **ROOT**  
  
```json  
{  
   <<json properties>>  
}  
```  
  
```json  
[  
   <<json array elements>>  
]  
```  
  
 Avec l’option **ROOT**  
  
```json  
{   
  "root": {  
   <<json properties>>  
 }  
}  
```  
  
```json  
{   
  "root": [  
   << json array elements >>  
  ]  
}  
```  
  
 Voici un autre exemple de clause **FOR JSON** avec l’option **ROOT** . Cet exemple spécifie une valeur pour l’argument *RootName* facultatif.  
  
 **Requête**  
  
```tsql  
SELECT TOP 5   
      BusinessEntityID As Id,  
      FirstName, LastName,  
      Title As 'Info.Title',  
      MiddleName As 'Info.MiddleName'  
  FROM Person.Person  
  FOR JSON PATH, ROOT('info')  
```  
  
 **Résultat**  
  
```json  
{  
  "info": [  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
  ]  
}  
  
```  
  
 **Résultat (sans racine)**  
  
```json  
[  
  {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
  {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
  {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
  {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
  {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
  
```  
  
## Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  