---
title: "Modifier un emplacement de point d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.breakpt.location.file"
helpviewer_keywords: 
  - "débogueur Transact-SQL, emplacement de point d’arrêt"
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Modifier un emplacement de point d&#39;arr&#234;t
  L'emplacement du point d'arrêt spécifie la ligne et le caractère où réside ce point d'arrêt dans un fichier de script [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous pouvez modifier cet emplacement pour déplacer le point d'arrêt vers un autre emplacement du script ou vers un script différent.  
  
## Modification d'un emplacement  
 Lorsque vous modifiez l'emplacement d'un point d'arrêt, ce point d'arrêt se déplace jusqu'à son nouvel emplacement et conserve toutes ses propriétés existantes, telles que le nombre d'accès ou la condition.  
  
#### Pour modifier l'emplacement d'un point d'arrêt  
  
1.  Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Emplacement** dans le menu contextuel.  
  
     - ou -  
  
     Dans la fenêtre **Points d’arrêt**, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Emplacement** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Point d’arrêt sur fichier**, modifiez **Fichier** pour spécifier un nouveau fichier, **Ligne** pour spécifier une nouvelle ligne ou **Caractère** pour spécifier un nouvel emplacement dans la ligne. Si le nouveau fichier que vous spécifiez est déjà ouvert dans une fenêtre de l'éditeur de requête, le point d'arrêt est déplacé vers cette fenêtre de l'éditeur. Si le fichier n'est pas ouvert, une nouvelle fenêtre d'éditeur s'ouvre, le fichier y est chargé et le point d'arrêt est déplacé vers le nouvel emplacement.  
  
     L’option **Permettre que le code source soit différent de la version d’origine** n’a aucun effet lors du débogage de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## Voir aussi  
 [Spécifier un nombre d'accès](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Spécifier une action de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-action.md)   
 [Spécifier une condition de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Spécifier un filtre de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-filter.md)  
  
  