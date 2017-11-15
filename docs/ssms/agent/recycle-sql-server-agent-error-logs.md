---
title: "Recycler les journaux d’erreurs de l’Agent SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3404d3eceb9a57f9807ed2b47515fddb7331646a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="recycle-sql-server-agent-error-logs"></a>Recycler les journaux d'erreurs de l'Agent SQL Server
Utilisez cette page pour recycler les journaux d'erreurs de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Le recyclage du journal ferme le journal des erreurs actuel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent et crée un nouveau journal des erreurs sans redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Notez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent conserve les neuf derniers journaux d'erreurs. S'il y a déjà neuf journaux d'erreurs et que vous recyclez un autre journal d'erreurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent supprime le journal d'erreurs le plus ancien.  
  
## <a name="see-also"></a>Voir aussi  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
