---
title: "Exemple&#160;: sp&#233;cification d&#39;un &#233;l&#233;ment racine pour les donn&#233;es XML g&#233;n&#233;r&#233;es par FOR XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode RAW, exemple de spécification d’élément racine"
  - "mode RAW, exemple avec FOR XML"
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Exemple&#160;: sp&#233;cification d&#39;un &#233;l&#233;ment racine pour les donn&#233;es XML g&#233;n&#233;r&#233;es par FOR XML
  En spécifiant l'option `ROOT` dans la requête `FOR XML`, vous pouvez demander un élément de niveau supérieur unique pour les données XML résultantes, comme illustré dans cette requête. L'argument spécifié pour la directive `ROOT` fournit le nom de l'élément racine.  
  
## Exemple  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
go  
```  
  
 Voici le résultat obtenu :  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## Voir aussi  
 [Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  