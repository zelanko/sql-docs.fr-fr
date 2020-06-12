---
title: Utiliser des vues de gestion dynamique (DMV) pour surveiller Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e3ea13dc58815e82d82a3f3b5ffdd3c5d666d7e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543714"
---
# <a name="use-dynamic-management-views-dmvs-to-monitor-analysis-services"></a>Utiliser des vues de gestion dynamique (DMV) pour surveiller Analysis Services
  Les vues de gestion dynamique (DMV) d'Analysis Services sont des structures de requête qui exposent des informations sur les opérations de serveur local et l'intégrité du serveur. La structure de requête est une interface vers des ensembles de lignes de schéma qui retournent des métadonnées et des informations d'analyse relatives à une instance Analysis Services.  
  
 Pour la plupart des requêtes DMV, vous utilisez une instruction `SELECT` et le schéma `$System` avec un ensemble de lignes de schéma XML/A.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Les requêtes DMV retournent des informations sur l'état du serveur actif au moment de l'exécution de la requête. Pour surveiller les opérations en temps réel, utilisez plutôt le suivi. Pour plus d’informations, consultez [Utiliser SQL Server Profiler pour contrôler Analysis Services](use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Cette rubrique contient les sections suivantes :  
  
 [Avantages de l'utilisation des requêtes DMV](#bkmk_ben)  
  
 [Exemples et scénarios](#bkmk_ex)  
  
 [Syntaxe de la requête](#bkmk_syn)  
  
 [Outils et autorisations](#bkmk_tools)  
  
 [Référence DMV](#bkmk_ref)  
  
##  <a name="benefits-of-using-dmv-queries"></a><a name="bkmk_ben"></a>Avantages de l’utilisation des requêtes DMV  
 Les requêtes DMV retournent des informations sur les opérations et la consommation des ressources qui ne sont pas accessibles par d'autres biais.  
  
 Les requêtes DMV sont une alternative à l'exécution des commandes Discover XML/A. Pour la plupart des administrateurs, l'écriture d'une requête DMV est plus simple car la syntaxe de la requête est basée sur le langage SQL. En outre, le jeu de résultats est retourné dans un format tabulaire qui est plus facile à lire et à copier.  
  
##  <a name="examples-and-scenarios"></a><a name="bkmk_ex"></a>Exemples et scénarios  
 Une requête DMV peut vous aider à répondre à des questions sur les sessions et les connexions actives, ainsi que sur les objets qui consomment le plus d'UC ou de mémoire à un moment précis. Cette section fournit des exemples pour les scénarios d'utilisation de requêtes DMV les plus courants. Vous pouvez également consulter le [Guide des opérations de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) pour plus d’informations sur l’utilisation de requêtes DMV pour surveiller une instance de serveur.  
  
 `Select * from $System.discover_object_activity` /** Cette requête rend compte de l’activité des objets depuis le dernier démarrage du service. Pour obtenir des exemples de requêtes basées sur cette vue DMV, consultez [New System.Discover_Object_Activity](https://go.microsoft.com/fwlink/?linkid=221322).  
  
 `Select * from $System.discover_object_memory_usage` /** Cette requête rend compte de la consommation de mémoire par objet.  
  
 `Select * from $System.discover_sessions` /** Cette requête rend compte des sessions actives, notamment de la session utilisateur et de sa durée.  
  
 `Select * from $System.discover_locks` /** Cette requête retourne un instantané des verrous utilisés à un moment précis.  
  
##  <a name="query-syntax"></a><a name="bkmk_syn"></a>Syntaxe de la requête  
 Le moteur d'interrogation des vues DMV est l'analyseur d'exploration de données. La syntaxe de requête DMV repose sur l’instruction [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
 Bien que la syntaxe de requête DMV soit basée sur une instruction SQL SELECT, elle ne prend pas en charge la syntaxe complète d'une instruction SELECT. Notez que JOIN, GROUP BY, LIKE, CAST et CONVERT ne sont pas pris en charge.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
 L'exemple suivant pour DISCOVER_CALC_DEPENDENCY illustre l'utilisation de la clause WHERE pour la fourniture d'un paramètre à la requête :  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
 Sinon, pour les ensembles de lignes de schéma soumis à des restrictions, la requête doit inclure la fonction SYSTEMRESTRICTSCHEMA. L'exemple suivant retourne des métadonnées CSDL sur les modèles tabulaires exécutés sur un serveur en mode tabulaire. Notez que CATALOG_NAME respecte la casse :  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="tools-and-permissions"></a><a name="bkmk_tools"></a>Outils et autorisations  
 Vous devez disposer d'autorisations d'administrateur système sur l'instance Analysis Services pour interroger une vue DMV.  
  
 Vous pouvez utiliser toute application cliente prenant en charge les requêtes MDX ou DMX, notamment SQL Server Management Studio, un rapport Reporting Services ou un tableau de bord PerformancePoint.  
  
 Pour exécuter une requête DMV à partir de Management Studio, connectez-vous à l’instance à interroger, puis cliquez sur **Nouvelle requête**. Vous pouvez exécuter une requête à partir d'une fenêtre de requête MDX ou DMX.  
  
##  <a name="dmv-reference"></a><a name="bkmk_ref"></a>Référence DMV  
 Tous les ensembles de lignes de schéma n'ont pas d'interface DMV. Pour retourner la liste de tous les ensembles de lignes de schéma qui peuvent être interrogés à l'aide d'une vue de gestion dynamique, exécutez la requête suivante.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  Si une DMV n’est pas disponible pour un ensemble de lignes donné, le serveur retourne l’erreur suivante : « le type de la \<schemarowset> demande n’a pas été reconnu par le serveur ». Toutes les autres erreurs signalent des problèmes de syntaxe.  
  
|Ensemble de lignes|Description|  
|------------|-----------------|  
|[Ensemble de lignes DBSCHEMA_CATALOGS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-catalogs-rowset)|Retourne la liste des bases de données Analysis Services sur la connexion actuelle.|  
|[Ensemble de lignes DBSCHEMA_COLUMNS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-columns-rowset)|Retourne la liste de toutes les colonnes dans la base de données active. Vous pouvez utiliser cette liste pour construire une requête DMV.|  
|[Ensemble de lignes de schéma DBSCHEMA_PROVIDER_TYPES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-provider-types-rowset)|Retourne les propriétés relatives aux types de données de base pris en charge par le fournisseur de données OLE DB.|  
|[Ensemble de lignes DBSCHEMA_TABLES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-tables-rowset)|Retourne la liste de toutes les tables dans la base de données active. Vous pouvez utiliser cette liste pour construire une requête DMV.|  
|[DISCOVER_CALC_DEPENDENCY, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset)|Retourne la liste des colonnes et des tables utilisées dans un modèle qui ont des dépendances sur d'autres colonnes et tables.|  
|[Ensemble de lignes DISCOVER_COMMAND_OBJECTS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-command-objects-rowset)|Fournit des informations sur l'activité et l'utilisation des ressources par les objets actuellement utilisés par la commande référencée.|  
|[Ensemble de lignes DISCOVER_COMMANDS](https://docs.microsoft.com/analysis-services/instances/analysis-services-schema-rowsets)|Fournit des informations sur l'activité et l'utilisation des ressources relatives à la commande en cours d'exécution.|  
|[Ensemble de lignes DISCOVER_CONNECTIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-connections-rowset)|Fournit à Analysis Services des informations sur l'activité et l'utilisation des ressources relatives aux connexions ouvertes.|  
|[DISCOVER_CSDL_METADATA, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)|Retourne des informations sur un modèle tabulaire.<br /><br /> Nécessite l'ajout de SYSTEMRESTRICTSCHEMA et de paramètres supplémentaires.|  
|[Ensemble de lignes DISCOVER_DB_CONNECTIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-db-connections-rowset)|Échange des informations sur l'activité et l'utilisation des ressources relatives aux connexions ouvertes entre Analysis Services et les sources de données externes, par exemple au cours des opérations de traitement et d'importation.|  
|[DISCOVER_DIMENSION_STAT, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-dimension-stat-rowset)|Retourne les attributs d'une dimension ou les colonnes d'une table, selon le type de modèle.|  
|[Ensemble de lignes DISCOVER_ENUMERATORS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-enumerators-rowset)|Retourne des métadonnées sur les énumérateurs pris en charge pour une source de données spécifique.|  
|[Ensemble de lignes DISCOVER_INSTANCES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/discover-instances-rowset)|Retourne des informations sur l'instance spécifiée.<br /><br /> Nécessite l'ajout de SYSTEMRESTRICTSCHEMA et de paramètres supplémentaires.|  
|[Ensemble de lignes DISCOVER_JOBS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-jobs-rowset)|Retourne des informations sur les travaux en cours.|  
|[Ensembles de lignes DISCOVER_KEYWORDS &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-keywords-rowset-xmla)|Retourne la liste des mots clés réservés.|  
|[Ensemble de lignes DISCOVER_LITERALS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-literals-rowset)|Retourne la liste des littéraux pris en charge par XMLA, y compris les types de données et les valeurs.|  
|[Ensemble de lignes DISCOVER_LOCKS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-locks-rowset)|Retourne un instantané des verrous utilisés à un instant précis.|  
|[DISCOVER_MEMORYGRANT, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-memorygrant-rowset)|Retourne des informations sur la mémoire allouée par Analysis Services au démarrage.|  
|[DISCOVER_MEMORYUSAGE, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-memoryusage-rowset)|Affiche l'utilisation de la mémoire par des objets spécifiques.|  
|[Ensemble de lignes DISCOVER_OBJECT_ACTIVITY](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-object-activity-rowset)|Rend compte de l'activité des objets depuis le dernier démarrage du service.|  
|[Ensemble de lignes DISCOVER_OBJECT_MEMORY_USAGE](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-object-memory-usage-rowset)|Rend compte de la consommation de mémoire par objet.|  
|[DISCOVER_PARTITION_DIMENSION_STAT, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-partition-dimension-stat-rowset)|Fournit des informations sur les attributs d'une dimension.<br /><br /> Nécessite l'ajout de SYSTEMRESTRICTSCHEMA et de paramètres supplémentaires.|  
|[DISCOVER_PARTITION_STAT, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-partition-stat-rowset)|Fournit des informations sur les partitions dans une dimension, une table ou un groupe de mesures.<br /><br /> Nécessite l'ajout de SYSTEMRESTRICTSCHEMA et de paramètres supplémentaires.|  
|[DISCOVER_PERFORMANCE_COUNTERS, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-performance-counters-rowset)|Répertorie les colonnes utilisées dans un compteur de performance.<br /><br /> Nécessite l'ajout de SYSTEMRESTRICTSCHEMA et de paramètres supplémentaires.|  
|[Ensemble de lignes DISCOVER_PROPERTIES](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-properties-rowset)|Retourne des informations sur les propriétés prises en charge par XMLA pour la source de données spécifiée.|  
|[Ensemble de lignes DISCOVER_SCHEMA_ROWSETS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-schema-rowsets-rowset)|Retourne des noms, des restrictions, des descriptions et d'autres informations pour toutes les valeurs d'énumération prises en charge par XMLA.|  
|[Ensemble de lignes DISCOVER_SESSIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-sessions-rowset)|Rend compte des sessions actives, notamment l'utilisateur de la session et la durée.|  
|[Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-table-column-segments-rowset)|Fournit des informations au niveau de la colonne et du segment concernant les tables de stockage utilisées par une base de données Analysis Services exécutée en mode tabulaire ou SharePoint.|  
|[Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMNS](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-table-columns-rowset)|Permet au client de déterminer l'affectation de colonnes aux tables de stockage utilisées par une base de données Analysis Services exécutée en mode tabulaire ou SharePoint.|  
|[Ensemble de lignes DISCOVER_STORAGE_TABLES](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-tables-rowset)|Retourne des informations sur les tables utilisées pour le stockage de modèles dans une base de données model tabulaire.|  
|[DISCOVER_TRACE_COLUMNS, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-columns-rowset)|Retourne une description XML des colonnes disponibles dans une trace.|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset)|Retourne le nom et les informations de version du fournisseur.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-event-categories-rowset)|Retourne la liste des catégories disponibles.|  
|[DISCOVER_TRACES, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-traces-rowset)|Retourne la liste des traces actives sur la connexion actuelle.|  
|[DISCOVER_TRANSACTIONS, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-transactions-rowset)|Retourne la liste des transactions actives sur la connexion actuelle.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION, ensemble de lignes](../dev-guide/discover-xevent-trace-definition-rowset.md)|Retourne la liste des traces xevent actives sur la connexion actuelle.|  
|[Ensemble de lignes DMSCHEMA_MINING_COLUMNS](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-columns-rowset)|Répertorie les colonnes de tous les modèles d'exploration de données disponibles sur la connexion actuelle.|  
|[Ensemble de lignes DMSCHEMA_MINING_FUNCTIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-functions-rowset)|Retourne la liste des fonctions prises en charge par les algorithmes d'exploration de données sur le serveur.|  
|[Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)|Retourne un ensemble de lignes composé de colonnes qui décrivent le modèle actuel.|  
|[Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT_PMML](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset)|Retourne un ensemble de lignes composé de colonnes qui décrivent le modèle actuel au format PMML.|  
|[Ensemble de lignes DMSCHEMA_MINING_MODEL_XML](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset)|Retourne un ensemble de lignes composé de colonnes qui décrivent le modèle actuel au format PMML.|  
|[Ensemble de lignes DMSCHEMA_MINING_MODELS](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-models-rowset)|Retourne la liste des modèles d'exploration de données dans la base de données active.|  
|[Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset)|Retourne la liste des paramètres des algorithmes sur le serveur.|  
|[Ensemble de lignes DMSCHEMA_MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)|Fournit la liste des algorithmes d'exploration de données disponibles sur le serveur.|  
|[Ensemble de lignes DMSCHEMA_MINING_STRUCTURE_COLUMNS](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset)|Retourne la liste de toutes les colonnes de tous les modèles d'exploration de données disponibles dans la connexion actuelle.|  
|[Ensemble de lignes DMSCHEMA_MINING_STRUCTURES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-structures-rowset)|Répertorie les structures d'exploration de données disponibles dans la connexion actuelle.|  
|[Ensemble de lignes MDSCHEMA_CUBES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-cubes-rowset)|Retourne des informations sur les cubes définis dans la base de données active.|  
|[Ensemble de lignes MDSCHEMA_DIMENSIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset)|Retourne des informations sur les dimensions définies dans la base de données active.|  
|[Ensemble de lignes MDSCHEMA_FUNCTIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-functions-rowset)|Retourne la liste des fonctions disponibles pour les applications clientes connectées à la base de données.|  
|[Ensemble de lignes MDSCHEMA_HIERARCHIES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset)|Retourne des informations sur les hiérarchies définies dans la base de données active.|  
|[Ensemble de lignes MDSCHEMA_INPUT_DATASOURCES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset)|Retourne des informations sur les objets source de données définis dans la base de données active.|  
|[Ensemble de lignes MDSCHEMA_KPIS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-kpis-rowset)|Retourne des informations sur les indicateurs de performance clés (KPI) définis dans la base de données active.|  
|[Ensemble de lignes MDSCHEMA_LEVELS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-levels-rowset)|Retourne des informations sur les niveaux au sein des hiérarchies définies dans la base de données active.|  
|[Ensemble de lignes MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas/e6399481-a289-41f3-94d2-e081bf29e094)|Répertorie la dimension des groupes de mesures.|  
|[Ensemble de lignes MDSCHEMA_MEASUREGROUPS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset)|Retourne la liste de groupes de mesures dans la connexion actuelle.|  
|[Ensemble de lignes MDSCHEMA_MEASURES](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas/ab8e721f-9b9c-4ba1-b105-37a5f200d67c)|Retourne la liste des mesures dans la connexion actuelle.|  
|[Ensemble de lignes MDSCHEMA_MEMBERS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)|Retourne la liste de tous les membres de la connexion actuelle, répertoriés par base de données, cube et dimension.|  
|[Ensemble de lignes MDSCHEMA_PROPERTIES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset)|Retourne le nom complet de chaque propriété, avec le type de propriété, le type de données et d'autres métadonnées.|  
|[Ensemble de lignes MDSCHEMA_SETS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-sets-rowset)|Retourne la liste des ensembles qui sont définis dans la connexion actuelle.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server 2008 R2 Analysis Services Guide des opérations](https://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [Nouveau System. Discover_Object_Activity](https://go.microsoft.com/fwlink/?linkid=221322)   
 [Nouvelle fonction SYSTEMRESTRICTEDSCHEMA pour les ensembles de lignes restreints et les vues de gestion dynamique](https://go.microsoft.com/fwlink/?LinkId=231885)  
  
  
