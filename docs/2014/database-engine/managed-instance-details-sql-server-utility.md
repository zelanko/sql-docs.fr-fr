---
title: Géré les détails de l’Instance (utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 6e51b7bb-a733-4852-8c33-7f4dbdf931c2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d2b01eceff763d554644065fdb5137695bd82f69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62774341"
---
# <a name="managed-instance-details-sql-server-utility"></a>Détails de l'instance gérée (utilitaire SQL Server)
  Les informations de la vue Instances managées de l’Explorateur de l’utilitaire fournissent des données d’utilisation pour les instances individuelles de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], un historique d’utilisation du processeur, les détails de l’utilisation du stockage au niveau du fichier, et la possibilité d’afficher et de mettre à jour des seuils de stratégie. Les seuils de stratégie peuvent être contrôlés au niveau de l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , pour un ordinateur, pour les fichiers de base de données et les fichiers journaux, ainsi qu’au niveau des volumes de stockage. Vous pouvez également consulter les détails des propriétés des instances managées individuelles de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Mode Liste  
 Le mode Liste, dans le volet supérieur, affiche des données sur les instances individuelles de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] répertoriées dans les lignes par ComputerName\InstanceName.  
  
 Les icônes d'état d'intégrité fournissent un résumé de l'état de chaque instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] par catégorie d'utilisation :  
  
-   Coche verte (![](../../2014/database-engine/media/well-utilized.gif "Correctement exploité")) : nombre d’instances gérées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ne violent pas les stratégies d’utilisation des ressources. Les ressources sont bien utilisées.  
  
-   Flèche bas verte (![](../../2014/database-engine/media/utility-down-arrow.gif "Utilitaire, flèche bas")) : les ressources sont sous-exploitées.  
  
-   Flèche haut rouge (![](../../2014/database-engine/media/utility-up-arrow.gif "Utilitaire, flèche haut")) : les ressources sont surexploitées.  
  
 La séquence des colonnes en mode Liste peut être modifiée en les faisant glisser vers la gauche ou la droite. Les colonnes en mode Liste peuvent être ajoutées ou supprimées en cliquant avec le bouton droit sur leurs en-tête et en les sélectionnant ou désélectionnant. Le menu contextuel offre également des options de tri. Le tri peut également être activé en cliquant en haut d'un nom de colonne.  
  
 Pour accéder aux options de filtre du mode Liste de l’utilitaire, cliquez avec le bouton droit sur le nœud **Instances managées** dans le volet de navigation de l’Explorateur de l’utilitaire et sélectionnez **Filtre**. Une fois que les paramètres de filtrage sont implémentés, le nœud **Instances managées** de l’Explorateur de l’utilitaire est étiqueté **Instances managées (filtré)** . Pour plus d’informations, consultez [Paramètres de filtre &#40;Explorateur d’objets et Explorateur de l’utilitaire&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).  
  
 Par défaut, les colonnes suivantes affichent des informations sur l'état d'intégrité de chaque instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Processeur de l’instance : affiche l’état d’intégrité de l’utilisation du processeur alloué à cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L'état d'intégrité de ce paramètre est déterminé d'après la stratégie d'utilisation du processeur définie pour l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et le paramètre de configuration de la stratégie d'évaluation des ressources volatiles. Pour plus d’informations, consultez [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Pour consulter l’historique de l’utilisation du processeur pour cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ou afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du processeur**.  
  
-   Processeur de l'ordinateur : affiche l'état d'intégrité de l'utilisation du processeur de l'ordinateur. L'état d'intégrité de ce paramètre est déterminé en fonction de la stratégie d'utilisation du processeur définie pour l'ordinateur et du paramètre de configuration de la stratégie d'évaluation des ressources volatiles. Pour plus d’informations, consultez [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Pour consulter l’historique de l’utilisation du processeur pour cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ou afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du processeur**.  
  
-   Espace de fichier : affiche un résumé de l’état d’intégrité de l’utilisation de l’espace de fichier pour toutes les bases de données appartenant à l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]sélectionnée. Si l'état d'intégrité de l'une des bases de données est surexploité, l'état d'intégrité de l'espace de fichier sera signalé en mode Liste comme étant surexploité. Si l'état d'intégrité de l'une des bases de données est sous-exploité et qu'aucune base de données n'est surexploitée, l'état d'intégrité de l'espace de fichier sera signalé en mode Liste comme étant sous-exploité. Sinon, l'état d'intégrité de l'espace du fichier sera signalé en mode Liste comme étant correctement utilisé. Pour afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du stockage** .  
  
-   Espace de volume : affiche un résumé des états d'intégrité de l'utilisation du volume pour tous les volumes contenant des bases de données qui appartiennent à l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]sélectionnée. Si l'état d'intégrité d'un des volumes est surexploité, l'état d'intégrité de l'espace de volume sera signalé en mode Liste comme étant surexploité. Si l'état d'intégrité d'un des volumes de données est sous-exploité et qu'aucun volume n'est surexploité, l'état d'intégrité de l'espace de volume sera signalé en mode Liste comme étant sous-exploité. Sinon, l'état d'intégrité de l'espace de volume sera signalé en mode Liste comme étant correctement utilisé. Pour afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du stockage** .  
  
-   Type de stratégie : indique si des stratégies « Globales » par défaut ou des stratégies de « Substitution » personnalisées sont appliquées pour l'instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Autres colonnes pouvant s'afficher à l'aide du menu contextuel dans la zone d'en-tête de colonne du mode Liste :  
  
-   Nom du processeur :  
  
-   Vitesse du processeur (MHz) :  
  
-   Nombre de processeurs :  
  
-   Mémoire physique (Mo) :  
  
-   Version du système d'exploitation :  
  
-   Version de SQL Server :  
  
-   Édition de SQL Server :  
  
-   Cluster : (True ou False)  
  
-   Répertoire de sauvegarde :  
  
-   Classement :  
  
-   En respectant la casse : (True ou False)  
  
-   Langue :  
  
-   Dernière heure signalée : Cette colonne indique la date locales du processeur et l’heure à l’aide du type de données datetime. Pour plus d’informations, consultez la rubrique [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) dans la documentation en ligne de SQL Server. Lorsque vous utilisez le modèle d'objet de l'utilitaire, notez que SSMS utilise le type de données datetimeoffset. Pour plus d’informations, consultez la rubrique [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) dans la documentation en ligne de SQL Server.  
  
 Onglet Utilisation du processeur  
 L’onglet d’utilisation du processeur affiche côte à côte des graphiques de données d’historique pour l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et l’utilisation du processeur de l’ordinateur.  
  
 Le graphique affiche l'historique de l'utilisation du processeur pour l'intervalle spécifié dans les cases d'option situées sur le côté droit de la zone d'affichage. Pour modifier l'intervalle d'affichage et actualiser le jeu de données, sélectionnez une case d'option sur la liste.  
  
 Les options d'intervalle sont les suivantes :  
  
-   1 jour, affiché par intervalles de 15 minutes ;  
  
-   1 semaine, affiché par intervalles de 1 jour ;  
  
-   1 mois, affiché par intervalles de 1 semaine ;  
  
-   1 an, affiché par intervalles de 1 mois.  
  
 Onglet Utilisation du stockage  
 L'arborescence de l'onglet Utilisation du stockage affiche les détails de l'utilisation du stockage. Notez que les données temporelles affichent la date et l'heure locales du processeur à l'aide du type de données datetime. Pour plus d’informations, consultez la rubrique [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) dans la documentation en ligne de SQL Server. Lorsque vous utilisez le modèle d'objet de l'utilitaire, notez que SSMS utilise le type de données datetimeoffset. Pour plus d’informations, consultez la rubrique [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) dans la documentation en ligne de SQL Server.  
  
 L'affichage peut être regroupé par base de données ou par volume. Pour utiliser l’arborescence de la base de données, sélectionnez la case d’option **Base de données** dans la sélection **Regrouper les fichiers par** . Pour consulter l'état de l'utilisation du stockage pour des fichiers de base de données individuels, cliquez sur le signe plus en regard du nom d'une base de données dans l'arborescence. Les fichiers de base de données répertoriés incluent toutes les bases de données utilisateur et système qui appartiennent à l’instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que vous avez sélectionnée en mode Liste.  
  
 L'arborescence correspond à la hiérarchie du stockage. Le nœud racine de l'arborescence est la base de données. Le niveau suivant de l'arborescence contient un nœud groupe de fichiers ou des nœuds qui appartiennent à la base de données, ainsi qu'un nœud fichier journal pour les journaux appartenant à la base de données. Le niveau suivant contient les fichiers de données qui appartiennent au groupe de fichiers.  
  
 Les données affichées dans le graphique d'historique de l'utilisation du stockage changent en fonction du nœud sélectionné dans l'arborescence :  
  
-   Sélectionnez le nœud groupe de fichiers pour afficher un graphique de l'espace de fichier utilisé par tous les fichiers de données appartenant au groupe de fichiers sélectionné.  
  
-   Sélectionnez le nœud fichier journal pour afficher un graphique de l'espace de fichier utilisé par tous les fichiers journaux appartenant à la base de données sélectionnée.  
  
-   Sélectionnez le nœud base de données pour afficher un graphique qui additionne l'espace de fichier utilisé par tous les fichiers de données et tous les fichiers journaux qui appartiennent à la base de données sélectionnée.  
  
 Les icônes d'état d'intégrité fournissent en un coup d'œil un état des fichiers, des groupes de fichiers et des fichiers journaux de la base de données :  
  
 Pour les bases de données :  
  
-   Coche verte : état d'intégrité de tous les groupes de fichiers et fichiers journaux ni surexploités ni sous-exploités.  
  
-   Flèche bas verte : état d'intégrité montrant qu'au moins un groupe de fichiers ou fichier journal est sous-exploité, aucun état d'intégrité n'étant surexploité.  
  
-   Flèche haut rouge : état d'intégrité montrant qu'au moins un groupe de fichiers ou fichier journal est surexploité.  
  
 Pour les groupes de fichiers ou les fichiers journaux :  
  
-   Coche verte : l'utilisation de l'espace de fichier de tous les fichiers du groupe de fichiers n'est ni surexploitée ni sous-exploitée.  
  
-   Flèche bas verte : l'utilisation de l'espace de fichier d'au moins un fichier du groupe de fichiers est sous-exploitée et aucun fichier du groupe de fichiers n'est surexploité.  
  
-   Flèche haut rouge : l'utilisation de l'espace de fichier de tous les fichiers de données du groupe de fichiers est surexploitée.  
  
 Pour consulter les fichiers par volume, sélectionnez la case d’option **Volume** dans la sélection **Regrouper les fichiers par** . Le graphique d'historique de l'utilisation du stockage montre l'espace de fichier utilisé par tous les fichiers de données et tous les fichiers journaux du volume de stockage. Développez l'arborescence pour voir le détail des fichiers des données et des fichiers journaux de la base de données.  
  
 Les icônes d'état servent à fournir l'état de chaque volume :  
  
-   Coche verte : les ressources sont bien utilisées.  
  
-   Flèche bas verte : les ressources sont sous-exploitées.  
  
-   Flèche haut rouge : les ressources sont surexploitées.  
  
 La jauge en regard de chaque nom de fichier sous l'onglet Utilisation du stockage représente la quantité d'espace utilisée par le fichier par rapport à sa capacité effective. La valeur en pourcentage affichée en regard de la jauge est le rapport entre la quantité d'espace utilisée par le fichier et la capacité effective du fichier. Les info-bulles fournissent des données qui servent à calculer le pourcentage de chaque volume et de chaque fichier par rapport à la capacité effective.  
  
 Si le fichier n'est pas configuré pour s'agrandir automatiquement, alors la capacité effective sera la quantité d'espace allouée au fichier. Si le fichier est configuré pour s'agrandir automatiquement, la capacité effective sera la somme de la quantité d'espace actuellement allouée au fichier et de la quantité d'espace libre actuellement disponible sur le volume.  
  
 Les stratégies d'utilisation du stockage peuvent être configurées pour les fichiers de données et pour les fichiers journaux. Pour afficher ou modifier les seuils de la stratégie d’utilisation du stockage pour les fichiers, cliquez sur le lien **Stratégie Fichiers** au bas du volet Utilisation du stockage. Pour afficher ou modifier les seuils de la stratégie d’utilisation du stockage pour un volume de stockage, cliquez sur le lien **Stratégie Volumes** au bas du volet Utilisation du stockage.  
  
 Pour remplacer les seuils de stratégie par défaut, cliquez sur la case d’option pour **Remplacer la stratégie par défaut**, spécifiez des valeurs pour les limites supérieures et inférieures, puis cliquez sur **OK**.  
  
 Pour plus d’informations sur la modification de la tolérance des violations de stratégie, consultez [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;Utilitaire SQL Server&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
 Onglet Détails des propriétés  
 Les détails de propriété répertoriés pour les instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] incluent les catégories suivantes :  
  
-   Nom du processeur :  
  
-   Vitesse du processeur (MHz) :  
  
-   Nombre de processeurs :  
  
-   Mémoire physique (Mo) :  
  
-   Version du système d'exploitation :  
  
-   Version de SQL Server :  
  
-   Édition de SQL Server :  
  
-   Cluster : (True ou False)  
  
-   Répertoire de sauvegarde :  
  
-   Classement :  
  
-   En respectant la casse : (True ou False)  
  
-   Langue :  
  
## <a name="see-also"></a>Voir aussi  
 [Détails des applications de la couche Données déployées &#40;utilitaire SQL Server&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)   
 [Tableau de bord utilitaire &#40;utilitaire SQL Server&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [Surveiller des instances de SQL Server dans l'utilitaire SQL Server](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Résolution des problèmes liés à l’utilitaire SQL Server](../../2014/database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
