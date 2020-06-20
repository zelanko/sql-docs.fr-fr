---
title: Informations sur le serveur de publication, liste de suivi des abonnements (publication d’instantané, SQL Server 2005 et versions ultérieures) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ae61697e1943aa97658d7651e6a2bd4176f88c1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85005028"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a>Informations du serveur de publication, Liste de suivi des abonnements (Publication d'instantanés, SQL Server 2005 et ultérieure)
   L’onglet **Liste de suivi des abonnements** est disponible pour les serveurs de distribution qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures. Il permet d’afficher des informations sur les abonnements depuis toutes les publications disponibles sur le serveur de publication sélectionné. Vous pouvez filtrer la liste des abonnements pour identifier les erreurs, les avertissements et les abonnements qui ne fonctionnent pas correctement. Cet onglet fournit à l'administrateur un emplacement central pour contrôler toute l'activité de réplication sur un serveur de publication : le Moniteur de réplication affiche tous les abonnements nécessitant une attention, en fonction du type de réplication sélectionné et de l'option choisie dans la zone de liste déroulante **Afficher** . Du fait que les éléments affichés dans cet onglet reposent sur l'état et les performances actuelles, les abonnements sont affichés sur cette page uniquement s'ils correspondent à l'option actuelle de la zone de liste **Afficher** .  
  
## <a name="options"></a>Options  
 Pour plus d'informations et en savoir plus sur les tâches associées à un abonnement, cliquez avec le bouton droit de la souris sur la ligne de l'abonnement, puis cliquez sur une option dans le menu contextuel. Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Trier**: cette option vous permet d'effectuer un tri sur ou plusieurs colonnes dans la boîte de dialogue **Trier les colonnes** .  
  
-   **Choisir les colonnes à afficher**: cette option vous permet de sélectionner les colonnes à afficher et l'ordre d'affichage dans la boîte de dialogue **Choisir les colonnes** .  
  
-   **Filtre**: cette option vous permet de filtrer les lignes dans la grille selon les valeurs de colonne dans la boîte de dialogue **Paramètres du filtre** .  
  
-   **Effacer le filtre**: cette option vous permet d'effacer tous les paramètres du filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **Afficher les abonnements aux instantanés**  
 Sélectionnez le type des abonnements (transactionnel, instantané ou fusion) à afficher pour le serveur de publication sélectionné.  
  
 **Afficher**  
 Sélectionnez les états d'abonnement à afficher pour le type d'abonnement sélectionné. Par exemple, vous pouvez afficher uniquement les abonnements associés à une erreur.  
  
 **État**  
 État de chaque abonnement, déterminé par l'état de l'Agent d'instantané ou l'Agent de distribution (la priorité d'état la plus haute est affichée).  
  
 Par défaut, la grille qui contient des informations d'abonnement est triée en fonction de la colonne **État** . La liste suivante contient toutes les valeurs d'état possibles et l'ordre de tri des valeurs (par exemple, les erreurs sont toujours affichées dans la partie supérieure de la grille).  
  
-   Erreur  
  
-   Expire bientôt/Expiré  
  
-   Abonnement non initialisé  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Synchronisation  
  
-   Sans synchronisation  
  
 L'ordre de tri détermine également la valeur affichée lorsqu'un abonnement a plusieurs états. Si, par exemple, un abonnement a une erreur et expire bientôt, la colonne **État** affiche **Erreur**.  
  
 Les valeurs d'état **Expire bientôt/Expiré** et **Abonnement non initialisé** sont des avertissements. Lorsqu'un avertissement est affiché, la colonne **État** s'affiche également si un agent est en cours d'exécution. Par exemple, l'état peut être **En cours d'exécution, Expire bientôt/Expiré**.  
  
 La valeur d'état **Expire bientôt/Expiré** s'affiche uniquement si un seuil est défini. Pour plus d’informations sur la définition des seuils, consultez [Définir des seuils et des avertissements dans le Moniteur de réplication](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Nom de chaque abonnement, au format : *NomAbonné: NomBaseDonnéesAbonnements*.  
  
 **Publication**  
 Nom de la publication avec laquelle un abonnement se synchronise, au format : *NomBaseDonnéesPublication: NomPublication*.  
  
 **Dernière synchronisation**  
 Heure de la dernière exécution de l'Agent de distribution. Si la synchronisation est en cours, **Opération en cours** s'affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)  
  
  
