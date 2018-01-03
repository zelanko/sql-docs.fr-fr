---
title: "Propriétés de SQL Server Agent (page Système de travaux) | Microsoft Docs"
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
f1_keywords: sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddaf9fe88289bb05c312539fdd60f83d55e0ca8b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-agent-properties-job-system-page"></a>Propriétés de l'Agent SQL Server (page Système de travaux)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Utilisez cette page pour afficher et modifier la façon dont le service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent gère les travaux.  
  
## <a name="options"></a>Options  
**Intervalle du délai d'arrêt (secondes)**  
Spécifie le nombre de secondes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] attend pour considérer que les travaux sont terminés et pour forcer l'arrêt. Si le travail est toujours en cours d'exécution après l'intervalle spécifié, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] force l'arrêt du travail.  
  
**Utiliser un compte proxy non-administrateur**  
Définit un compte proxy non-administrateur pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**User name**  
Entrez le nom de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Mot de passe**  
Entrez le mot de passe de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qui précèdent [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)].  
  
**Domainee**  
Entrez le domaine de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a> Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
  
