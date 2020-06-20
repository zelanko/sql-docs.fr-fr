---
title: Propriétés de SQL Server Agent (page Système de travaux) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9b7f5064270e8e648b5b24b24745aa5a7c11120
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058680"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Propriétés de l'Agent SQL Server (page Système de travaux)
  Utilisez cette page pour afficher et modifier la manière dont le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service agent gère les travaux.  
  
## <a name="options"></a>Options  
 **Intervalle du délai d'arrêt (secondes)**  
 Spécifie le nombre de secondes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend pour considérer que les travaux sont terminés et pour forcer l'arrêt. Si le travail est toujours en cours d'exécution après l'intervalle spécifié, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] force l'arrêt du travail.  
  
 **Utiliser un compte proxy non-administrateur**  
 Définit un compte proxy non-administrateur pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]et les versions ultérieures prennent en charge plusieurs proxies, c’est pourquoi cette option est applicable uniquement lors de la gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versions de l’agent antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .  
  
 **Nom d'utilisateur**  
 Entrez le nom de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Mot de passe**  
 Entrez le mot de passe de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 **Domaine**  
 Entrez le domaine de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter des travaux](implement-jobs.md)  
  
  
