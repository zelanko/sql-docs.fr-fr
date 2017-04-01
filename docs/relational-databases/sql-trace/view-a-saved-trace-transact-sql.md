---
title: "Afficher une trace enregistr&#233;e (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "traces [SQL Server], affichage"
  - "affichage des traces"
  - "visualisation des traces"
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Afficher une trace enregistr&#233;e (Transact-SQL)
  Cette rubrique décrit l'utilisation des fonctions intégrées pour afficher une trace enregistrée.  
  
### Pour afficher une trace  
  
1.  Exécutez **fn_trace_getinfo** en spécifiant l’identificateur de la trace sur laquelle vous souhaitez des informations. Cette fonction retourne un tableau qui présente la trace, ses propriétés et des informations sur celle-ci.  
  
     Appelez la fonction comme suit :  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### Pour afficher toutes les traces existantes  
  
1.  Exécutez **fn_trace_getinfo** en spécifiant `0` ou `default`. Cette fonction retourne un tableau qui présente toutes les traces, leurs propriétés et des informations sur celles-ci.  
  
     Appelez la fonction comme suit :  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## Sécurité du .NET Framework  
 Pour exécuter la fonction intégrée **fn_trace_getinfo**, l’utilisateur a besoin de l’autorisation suivante :  
  
 ALTER TRACE sur le serveur.  
  
## Voir aussi  
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Afficher et analyser des traces avec SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  