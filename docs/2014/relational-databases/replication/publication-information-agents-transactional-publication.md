---
title: Informations de publication, Agents (Publication transactionnelle) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68996f64bd61d96b4a2938a9711519207861fcd3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52780361"
---
# <a name="publication-information-agents-transactional-publication"></a>Informations de publication, Agents (Publication transactionnelle)
  L'onglet **Agents** contient des informations résumées sur les agents de la publication sélectionnée. Les informations sur l'Agent d'instantané et sur l'Agent de lecture du journal s'affichent pour toutes les publications transactionnelles. Les informations sur l'Agent de lecture de la file d'attente s'affichent pour les publications transactionnelles qui ont des abonnements mis à jour en file d'attente.  
  
## <a name="options"></a>Options  
 Pour plus d'informations et en savoir plus sur les tâches associées à un agent, cliquez avec le bouton droit de la souris sur la ligne de l'Agent, puis cliquez sur une option dans le menu contextuel. Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Tri**: Trier sur une ou plusieurs colonnes dans le **trier les colonnes** boîte de dialogue.  
  
-   **Choisissez les colonnes à afficher**: Sélectionner les colonnes à afficher et l’ordre dans lequel les afficher dans le **choisir les colonnes** boîte de dialogue.  
  
-   **Filtre**: Filtrer des lignes dans la grille en fonction des valeurs de colonne dans la **paramètres de filtre** boîte de dialogue.  
  
-   **Effacer le filtre**: Effacer des paramètres de filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **État**  
 État de chaque agent de réplication associé à la publication. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Non exécuté  
  
-   Exécution en cours  
  
-   Terminé  
  
 **Agent**  
 Nom de chaque agent de réplication associé à la publication. L'Agent de distribution est associé aux abonnements à cette publication. Pour plus d’informations, consultez [Afficher des informations et effectuer des tâches pour les agents d’abonnement &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
 **Dernière heure de début**  
 Heure du dernier démarrage de l'Agent.  
  
 **Duration**  
 Durée d'exécution de l'Agent. La durée correspond au délai écoulé si l'Agent est actif ou au délai total si l'Agent a déjà été exécuté.  
  
 **Dernière action**  
 La dernière action effectuée au cours de la dernière exécution de l'Agent.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour un serveur de publication &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour les agents associés à une publication &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [Surveillance de la réplication](monitoring-replication.md)  
  
  
