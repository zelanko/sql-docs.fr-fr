---
title: Propriétés de SQL Server Agent (page Historique) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bead031a6d7966db8894fc4b612714ae9c76eda2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207199"
---
# <a name="sql-server-agent-properties-history-page"></a>Propriétés de SQL Server Agent (page Historique)
  Utilisez cette page pour afficher et modifier des paramètres de gestion du journal d'historique du service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
 **Limiter la taille du journal d'historique des travaux.**  
 Limite la quantité d'informations d'historique des travaux que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve dans le journal.  
  
 **Taille maximale du journal d'historique des travaux (lignes)**  
 Spécifie le nombre maximal de lignes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve. Lorsque le journal a atteint le nombre de lignes indiqué, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime les lignes les plus anciennes à mesure que de nouvelles lignes sont insérées.  
  
 **Nombre  maximal de lignes d'historique des travaux par travail**  
 Spécifie le nombre maximal de lignes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve par travail. Lorsque l'historique d'un travail particulier a atteint le nombre de lignes indiqué, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime les lignes les plus anciennes à mesure que de nouvelles lignes sont insérées.  
  
 **Supprimer l'historique de l'agent**  
 Indique que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] va supprimer les entrées présentes dans le journal depuis plus longtemps que la période spécifiée. Il s'agit d'une exécution ponctuelle pour supprimer l'historique. Si vous préférez un travail récurrent, créez et planifiez un plan de maintenance avec un travail de nettoyage.  
  
 **Antérieur à**  
 Spécifie la période pendant laquelle l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve les entrées.  
  
## <a name="see-also"></a>Voir aussi  
 [Journal des erreurs de l'Agent SQL Server](sql-server-agent-error-log.md)  
  
  
