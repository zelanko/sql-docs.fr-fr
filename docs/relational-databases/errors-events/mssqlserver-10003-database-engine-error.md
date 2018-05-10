---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b1aca5fb9c78a99d732f7b0a57ba2b7e0312b10
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver10003"></a>MSSQLSERVER_10003
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10003|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HR_E_OUTOFMEMORY|  
|Texte du message|Le fournisseur n'a plus de mémoire.|  
  
## <a name="explanation"></a>Explication  
L'insuffisance de mémoire système a provoqué une pénurie de mémoire pour le fournisseur OLE DB.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Redémarrez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cela ne change rien, redémarrez l'ordinateur. Si le problème persiste, collectez les événements de trace OLE DB à l’aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et fournissez ces données au support technique du fournisseur OLE DB.  
  
## <a name="see-also"></a> Voir aussi  
[Modèles et autorisations SQL Server Profiler](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client &#40;OLE DB&#41;](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
