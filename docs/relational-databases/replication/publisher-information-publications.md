---
title: Informations sur le serveur de distribution, Publications | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publisherinfo.publications.f1
ms.assetid: 0b2e3d4e-03b7-4c31-8f96-48648d750010
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 5c7af0d388deef7b0f8249de759b688c4f49124d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287493"
---
# <a name="publisher-information-publications"></a>Informations sur le serveur de publication, onglet Publications
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  L'onglet **Publications** fournit des informations résumées pour toutes les publications sur le serveur de publication sélectionné dans le volet gauche.  
  
## <a name="options"></a>Options  
 Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Trier**: cette option vous permet d'effectuer un tri sur ou plusieurs colonnes dans la boîte de dialogue **Trier les colonnes** .  
  
-   **Choisir les colonnes à afficher**: cette option vous permet de sélectionner les colonnes à afficher et l'ordre d'affichage dans la boîte de dialogue **Choisir les colonnes** .  
  
-   **Filtre**: cette option vous permet de filtrer les lignes dans la grille selon les valeurs de colonne dans la boîte de dialogue **Paramètres du filtre** .  
  
-   **Effacer le filtre**: cette option vous permet d'effacer tous les paramètres du filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **État**  
 État de chaque publication déterminé par l'état de priorité la plus haute de ses abonnements. La grille contenant les informations de publication est triée par défaut par la colonne **État** . La liste suivante répertorie les éventuelles valeurs d'état ainsi que leur ordre de tri (par exemple, les erreurs sont toujours affichées en haut de la grille) :  
  
-   Error  
  
-   Critique pour les performances  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   OK  
  
 La valeur d'état **Critique pour les performances** est pertinente pour les abonnements transactionnels et de fusion. Pour les abonnements transactionnels, elle ne peut être affichée que si un seuil est défini. Pour plus d’informations sur les mesures de performances et sur la définition des seuils, consultez [Analyser les performances avec le Moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) et [Définir des seuils et des avertissements dans le Moniteur de réplication](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Publication**  
 Nom de chaque publication, sous la forme *PublicationDatabaseName: PublicationName*.  
  
 **Abonnements**  
 Nombre d'abonnements pour chaque publication.  
  
 **Synchronisation**  
 Nombre d'abonnements pour chaque publication en cours de synchronisation :  
  
-   Pour la réplication transactionnelle, le terme « synchronisation » signifie que l'Agent de distribution est en cours d'exécution mais que les données ne sont pas nécessairement répliquées.  
  
-   Pour la réplication de fusion, le terme « synchronisation » signifie que l'Agent de fusion est en cours d'exécution et que les données sont en cours de réplication.  
  
-   Pour la réplication d'instantané, le terme « synchronisation » signifie que l'Agent de distribution est en cours d'exécution et que les données sont en cours de réplication.  
  
 **Performance moyenne actuelle** et **Pire performance actuelle**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Évaluations respectives des performances moyenne et pire pour tous les abonnements à une publication. Ces évaluations sont basées sur les mesures les plus récentes prises par le moniteur de réplication. Elles ne reflètent pas les performances d'un abonnement dans le temps.  
  
 Dans le cas de la réplication transactionnelle, le moniteur de réplication affiche une valeur uniquement pour les publications dont les seuils de performances sont définis. Si des seuils de performances ne sont pas définis pour une publication, cette colonne contient **Non activé**. Dans le cas de la réplication de fusion, le moniteur de réplication affiche une valeur après cinq synchronisations avec au moins 50 modifications chacune via le même type de connexion (accès à distance ou LAN). S'il y a eu moins de cinq synchronisations avec au moins 50 modifications ou que la synchronisation la plus récente possède moins de 50 modifications, cette colonne est vide.  
  
 Les valeurs possibles sont les suivantes :  
  
-   Excellent  
  
-   Bonne  
  
-   Correcte  
  
-   Médiocre  
  
-   Critique  
  
 Pour plus d’informations sur la définition des indices et des seuils de performances, consultez [Analyser les performances avec le Moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour un serveur de publication &#40;moniteur de réplication&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
