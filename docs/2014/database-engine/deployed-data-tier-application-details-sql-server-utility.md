---
title: Déployé les détails de l’Application de couche données (utilitaire SQL Server) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c76314d835c13a63f4dfcd22f9ed54b819953a49
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044791"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a>Détails des applications de la couche Données déployées (utilitaire SQL Server)
  Les informations de la vue Applications de la couche Données déployées de l'Explorateur de l'utilitaire fournissent des données d'utilisation pour les applications de la couche Données, l'historique de l'utilisation du processeur, des détails sur l'utilisation du stockage au niveau du fichier, ainsi que la capacité d'afficher et de mettre à jour des seuils de stratégie. Les seuils de stratégie peuvent être contrôlés au niveau de l'application de la couche Données pour l'utilisation du processeur et pour les fichiers des données de la base de données et les fichiers journaux. Vous pouvez également consulter les détails des propriétés des applications de la couche Données.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Mode Liste  
 Le mode Liste, dans le volet supérieur, affiche des données concernant des applications de la couche Données. Les icônes d'état d'intégrité fournissent un résumé de l'état de chaque application de la couche Données par catégorie d'utilisation :  
  
-   Coche verte (![](../../2014/database-engine/media/well-utilized.gif "Correctement exploité")) : nombre d’applications de la couche Données qui ne violent pas les stratégies d’utilisation des ressources. Les ressources sont bien utilisées.  
  
-   Flèche bas verte (![](../../2014/database-engine/media/utility-down-arrow.gif "Utilitaire, flèche bas")) : les ressources sont sous-exploitées.  
  
-   Flèche haut rouge (![](../../2014/database-engine/media/utility-up-arrow.gif "Utilitaire, flèche haut")) : les ressources sont surexploitées.  
  
 La séquence des colonnes en mode Liste peut être modifiée en les faisant glisser vers la gauche ou la droite. Les colonnes en mode Liste peuvent être ajoutées ou supprimées en cliquant avec le bouton droit sur leurs en-tête et en les sélectionnant ou désélectionnant. Le menu contextuel offre également des options de tri. Le tri peut également être activé en cliquant en haut d'un nom de colonne.  
  
 Pour accéder aux options du filtre du mode Liste de l’utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , cliquez avec le bouton droit sur le nœud **Applications de la couche Données déployées** dans le volet de navigation de l’Explorateur de l’utilitaire et sélectionnez **Filtre**. Une fois les paramètres de filtrage implémentés, le nœud **Applications de la couche Données déployées** est étiqueté **Applications de la couche Données déployées (filtré)** dans l’Explorateur de l’utilitaire. Pour plus d’informations, consultez [Paramètres de filtre &#40;Explorateur d’objets et Explorateur de l’utilitaire&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md).  
  
 Par défaut, les colonnes suivantes affichent les informations d'état d'intégrité de chaque application de la couche Données.  
  
-   Nom : le nom de l'application de la couche Données.  
  
-   Processeur de l'application : affiche l'état d'intégrité de l'utilisation du processeur pour cette application de la couche Données. L'état d'intégrité de ce paramètre est déterminé en fonction de la stratégie d'utilisation du processeur définie pour l'application de la couche Données et du paramètre de configuration de la stratégie d'évaluation des ressources volatiles. Pour plus d’informations, consultez [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Pour consulter l’historique de l’utilisation du processeur pour cette application de la couche Données ou pour afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du processeur**.  
  
-   Processeur de l'ordinateur : affiche l'état d'intégrité de l'utilisation du processeur de l'ordinateur. L'état d'intégrité de ce paramètre est déterminé en fonction de la stratégie d'utilisation du processeur définie pour l'ordinateur et du paramètre de configuration de la stratégie d'évaluation des ressources volatiles. Pour plus d’informations, consultez [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md).  
  
     Pour consulter l’historique de l’utilisation du processeur pour cette application de la couche Données ou pour afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du processeur**.  
  
-   Espace de fichier : affiche un résumé des états d'intégrité de l'utilisation de l'espace de fichier pour chaque application de la couche Données.  
  
    -   Coche verte : les états d'intégrité de tous les groupes de fichiers et du groupe de fichier journal ne sont ni surexploités ni sous-exploités.  
  
    -   Flèche bas verte : l'état d'intégrité d'au moins un groupe de fichiers ou du groupe de fichiers journaux est sous-exploité et aucun groupe de fichiers ou groupe de fichiers journaux n'est surexploité.  
  
    -   Flèche haut rouge : l'état d'intégrité d'au moins un groupe de fichiers ou du groupe de fichier journal est surexploité. Notez que si la base de données se trouve dans l'état « urgence », l'état d'intégrité affiche l'espace de fichier journal surexploité.  
  
     Pour afficher ou modifier les limites de la stratégie d’espace de fichier, cliquez sur l’onglet **Utilisation du stockage** .  
  
-   Espace de volume : affiche un résumé des états d'intégrité de l'utilisation de l'espace de volume pour tous les volumes contenant des bases de données qui appartiennent à l'application de la couche Données sélectionnée. Si l'état d'intégrité d'un des volumes est surexploité, l'état d'intégrité de l'espace de volume sera signalé en mode Liste comme étant surexploité. Si l'état d'intégrité d'un des volumes de données est sous-exploité et qu'aucun volume n'est surexploité, l'état d'intégrité de l'espace de volume sera signalé en mode Liste comme étant sous-exploité. Sinon, l'état d'intégrité de l'espace de volume sera signalé en mode Liste comme étant correctement utilisé. Pour afficher ou modifier les limites de la stratégie, cliquez sur l’onglet **Utilisation du stockage** .  
  
-   Type de stratégie : indique si les stratégies « Globales » par défaut ou des stratégies de « Substitution » personnalisées sont appliquées pour l'application de la couche Données.  
  
-   Nom de l'instance : affiche le nom de l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui héberge l'application de la couche Données.  
  
 Autres colonnes pouvant s'afficher à l'aide du menu contextuel dans la zone d'en-tête de colonne du mode Liste :  
  
-   Nom de la base de données  
  
-   Date déployée  
  
-   Digne de confiance : (True ou False)  
  
-   Classement  
  
-   Niveau de compatibilité : (par exemple, Version100)  
  
-   Chiffrement activé : (True ou False)  
  
-   Mode de récupération : (simple, complet ou en utilisant les journaux de transactions)  
  
-   Dernière heure signalée : cette colonne affiche l'heure et la date locales du processeur à l'aide du type de données datetime. Pour plus d’informations, consultez la rubrique [datetime (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=164071) dans la documentation en ligne de SQL Server. Lorsque vous utilisez le modèle d'objet de l'utilitaire, notez que SSMS utilise le type de données datetimeoffset. Pour plus d’informations, consultez la rubrique [datetimeoffset (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=141713) dans la documentation en ligne de SQL Server.  
  
 Onglet Utilisation du processeur  
 L'onglet d'utilisation du processeur affiche côte à côte des graphiques de données d'historique pour l'application de la couche Données et l'utilisation du processeur de l'ordinateur.  
  
 Le graphique affiche l'historique de l'utilisation du processeur pour l'intervalle spécifié dans les cases d'option situées sur le côté droit de la zone d'affichage. Pour modifier l'intervalle d'affichage et actualiser le jeu de données, sélectionnez une case d'option sur la liste.  
  
 Les options d'intervalle sont les suivantes :  
  
-   1 jour, affiché par intervalles de 15 minutes ;  
  
-   1 semaine, affiché par intervalles de 1 jour ;  
  
-   1 mois, affiché par intervalles de 1 semaine ;  
  
-   1 an, affiché par intervalles de 1 mois.  
  
 Onglet Utilisation du stockage  
 L'arborescence de l'onglet Utilisation du stockage montre les détails de l'utilisation de stockage pour les fichiers de base de données et les fichiers journaux qui appartiennent à l'application de la couche Données sélectionnée en mode Liste. Notez que les données temporelles affichent la date et l'heure locales du processeur à l'aide du type de données datetime. Pour plus d’informations, consultez la rubrique [datetime (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=164071) dans la documentation en ligne de SQL Server. Lorsque vous utilisez le modèle d'objet de l'utilitaire, notez que SSMS utilise le type de données datetimeoffset. Pour plus d’informations, consultez la rubrique [datetimeoffset (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=141713) dans la documentation en ligne de SQL Server.  
  
 L'affichage peut être regroupé par groupe de fichiers ou par volume. Pour utiliser l’arborescence de groupe de fichiers, sélectionnez la case d’option **Groupe de fichiers** dans la sélection **Regrouper les fichiers par :** .  
  
 Les données affichées dans le graphique d'historique de l'utilisation du stockage changent en fonction du nœud sélectionné dans l'arborescence :  
  
-   Sélectionnez le nœud groupe de fichiers pour afficher un graphique de l'espace de fichier utilisé par tous les fichiers de données appartenant au groupe de fichiers sélectionné.  
  
-   Sélectionnez le nœud fichier journal pour afficher un graphique de l'espace de fichier utilisé par tous les fichiers journaux appartenant à la base de données sélectionnée.  
  
-   Sélectionnez le nœud base de données pour afficher un graphique qui additionne l'espace de fichier utilisé par tous les fichiers de données et tous les fichiers journaux qui appartiennent à la base de données sélectionnée.  
  
 Pour consulter l'état de l'utilisation du stockage pour des fichiers individuels, cliquez sur le signe plus en regard du nom d'un fichier dans l'arborescence.  
  
 Les icônes d'état d'intégrité fournissent en un coup d'œil l'état de chaque groupe de fichiers en fonction des seuils de stratégie :  
  
-   Coche verte : l'utilisation de l'espace de fichier d'au moins un fichier de données du groupe de fichiers n'est ni surexploitée ni sous-exploitée.  
  
-   Flèche bas verte : l'utilisation de l'espace de fichier d'au moins un fichier de données du groupe de fichiers est sous-exploitée et aucun fichier du groupe de fichiers n'est surexploité.  
  
-   Flèche haut rouge : l'utilisation de l'espace de fichier de tous les fichiers de données du groupe de fichiers est surexploitée. Notez que si la base de données se trouve dans l'état « urgence », l'état d'intégrité affiche l'espace de fichier journal surexploité.  
  
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
 Les détails des propriétés répertoriés pour les applications de la couche Données incluent les catégories suivantes :  
  
-   Nom de la base de données  
  
-   Date déployée  
  
-   Digne de confiance : (True ou False)  
  
-   Classement  
  
-   Niveau de compatibilité : (par exemple, Version100)  
  
-   Chiffrement activé : (True ou False)  
  
-   Mode de récupération : (simple, complet ou en utilisant les journaux de transactions)  
  
-   Dernière heure signalée : cette colonne affiche l'heure et la date locales du processeur à l'aide du type de données datetime. Pour plus d’informations, consultez la rubrique [datetime (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=164071) dans la documentation en ligne de SQL Server. Lorsque vous utilisez le modèle d'objet de l'utilitaire, notez que SSMS utilise le type de données datetimeoffset. Pour plus d’informations, consultez la rubrique [datetimeoffset (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=141713) dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de l’instance gérée &#40;utilitaire SQL Server&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)   
 [Tableau de bord utilitaire &#40;utilitaire SQL Server&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [Surveiller des instances de SQL Server dans l'utilitaire SQL Server](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [Fonctionnalités et tâches de l’utilitaire SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  