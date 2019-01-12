---
title: Informations sur l’éditeur, suivi des abonnements (Publication transactionnelle, SQL Server 2005 et versions ultérieur) de liste | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.tran.f1
ms.assetid: 6bc64ddb-5c86-4681-a391-77fc1d3c4e6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 55a3be7188905ccebb9f9d09567879b6bca13de5
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126529"
---
# <a name="publisher-information-subscription-watch-list-transactional-publication-sql-server-2005-and-later"></a>Informations sur le serveur de publication, Liste de suivi des abonnements (Publication transactionnelle, SQL Server 2005 et version ultérieure)
  L'onglet **Liste de suivi des abonnements** est disponible pour les serveurs de distribution qui exécutent SQL Server 2005 et les versions ultérieures. Il permet d'afficher des informations sur les abonnements depuis toutes les publications disponibles sur le serveur de publication sélectionné. Vous pouvez filtrer la liste des abonnements pour identifier les erreurs, les avertissements et les abonnements qui ne fonctionnent pas correctement. Cet onglet fournit à l'administrateur un emplacement central pour contrôler toute l'activité de réplication sur un serveur de publication : Moniteur de réplication affiche tous les abonnements qui requièrent votre attention, en fonction du type de réplication sélectionné et de l’option choisie dans la **afficher** zone de liste déroulante. Du fait que les éléments affichés dans cet onglet reposent sur l'état et les performances actuelles, les abonnements sont affichés sur cette page uniquement s'ils correspondent à l'option actuelle de la zone de liste **Afficher** .  
  
## <a name="options"></a>Options  
 Pour plus d'informations et en savoir plus sur les tâches associées à un abonnement, cliquez avec le bouton droit de la souris sur la ligne de l'abonnement, puis cliquez sur une option dans le menu contextuel. Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Tri**: Trier sur une ou plusieurs colonnes dans le **trier les colonnes** boîte de dialogue.  
  
-   **Choisissez les colonnes à afficher**: Sélectionner les colonnes à afficher et l’ordre dans lequel les afficher dans le **choisir les colonnes** boîte de dialogue.  
  
-   **Filtre**: Filtrer des lignes dans la grille en fonction des valeurs de colonne dans la **paramètres de filtre** boîte de dialogue.  
  
-   **Effacer le filtre**: Effacer des paramètres de filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **Afficher les abonnements transactionnels**  
 Sélectionnez le type des abonnements (transactionnel, instantané ou fusion) à afficher pour le serveur de publication sélectionné.  
  
 **Afficher**  
 Sélectionnez les états d'abonnement à afficher pour le type d'abonnement sélectionné. Par exemple, vous pouvez afficher uniquement les abonnements associés à une erreur.  
  
 **État**  
 État de chaque abonnement déterminé par l'état de l'Agent de distribution ou l'Agent de lecture du journal (la priorité la plus haute est affichée ; l'état peut être également déterminé par l'Agent de lecture de la file d'attente si des abonnements mis à jour en attente sont utilisés).  
  
 Par défaut, la grille qui contient des informations d'abonnement est triée en fonction de la colonne **État** (puis en fonction de la colonne **Performances** pour les abonnements ayant le même état). La liste suivante contient toutes les valeurs d'état possibles et l'ordre de tri des valeurs (par exemple, les erreurs sont toujours affichées dans la partie supérieure de la grille).  
  
-   Error  
  
-   Critique pour les performances  
  
-   Expire bientôt/Expiré  
  
-   Abonnement non initialisé  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Non exécuté  
  
-   Exécution en cours  
  
 L'ordre de tri détermine également la valeur affichée lorsqu'un abonnement a plusieurs états. Si, par exemple, un abonnement a une erreur et expire bientôt, la colonne **État** affiche **Erreur**.  
  
 Les valeurs d'état **Critique pour les performances**, **Expire bientôt/Expiré**et **Abonnement non initialisé** sont des avertissements. Lorsqu'un avertissement est affiché, la colonne **État** s'affiche également si un agent est en cours d'exécution. Par exemple, l'état peut être **En cours d'exécution, Critique pour les performances**.  
  
 Les valeurs d'état **Critique pour les performances** et **Expire bientôt/Expiré** s'affichent uniquement si des seuils sont définis. Pour plus d’informations sur les mesures de performances et sur la définition des seuils, consultez [Analyser les performances avec le Moniteur de réplication](monitor/monitor-performance-with-replication-monitor.md) et [Définir des seuils et des avertissements dans le Moniteur de réplication](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Nom de chaque abonnement au format : *NomAbonné : Nombasedonnéesabonnements*.  
  
 **Publication**  
 Nom de la publication avec laquelle un abonnement se synchronise, au format : *PublicationDatabaseName: Nom_publication*.  
  
 **Performances**  
 La valeur de performance de chaque abonnement est basée sur les dernières mesures relevées par le Moniteur de réplication et n'affecte pas les performances historiques. Les performances sont mesurées pour les abonnements aux publications ayant des seuils définis. Si des seuils de performances ne sont pas définis pour une publication, cette colonne contient **Non activé**. Les valeurs possibles sont les suivantes :  
  
-   Excellent  
  
-   Bonne  
  
-   Correcte  
  
-   Médiocre  
  
-   Critique  
  
 Si les performances sont critiques, **Critique pour les performances** figure dans la colonne **État** . Pour plus d’informations sur la définition des indices et des seuils de performances, consultez [Analyser les performances avec le Moniteur de réplication](monitor/monitor-performance-with-replication-monitor.md).  
  
 **Latence**  
 Délai moyen qui s'écoule entre la validation d'une transaction sur le serveur de publication et la validation de la transaction correspondante au niveau de l'Abonné. La latence affichée est basée sur les dernières mesures relevées par le Moniteur de réplication. Pour plus d’informations sur la mesure de la latence, consultez [Mesurer la latence et valider les connexions pour la réplication transactionnelle](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
 **Dernière synchronisation**  
 Heure de la dernière exécution de l'Agent de distribution. Si la synchronisation est en cours, **Opération en cours** s'affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)  
  
  
