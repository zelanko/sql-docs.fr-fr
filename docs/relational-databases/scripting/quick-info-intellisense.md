---
title: "Infos express (IntelliSense) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Infos express (option) [IntelliSense]"
  - "déclarations [IntelliSense]"
  - "IntelliSense [SQL Server], Infos express"
  - "déclarations d'identificateur [IntelliSense]"
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Infos express (IntelliSense)
  L’option **Info express** de [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense affiche la déclaration complète de tout identificateur présent dans votre code. Lorsque vous déplacez le pointeur de la souris sur un identificateur, sa déclaration apparaît dans une fenêtre indépendante jaune. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Info express** est disponible dans les éditeurs de requête XML et du moteur de base de données.  
  
## Info express (Transact-SQL)  
 **Info express** affiche deux types d’informations dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Quand l’option **Info express** n’est pas en mode débogage, elle affiche la déclaration de l’expression. En revanche, en mode débogage, **Info express** affiche le nom de l’expression et sa valeur actuelle.  
  
 Dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)], **Info express** n’est disponible que pour les parties de la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] prises en charge par IntelliSense. Par exemple, si vous déplacez le pointeur de la souris sur l’identificateur d’un objet dont le type de données n’est pas pris en charge par IntelliSense, la fenêtre indépendante **Info express** contient un message indiquant que le type de données n’est pas pris en charge.  
  
## Voir aussi  
 [Syntaxe Transact-SQL prise en charge par IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  