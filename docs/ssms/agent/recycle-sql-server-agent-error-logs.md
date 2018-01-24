---
title: "Recycler les journaux d’erreurs de l’Agent SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: da85bcd6f835dd5b8c3cd2595c2d0e0222a1aefe
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="recycle-sql-server-agent-error-logs"></a>Recycler les journaux d'erreurs de l'Agent SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Utilisez cette page pour recycler les journaux d’erreurs de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Le recyclage du journal ferme le journal des erreurs actuel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent et crée un nouveau journal des erreurs sans redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Notez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent conserve les neuf derniers journaux d'erreurs. S'il y a déjà neuf journaux d'erreurs et que vous recyclez un autre journal d'erreurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent supprime le journal d'erreurs le plus ancien.  
  
## <a name="see-also"></a> Voir aussi  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
