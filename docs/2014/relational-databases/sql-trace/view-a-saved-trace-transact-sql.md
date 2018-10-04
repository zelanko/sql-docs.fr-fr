---
title: Afficher une trace enregistrée (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 01558096bb33aec8ffd21841d59a39b2cc26c6c5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166681"
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
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)   
 [Afficher et analyser des traces avec SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
