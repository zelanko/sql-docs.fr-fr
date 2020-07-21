---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 719f541b31c9b537a6fee75970567f24eb50f674
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554224"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10003|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HR_E_OUTOFMEMORY|  
|Texte du message|Le fournisseur n'a plus de mémoire.|  
  
## <a name="explanation"></a>Explication  
 L'insuffisance de mémoire système a provoqué une pénurie de mémoire pour le fournisseur OLE DB.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Redémarrez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cela ne change rien, redémarrez l'ordinateur. Si le problème persiste, collectez les événements de trace OLE DB à l’aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et fournissez ces données au support technique du fournisseur OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles et autorisations du générateur de SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
