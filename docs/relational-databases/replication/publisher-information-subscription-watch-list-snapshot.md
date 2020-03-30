---
title: Liste de suivi des abonnements (Moniteur de réplication - Instantané)
description: Décrit l’onglet « Liste de suivi des abonnements » du moniteur de réplication pour une publication d’instantané dans SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 254309ae930abea33d8b2ebdc285719fe614fab4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287471"
---
# <a name="publisher-information-subscription-watch-list-snapshot"></a>Informations sur le serveur de publication, Liste de suivi des abonnements (Instantané)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  L'onglet **Liste de suivi des abonnements** est disponible pour les serveurs de distribution qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures. Il permet d'afficher des informations sur les abonnements depuis toutes les publications disponibles sur le serveur de publication sélectionné. Vous pouvez filtrer la liste des abonnements pour identifier les erreurs, les avertissements et les abonnements qui ne fonctionnent pas correctement. Cet onglet fournit à l'administrateur un emplacement central pour contrôler toute l'activité de réplication sur un serveur de publication : le Moniteur de réplication affiche tous les abonnements nécessitant une attention, en fonction du type de réplication sélectionné et de l'option choisie dans la zone de liste déroulante **Afficher** . Du fait que les éléments affichés dans cet onglet reposent sur l'état et les performances actuelles, les abonnements sont affichés sur cette page uniquement s'ils correspondent à l'option actuelle de la zone de liste **Afficher** .  
  
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
  
-   Error  
  
-   Expire bientôt/Expiré  
  
-   Abonnement non initialisé  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Synchronisation  
  
-   Sans synchronisation  
  
 L'ordre de tri détermine également la valeur affichée lorsqu'un abonnement a plusieurs états. Si, par exemple, un abonnement a une erreur et expire bientôt, la colonne **État** affiche **Erreur**.  
  
 Les valeurs d'état **Expire bientôt/Expiré** et **Abonnement non initialisé** sont des avertissements. Lorsqu'un avertissement est affiché, la colonne **État** s'affiche également si un agent est en cours d'exécution. Par exemple, l'état peut être **En cours d'exécution, Expire bientôt/Expiré**.  
  
 La valeur d'état **Expire bientôt/Expiré** s'affiche uniquement si un seuil est défini. Pour plus d’informations sur la définition des seuils, consultez [Définir des seuils et des avertissements dans le Moniteur de réplication](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Nom de chaque abonnement, au format : *NomAbonné: NomBaseDonnéesAbonnements*.  
  
 **Publication**  
 Nom de la publication avec laquelle un abonnement se synchronise, au format : *NomBaseDonnéesPublication: NomPublication*.  
  
 **Dernière synchronisation**  
 Heure de la dernière exécution de l'Agent de distribution. Si la synchronisation est en cours, **Opération en cours** s'affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour un serveur de publication &#40;moniteur de réplication&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
