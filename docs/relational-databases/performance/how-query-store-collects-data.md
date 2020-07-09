---
title: Comment le magasin de requêtes collecte les données | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store, data collection
ms.assetid: 8d5eec36-0013-480a-9c11-183e162e4c8e
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||= azure-sqldw-latest||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 23b3d551d11ee09875f49be1bd553adcb9d9759c
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86005989"
---
# <a name="how-query-store-collects-data"></a>Comment le magasin de requêtes collecte les données
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

Le magasin de requêtes SQL Server fonctionne de manière similaire à un enregistreur de données de vol et collecte constamment des informations de compilation et d’exécution relatives aux requêtes et aux plans. Les données relatives aux requêtes sont conservées dans les tables internes et présentées aux utilisateurs via différentes vues.
  
## <a name="views"></a>Les vues 
 Le diagramme suivant montre les affichages du magasin de requêtes et leurs relations logiques avec les informations de compilation présentées sous la forme d'entités bleues :
  
 ![Vues des processus du Magasin des requêtes](../../relational-databases/performance/media/query-store-process-2views.png "query-store-process-2views")  
**Description des vues**  
  
|Affichage|Description|  
|----------|-----------------|  
|**sys.query_store_query_text**|Présente les textes de requêtes uniques exécutés sur la base de données. Les commentaires et les espaces avant et après le texte de requête sont ignorés. Les commentaires et les espaces au sein du texte ne sont pas ignorés. Chaque instruction du lot génère une entrée de texte de requête distincte.|  
|**sys.query_context_settings**|Présente les combinaisons uniques des paramètres affectant le plan selon lesquels les requêtes sont exécutées. Un même texte de requête exécuté avec d’autres paramètres affectant le plan produit une entrée de requête distincte dans le magasin de requêtes, car `context_settings_id` fait partie de la clé de requête.|  
|**sys.query_store_query**|Entrées de requête suivies et forcées séparément dans le magasin de requêtes. Un texte de requête individuel peut produire plusieurs entrées de requête s’il est exécuté selon différents paramètres de contexte ou à l’extérieur/à l’intérieur de modules [!INCLUDE[tsql](../../includes/tsql-md.md)] différents, tels que des procédures stockées et des déclencheurs.|  
|**sys.query_store_plan**|Présente le plan estimé pour la requête avec les statistiques de compilation. Un plan stocké est équivalent à ce que vous pouvez obtenir avec `SET SHOWPLAN_XML ON`.|  
|**sys.query_store_runtime_stats_interval**|Le magasin de requêtes divise le temps en périodes générées automatiquement (intervalles) et stocke les statistiques agrégées sur cet intervalle pour chaque plan exécuté. La taille de l’intervalle est contrôlée par l’option de configuration **Intervalle de collecte des statistiques** (dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]) ou `INTERVAL_LENGTH_MINUTES` à l’aide des [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).|  
|**sys.query_store_runtime_stats**|Statistiques d'exécution agrégées pour les plans exécutés. Toutes les métriques capturées sont exprimées sous la forme de quatre fonctions statistiques : Moyenne, Minimum, Maximum et Écart type.|  
  
 Pour plus d’informations sur les vues du magasin de requêtes, consultez la section « Vues, fonctions et procédures associées » de [Surveillance des performances à l’aide du magasin de requêtes](monitoring-performance-by-using-the-query-store.md). 
  
## <a name="query-processing"></a>Traitement des requêtes
 Le magasin de requêtes interagit avec le pipeline de traitement des requêtes sur les points clés suivants :
  
1.  Lorsqu’une requête est compilée pour la première fois, le texte de la requête et le plan initial sont envoyés au magasin de requêtes.
  
2.  Lorsque la requête est recompilée, le plan est mis à jour dans le magasin de requêtes. Si un nouveau plan est créé, le magasin de requêtes ajoute l’entrée du nouveau plan pour la requête et conserve les précédentes avec leurs statistiques d’exécution.
  
3.  Lors de l’exécution des requêtes, les statistiques d’exécution sont envoyées au magasin de requêtes. Le magasin de requêtes conserve des statistiques agrégées précises pour chaque plan exécuté dans l'intervalle actuellement actif. 
  
4.  Lors des phases de compilation et de vérification pour recompilation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détermine s’il existe un plan dans le magasin de requêtes à appliquer pour la requête en cours d’exécution. S’il existe un plan forcé différent du plan figurant dans le cache de procédures, la requête est recompilée. Cela s’effectue de la même façon que si l’INDICATEUR PLAN était appliqué à cette requête. Ce processus se produit de façon transparente pour l'application utilisateur. 
  
 Le diagramme suivant illustre les points d’intégration expliqués dans les étapes précédentes :
  
 ![Processus du Magasin des requêtes](../../relational-databases/performance/media/query-store-process-2processor.png "query-store-process-2processor") 

## <a name="remarks"></a>Notes
 Pour réduire la surcharge d’E/S, les nouvelles données sont capturées en mémoire. Les opérations d’écriture sont mises en file d’attente et vidées sur le disque par la suite. Les informations de requête et de plan, indiquées en tant que Magasin de plans dans le schéma ci-dessous, sont vidées avec une latence minimale. Les statistiques d’exécution, indiquées en tant que Statistiques du runtime, sont conservées en mémoire pendant une période définie avec l’option `DATA_FLUSH_INTERVAL_SECONDS` de l’instruction `SET QUERY_STORE`. Vous pouvez utiliser la boîte de dialogue [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] Magasin des requêtes pour entrer une valeur pour **Intervalle de vidage des données (minutes)** , qui est convertie en secondes en interne. 
  
 ![Plan de processus du Magasin des requêtes](../../relational-databases/performance/media/query-store-process-3.png "query-store-process-3plan") 
  
 Si le système se bloque ou qu’un arrêt se produit lors de l’utilisation de l’[indicateur de trace 7745](../../relational-databases/performance/best-practice-with-the-query-store.md#Recovery), le magasin de requêtes peut perdre les données d’exécution qui ont été collectées mais qui ne sont pas encore persistantes, jusqu’à une fenêtre de temps définie avec `DATA_FLUSH_INTERVAL_SECONDS`. Nous recommandons la valeur par défaut de 900 secondes (15 minutes) en tant qu’équilibre entre les performances de capture de requête et la disponibilité des données.
 
 > [!IMPORTANT] 
 > La limite **Taille maximale (Mo)** n’est pas strictement appliquée. La taille de stockage est vérifiée seulement quand le Magasin des requêtes écrit des données sur le disque. Cet intervalle est défini par la valeur **Intervalle de vidage des données**. Si le Magasin des requêtes a enfreint la limite de taille maximale entre les vérifications de taille de stockage, il passe en mode lecture seule. Si l’option **Mode de nettoyage basé sur la taille** est activée, le mécanisme de nettoyage permettant d’appliquer la limite de taille maximale est également déclenché.
 
 > [!NOTE]
 > Si le système est soumis à une sollicitation élevée de la mémoire, les statistiques d’exécution peuvent être vidées sur le disque plus tôt que ce qui est défini avec `DATA_FLUSH_INTERVAL_SECONDS`.
 
 Lors de la lecture des données du magasin de requêtes, les données en mémoire et sur disque sont unifiées en toute transparence. 
 
 Si une session est arrêtée ou que l’application cliente redémarre ou se plante, les statistiques de requêtes ne seront pas enregistrées. 
  
 ![Informations sur le plan de processus du Magasin des requêtes](../../relational-databases/performance/media/query-store-process-4planinfo.png "query-store-process-4planinfo")    

## <a name="see-also"></a>Voir aussi
 [Surveillance des performances à l’aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [Bonnes pratiques relatives au magasin de requêtes](../../relational-databases/performance/best-practice-with-the-query-store.md)  
 [Affichages catalogue du magasin de requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md) 
  
  
