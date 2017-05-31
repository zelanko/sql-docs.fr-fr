---
title: "Moniteur d’activité des travaux | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.jobactivitymonitor.alljobs.f1
- SQL13.SWB.ACTIVITYMON.F1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 16b68288a45afc08dde3b251f800a88ae2de75f6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="job-activity-monitor"></a>Moniteur d'activité des travaux
Utilisez cette page pour afficher l'activité actuelle des travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Cliquez sur **Filtre** pour restreindre le nombre de travaux affichés. La grille **Activité du travail de l’Agent** est en lecture seule. Cliquez sur les en-têtes de colonne pour trier la grille. Pour modifier un travail, double-cliquez dessus pour ouvrir la boîte de dialogue **Propriétés du travail** . En cliquant avec le bouton droit sur un travail affiché dans la grille, vous pouvez démarrer l'exécution de toutes les étapes du travail, démarrer le travail à partir d'une étape spécifique, désactiver ou activer le travail, actualiser le travail, supprimer le travail, afficher l'historique du travail ou afficher les propriétés du travail. Cliquez sur **Actualiser** pour afficher les informations actuelles dans la grille.  
  
## <a name="options"></a>Options  
**Nom**  
Nom du travail.  
  
**Activé**  
Indique si le travail est activé (**oui**) ou désactivé (**non**).  
  
**État***  
État actuel du travail.  
  
**Résultats de la dernière exécution**  
État du travail lors de sa dernière exécution.  
  
**Dernière exécution**  
Date et heure de la dernière exécution du travail via la date et l'heure locales du serveur.  
  
**Prochaine exécution***  
Date et heure de la prochaine planification du travail via la date et l'heure locales du serveur.  
  
**Catégorie**  
La catégorie de travaux attribuée au travail.  
  
**Exécutable**  
**Oui** si le travail peut être exécuté ; **Non** si le travail ne peut pas être exécuté. Un travail ne peut pas être exécuté s'il ne comporte aucune étape ou s'il n'est associé à aucun serveur cible.  
  
**Planifié**  
**Oui** s’il existe une planification du travail pour ce travail ; **Non** s’il n’y a pas de planification pour ce travail.  
  
*Seuls les membres du rôle serveur fixe sysadmin de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et le groupe d’administrateurs du serveur peuvent consulter les valeurs de cette colonne. Les membres du rôle SQLAgentOperatorRole ne peuvent pas consulter les valeurs de cette colonne.  
  
#### <a name="to-open-the-job-activity-monitor"></a>Pour ouvrir le Moniteur d'activité du travail  
  
-   Dans **l’Explorateur d’objets**, développez votre serveur, puis **Agent SQL Server**, cliquez avec le bouton droit sur **Moniteur d’activité des travaux**, puis cliquez sur **Afficher l’activité du travail**.  
  
## <a name="see-also"></a>Voir aussi  
[Surveiller l'activité des travaux](../../ssms/agent/monitor-job-activity.md)  
  

