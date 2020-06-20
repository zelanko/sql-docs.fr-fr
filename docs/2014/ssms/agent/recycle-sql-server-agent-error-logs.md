---
title: Recycler les journaux d’erreurs de l’Agent SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b30f0a2ba9a2d861d4a36a86489757cde512fea
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058788"
---
# <a name="recycle-sql-server-agent-error-logs"></a>Recycler les journaux d'erreurs de l'Agent SQL Server
  Utilisez cette page pour recycler les journaux d’erreurs de l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent. Le recyclage du journal ferme le journal des erreurs actuel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et crée un nouveau journal des erreurs sans redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Notez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent conserve les neuf derniers journaux d'erreurs. S'il y a déjà neuf journaux d'erreurs et que vous recyclez un autre journal d'erreurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent supprime le journal d'erreurs le plus ancien.  
  
## <a name="see-also"></a>Voir aussi  
 [Journal des erreurs de l'Agent SQL Server](sql-server-agent-error-log.md)  
  
  
