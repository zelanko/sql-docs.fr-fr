---
title: Informations de publication, Agents (Publication d’instantané) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publicationinfo.downlevelagents.snapshot.f1
ms.assetid: 599ff80b-392c-43aa-9db2-dc4ed33d4f6e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 47b334cf08e126308544ec2126c96f7da0bed932
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770023"
---
# <a name="publication-information-agents-snapshot-publication"></a>Informations de publication, Agents (Publication d'instantané)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  L'onglet **Agents** contient des informations résumées sur l'Agent d'instantané de la publication sélectionnée.  
  
## <a name="options"></a>Options  
 Pour plus d'informations et en savoir plus sur les tâches associées à l'Agent d'instantané, cliquez avec le bouton droit de la souris sur l'Agent, puis cliquez sur une option dans le menu contextuel. Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Trier** : cette option vous permet d’effectuer un tri sur une ou plusieurs colonnes dans la boîte de dialogue **Trier les colonnes**.  
  
-   **Choisir les colonnes à afficher** : cette option vous permet de sélectionner les colonnes à afficher et l’ordre d’affichage dans la boîte de dialogue **Choisir les colonnes**.  
  
-   **Filtrer** : cette option vous permet de filtrer les lignes dans la grille selon les valeurs de colonne dans la boîte de dialogue **Paramètres du filtre**.  
  
-   **Effacer le filtre** : cette option vous permet d’effacer tous les paramètres du filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **État**  
 État de l'Agent d'instantané. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Non exécuté  
  
-   Terminé  
  
 **Agent**  
 L'Agent d'instantané. Il s'agit du seul Agent associé à une publication d'instantané. L'Agent de distribution est associé aux abonnements à cette publication. Pour plus d’informations, consultez [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 **Dernière heure de début**  
 Heure du dernier démarrage de l'Agent.  
  
 **Duration**  
 Durée d'exécution de l'Agent. La durée correspond au délai écoulé si l'Agent est actif ou au délai total si l'Agent a déjà été exécuté.  
  
 **Dernière action**  
 La dernière action effectuée au cours de la dernière exécution de l'Agent.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
