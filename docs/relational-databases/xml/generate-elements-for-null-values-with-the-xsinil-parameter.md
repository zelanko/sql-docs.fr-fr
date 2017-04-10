---
title: "G&#233;n&#233;rer des &#233;l&#233;ments pour des valeurs NULL avec le param&#232;tre XSINIL | Microsoft Docs"
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
  - "Clause FOR XML, valeurs null"
  - "valeurs null [SQL Server], XML"
  - "ELEMENTS, directive"
  - "XSINIL, paramètre"
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# G&#233;n&#233;rer des &#233;l&#233;ments pour des valeurs NULL avec le param&#232;tre XSINIL
  La directive **ELEMENTS** construit du code XML dans lequel chaque valeur de colonne est mappée à un élément du code XML. Si la valeur de colonne est NULL, aucun élément n'est ajouté. En spécifiant le paramètre facultatif **XSINIL** sur la directive ELEMENTS, vous pouvez demander qu’un élément soit également créé pour la valeur NULL. Dans ce cas, un élément dont l’attribut **xsi:nil** a la valeur TRUE est retourné pour chaque valeur de colonne NULL.  
  
## Voir aussi  
 [Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  