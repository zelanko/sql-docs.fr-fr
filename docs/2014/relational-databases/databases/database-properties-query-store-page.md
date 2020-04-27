---
title: Propriétés de la base de données (page Magasin de requêtes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.querystore.f1
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 51116c993cf795e6390ac463f67f75e2ddff3e0e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62917200"
---
# <a name="database-properties-query-store-page"></a>Propriétés de la base de données (page Magasin de requêtes)
  Accédez à cette page depuis la base de données principale et utilisez-la pour configurer et modifier les propriétés du magasin de requêtes de la base de données. Ces options peuvent également être configurées à l'aide des [options ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options). Pour plus d'informations sur le magasin de requêtes, consultez [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).  
  
||  
|-|  
|**S'applique à**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
## <a name="options"></a>Options  
 Activer  
 Active et désactive le magasin de requêtes.  
  
 Mode d'opération  
 Les valeurs valides sont READ_ONLY et READ_WRITE. En mode READ_WRITE, le magasin de requête collecte et conserve les informations sur le plan de requête et les statistiques d'exécution. En mode READ_ONLY, les informations peuvent être lues à partir du magasin de requête, mais les nouvelles informations ne sont pas ajoutées. Si la valeur maximale de l'espace du magasin de requête allouée est épuisée, le mode d'opération du magasin de requêtes passe en READ_ONLY.  
  
 Mode d'opération (réel)  
 Obtient le mode de fonctionnement réel du magasin de requêtes.  
  
 Mode d'opération (demandé)  
 Obtient et définit le mode de fonctionnement souhaité du magasin de requêtes.  
  
 Intervalle de vidange des données (minutes)  
 Détermine la fréquence à laquelle les données écrites sur le magasin de requête magasin est conservée sur le disque. Pour optimiser les performances, les données collectées par le magasin de requête sont écrites de façon asynchrone sur le disque. La fréquence à laquelle ce transfert asynchrone se produit est configurée.  
  
 Intervalle de collecte des statistiques  
 Obtient et définit la valeur de l'intervalle de collecte des statistiques.  
  
 Taille maximale (Mo)  
 Obtient et définit l'espace total alloué au magasin de requêtes.  
  
 Seuil de requêtes périmées (jours)  
 Obtient et définit le seuil de requêtes périmées. Configurez l'argument STALE_QUERY_THRESHOLD_DAYS pour spécifier le nombre de jours de conservation des données dans le magasin de requêtes.  
  
 Purger les données de requête  
 Supprime le contenu du magasin de requêtes.  
  
 Graphiques à secteurs  
 Le graphique de gauche montre la consommation totale du fichier de base de données sur le disque et la partie du fichier qui est remplie avec les données du magasin de requêtes.  
  
 Le graphique de droite montre la partie du quota de magasin de requêtes actuellement utilisé. Notez que le quota n'est pas affiché dans le graphique de gauche. Le quota peut dépasser la taille actuelle de la base de données.  
  
## <a name="remarks"></a>Notes  
 La fonctionnalité de magasin de requêtes fournit aux administrateurs de bases de données des informations sur le choix de plan de requête et les performances. Elle simplifie la résolution des problèmes de performances en vous permettant de trouver rapidement les différences de performances provoquées par un changement de plan de requête. La fonctionnalité capture automatiquement l'historique des requêtes, des plans et des statistiques d'exécution et les conserve à des fins de consultation. Elle sépare les données en périodes, ce qui vous permet de voir les modèles d'utilisation de base de données et de comprendre à quel moment le changement de plan de requête a eu lieu sur le serveur. Le magasin de requêtes peut être configuré à l'aide de la page de propriétés de la base de données du magasin de requêtes ou de l’option [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) . Le magasin de requêtes présente les informations via la boîte de dialogue [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] . Pour plus d'informations sur le magasin de requêtes, consultez [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Magasin des requêtes des procédures stockées &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql)   
 [Affichages catalogue du magasin de requêtes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/query-store-catalog-views-transact-sql)  
  
  
