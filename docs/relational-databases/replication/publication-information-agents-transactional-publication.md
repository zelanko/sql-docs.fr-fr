---
title: Informations de publication, Agents (Publication transactionnelle) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 36c0233d5ba6f51f0cc7cd354bd810a08b2d3b72
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770034"
---
# <a name="publication-information-agents-transactional-publication"></a>Informations de publication, Agents (Publication transactionnelle)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  L'onglet **Agents** contient des informations résumées sur les agents de la publication sélectionnée. Les informations sur l'Agent d'instantané et sur l'Agent de lecture du journal s'affichent pour toutes les publications transactionnelles. Les informations sur l'Agent de lecture de la file d'attente s'affichent pour les publications transactionnelles qui ont des abonnements mis à jour en file d'attente.  
  
## <a name="options"></a>Options  
 Pour plus d'informations et en savoir plus sur les tâches associées à un agent, cliquez avec le bouton droit de la souris sur la ligne de l'Agent, puis cliquez sur une option dans le menu contextuel. Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Trier** : cette option vous permet d’effectuer un tri sur une ou plusieurs colonnes dans la boîte de dialogue **Trier les colonnes**.  
  
-   **Choisir les colonnes à afficher** : cette option vous permet de sélectionner les colonnes à afficher et l’ordre d’affichage dans la boîte de dialogue **Choisir les colonnes**.  
  
-   **Filtrer** : cette option vous permet de filtrer les lignes dans la grille selon les valeurs de colonne dans la boîte de dialogue **Paramètres du filtre**.  
  
-   **Effacer le filtre** : cette option vous permet d’effacer tous les paramètres du filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **État**  
 État de chaque agent de réplication associé à la publication. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Non exécuté  
  
-   Exécution en cours  
  
-   Terminé  
  
 **Agent**  
 Nom de chaque agent de réplication associé à la publication. L'Agent de distribution est associé aux abonnements à cette publication. Pour plus d’informations, consultez [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 **Dernière heure de début**  
 Heure du dernier démarrage de l'Agent.  
  
 **Duration**  
 Durée d'exécution de l'Agent. La durée correspond au délai écoulé si l'Agent est actif ou au délai total si l'Agent a déjà été exécuté.  
  
 **Dernière action**  
 La dernière action effectuée au cours de la dernière exécution de l'Agent.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
  
