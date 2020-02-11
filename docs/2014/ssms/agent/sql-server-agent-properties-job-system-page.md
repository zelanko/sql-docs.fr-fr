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
manager: craigg
ms.openlocfilehash: 8dceeba78e639ecbe2fd81fbdb1021293e75cf8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63246084"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Propriétés de l'Agent SQL Server (page Système de travaux)
  Utilisez cette page pour afficher et modifier la manière [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dont le service agent gère les travaux.  
  
## <a name="options"></a>Options  
 **Intervalle de délai d’arrêt (en secondes)**  
 Spécifie le nombre de secondes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend pour considérer que les travaux sont terminés et pour forcer l'arrêt. Si le travail est toujours en cours d'exécution après l'intervalle spécifié, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] force l'arrêt du travail.  
  
 **Utiliser un compte proxy non-administrateur**  
 Définit un compte proxy non-administrateur pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures prennent en charge plusieurs proxies. par conséquent, cette [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] option s’applique uniquement [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]lors de la gestion des versions de l’agent antérieures à.  
  
 **Nom d'utilisateur**  
 Entrez le nom de l'utilisateur du compte proxy non-administrateur. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Mot de passe**  
 Entrez le mot de passe de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]et les versions ultérieures prennent en charge plusieurs proxies. par conséquent, cette [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] option s’applique uniquement [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]lors de la gestion des versions de l’agent antérieures à.  
  
 **Domain**  
 Entrez le domaine de l'utilisateur du compte proxy non-administrateur. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter des travaux](implement-jobs.md)  
  
  
