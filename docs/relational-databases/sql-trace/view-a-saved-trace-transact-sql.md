---
title: Afficher une trace enregistrée (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4118a30ffe84210bd7829522d50dc0f163e88639
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582403"
---
# <a name="view-a-saved-trace-transact-sql"></a>Afficher une trace enregistrée (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique décrit l'utilisation des fonctions intégrées pour afficher une trace enregistrée.  
  
### <a name="to-view-a-specific-trace"></a>Pour afficher une trace  
  
1.  Exécutez **fn_trace_getinfo** en spécifiant l’identificateur de la trace sur laquelle vous souhaitez des informations. Cette fonction retourne un tableau qui présente la trace, ses propriétés et des informations sur celle-ci.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     Invoke the function this way:  
  
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
  
  
