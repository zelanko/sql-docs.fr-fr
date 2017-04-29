---
title: "Afficher une trace enregistrée (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ac0fccff82a4324911481ea1179ca3cab01b8f10
ms.lasthandoff: 04/11/2017

---
# <a name="view-a-saved-trace-transact-sql"></a>Afficher une trace enregistrée (Transact-SQL)
  Cette rubrique décrit l'utilisation des fonctions intégrées pour afficher une trace enregistrée.  
  
### <a name="to-view-a-specific-trace"></a>Pour afficher une trace  
  
1.  Exécutez **fn_trace_getinfo** en spécifiant l’identificateur de la trace sur laquelle vous souhaitez des informations. Cette fonction retourne un tableau qui présente la trace, ses propriétés et des informations sur celle-ci.  
  
     Appelez la fonction comme suit :  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a>Pour afficher toutes les traces existantes  
  
1.  Exécutez **fn_trace_getinfo** en spécifiant `0` ou `default`. Cette fonction retourne un tableau qui présente toutes les traces, leurs propriétés et des informations sur celles-ci.  
  
     Appelez la fonction comme suit :  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Pour exécuter la fonction intégrée **fn_trace_getinfo**, l’utilisateur a besoin de l’autorisation suivante :  
  
 ALTER TRACE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Afficher et analyser des traces avec SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
