---
title: "Prise en charge de FOR XML pour les types de donn&#233;es d&#233;finis par l&#39;utilisateur (UDT) | Microsoft Docs"
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
  - "UDT [SQL Server], XML"
  - "types définis par l’utilisateur [SQL Server], XML"
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Prise en charge de FOR XML pour les types de donn&#233;es d&#233;finis par l&#39;utilisateur (UDT)
  FOR XML ne prend pas en charge les types de données définis par l'utilisateur (UDT) du Common Language Runtime (CLR).  
  
 Pour utiliser FOR XML avec des types de données CLR définis par l'utilisateur, assurez-vous que le type de données a une sérialisation XML et utilisez un cast explicite en XML dans la clause select FOR XML.  
  
## Voir aussi  
 [Prise en charge FOR XML des différents types de données SQL Server](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  