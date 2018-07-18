---
title: Tableau de bord utilitaire (utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 999eb741-4a60-43f6-ab37-2df7dce845c1
caps.latest.revision: 5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c37387c3a5a47a624cdcac57d73552c8eeda9b3e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192139"
---
# <a name="utility-dashboard-sql-server-utility"></a>Tableau de bord de l'utilitaire (utilitaire SQL Server)
  Pour consulter des données dans le tableau de bord de l’utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], sélectionnez le nœud supérieur dans l’arborescence de l’Explorateur de l’utilitaire - étiqueté « Utility<nom_UCP\\\(NomOrdinateur\UCP) ». Le tableau de bord inclut les données de synthèse et les données détaillées de toutes les instances managées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et de toutes les applications de couche Données dans l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour actualiser les données du tableau de bord, cliquez avec le bouton droit sur le nœud supérieur de l’arborescence de l’Explorateur de l’utilitaire et sélectionnez **Actualiser**.  
  
 Pour plus d’informations sur la création d’un point de contrôle d’utilitaire, consultez [Créer un point de contrôle de l’utilitaire SQL Server &#40;utilitaire SQL Server&#41;](../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md). Pour plus d’informations sur l’ajout d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , consultez [Inscrire une instance de SQL Server &#40;utilitaire SQL Server&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md).  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Intégrité de l'instance gérée  
 L'état d'intégrité des instances gérées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'affiche sur le côté gauche du volet de contenu de l'Explorateur de l'utilitaire.  
  
 Les paramètres d'intégrité de l'instance gérée sont les suivants :  
  
-   utilisation du processeur pour l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)];  
  
-   utilisation du fichier de base de données ;  
  
-   utilisation de l'espace du volume de stockage ;  
  
-   utilisation du processeur par l'ordinateur ;  
  
-   L'état de chaque paramètre est divisé en trois catégories :  
  
-   bien utilisé : nombre d'instances gérées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ne violent pas les stratégies d'utilisation des ressources ;  
  
-   sous-exploité : nombre de ressources gérées qui violent les stratégies de sous-exploitation des ressources ;  
  
-   surexploité : nombre de ressources gérées qui violent les stratégies de surexploitation des ressources ;  
  
-   aucune donnée disponible : les données ne sont pas non plus disponibles pour les instances gérées de SQL Server parce que l'instance de SQL Server vient d'être inscrite et que la première opération de collecte de données n'est pas terminée, ou parce que l'instance gérée de SQL Server rencontre un problème pour recueillir et télécharger des données vers l'UCP.  
  
 L'état détaillé de chaque paramètre d'intégrité est répertorié dans des curseurs. La fraction située à la droite des curseurs montre combien d'instances gérées se trouvent dans chaque catégorie d'état.  
  
 Pour créer une vue filtrée d'une instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou une application de la couche Données, cliquez sur le lien pour une catégorie d'utilisation en regard de son curseur dans le tableau de bord de l'utilitaire. Par exemple, si vous cliquez sur **Processeur des instances surexploité** dans le volet **Contenu de l'Explorateur de l'utilitaire** , SSMS crée une vue de liste filtrée des instances gérées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ont l'UCP surexploité selon les paramètres de stratégie actuels.  
  
 Remarquez que lorsque vous cliquez sur un lien pour une catégorie d’utilisation, le nœud correspondant dans le volet de navigation Explorateur de l’utilitaire est ajouté avec **(filtré)** - c’est-à-dire, **Instances gérées** est étiqueté **Instances gérées (filtré)**. Pour consulter des paramètres de filtre, cliquez avec le bouton droit sur le nœud dans le volet de navigation et sélectionnez **Filtre**, puis cliquez sur **Paramètres du filtre**. Pour effacer des paramètres de filtre, cliquez avec le bouton droit sur le nœud dans le volet de navigation et sélectionnez **Filtre**, puis cliquez sur **Supprimer le filtre**.  
  
 Pour plus d’informations sur la consultation de l’état d’instances individuelles de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ou pour afficher ou modifier des paramètres de configuration de stratégie, consultez [Détails de l’instance gérée &#40;utilitaire SQL Server&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md).  
  
 Résumé de l'utilitaire  
 Affiche le nombre d'instances managées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et le nombre d'applications de couche Données gérées par l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 État d'intégrité des applications de couche Données  
 L'état d'intégrité des applications de couche Données s'affiche sur le côté droit du volet de contenu de l'Explorateur de l'utilitaire.  
  
 Les paramètres d'état d'intégrité des applications de couche Données sont les suivants :  
  
-   utilisation du processeur pour l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)];  
  
-   utilisation du fichier de base de données ;  
  
-   utilisation de l'espace du volume de stockage ;  
  
-   utilisation du processeur par l'ordinateur ;  
  
 L'état de chaque paramètre est divisé en trois catégories :  
  
-   bien utilisé : nombre d'applications de couche Données qui ne violent pas les stratégies d'utilisation des ressources ;  
  
-   surexploité : nombre d'applications de couche Données qui ne violent pas les stratégies de surexploitation des ressources ;  
  
-   sous-exploité : nombre d'applications de couche Données qui ne violent pas les stratégies de sous-exploitation des ressources ;  
  
-   aucune donnée disponible : les données ne sont pas disponibles pour les applications de couche Données parce que l'instance gérée de SQL Server qui contient l'application de couche Données ne signale pas de données.  
  
 L'état détaillé de chaque paramètre d'intégrité est répertorié dans des curseurs. La fraction située à droite des curseurs montre combien d'applications de couche Données se trouvent dans chaque catégorie d'état. Pour plus d’informations sur la consultation de l’état des instances de la couche Données, ou pour afficher ou modifier des paramètres de configuration de stratégie, consultez [Détails des applications de la couche Données déployées &#40;utilitaire SQL Server&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md).  
  
 Historique de l'utilisation de l'utilitaire du stockage  
 L'historique de l'utilisation s'affiche dans un graphique temporel situé au bas du tableau de bord de l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Notez que les données temporelles affichent la date et l'heure locales du processeur à l'aide du type de données datetime. Pour plus d’informations, consultez la rubrique [datetime (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=164071) dans la documentation en ligne de SQL Server. Lorsque vous utilisez le modèle d'objet de l'utilitaire, notez que SSMS utilise le type de données datetimeoffset. Pour plus d’informations, consultez la rubrique [datetimeoffset (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=141713) dans la documentation en ligne de SQL Server.  
  
 Utilisez les cases d'option situées à gauche de la zone d'affichage pour modifier la période de création de rapports pour le graphique.  
  
 Les options d'intervalle de création de rapport sont les suivants :  
  
-   1 jour, affiché par intervalles de 15 minutes ;  
  
-   1 semaine, affiché par intervalles de 1 jour ;  
  
-   1 mois, affiché par intervalles de 1 semaine ;  
  
-   1 an, affiché par intervalles de 1 mois.  
  
 Une fois que vous avez apporté une modification à l'intervalle de création de rapport, les données sont automatiquement actualisées.  
  
 Utilisation du stockage par l'utilitaire  
 Dans la partie inférieure droite du tableau de bord, le graphique à secteurs de l'utilisation du stockage affiche le rapport entre l'espace utilisé et l'espace libre sur les volumes résidant sur des ordinateurs qui contiennent des instances gérées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les données de cet affichage sont actualisées toutes les 15 minutes.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser l'Explorateur de l'utilitaire pour gérer l'Utilitaire SQL Server](../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Inscrire une Instance de SQL Server &#40;utilitaire SQL Server&#41;](../relational-databases/manage/enroll-an-instance-of-sql-server-sql-server-utility.md)   
 [Modifier une définition de la stratégie de contrôle d’intégrité des ressources &#40;Utilitaire SQL Server&#41;](../relational-databases/manage/modify-a-resource-health-policy-definition-sql-server-utility.md)  
  
  
