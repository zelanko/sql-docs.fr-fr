---
title: XML for Analysis Schema Rowsets | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2f5cb613a916f2cff4ec8aca3bb67fc9c14d1b10
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis Schema Rowsets
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML pour le fournisseur Analysis (XMLA) inclut des ensembles de lignes de schéma qui retournent des métadonnées sur l’état du serveur, d’activité et d’objets. La récupération de métadonnées est nécessaire si vous développez une application cliente qui se connecte à un modèle Analysis Services dont la structure et les caractéristiques sont variables.  
  
 Les ensembles de lignes de schéma fournissent également l'analyse des processus internes et les opérations qui peuvent vous aider à analyser le serveur et à résoudre les problèmes. Pour une meilleure prise en charge des tâches d'administration ad hoc, vous pouvez exécuter une requête de vue de gestion dynamique (DMV) sur la plupart des ensembles de lignes de schéma. Les requêtes DMV retournent des résultats dans un format lisible et tabulaire que vous pouvez afficher dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
 Le tableau suivant répertorie et décrit chaque ensemble de lignes de schéma XMLA, et identifie s'il retourne des informations spécifiques aux modèles de données tabulaires.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Ensemble de lignes<sup>1</sup>| Description|  
|------------------------|-----------------|  
|[DISCOVER_CALC_DEPENDENCY, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)|Retourne des informations sur les dépendances entre les tables, colonnes, mesures et formules de colonne calculée.<br /><br /> S’applique aux modèles tabulaires déployés sur une instance Analysis Services et [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modèles dans les classeurs Excel qui s’exécutent dans un environnement SharePoint.|  
|[DISCOVER_CONNECTIONS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-connections-rowset.md)|Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes sur le serveur.|  
|[DISCOVER_COMMAND_OBJECTS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-command-objects-rowset.md)|Fournit des informations sur l'activité et l'utilisation des ressources des objets actuellement utilisés par la commande référencée.|  
|[DISCOVER_COMMANDS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-commands-rowset.md)|Fournit des informations sur l'activité et l'utilisation des ressources des dernières commandes exécutées ou des commandes en cours d'exécution sur les connexions ouvertes sur le serveur.|  
|[DISCOVER_CSDL_METADATA, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)|Retourne une définition XML d’une source de données à un client qui peut consommer un tabulaire ou [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] de modèle et présente les données sources dans le cadre d’un rapport.<br /><br /> S’applique aux modèles tabulaires déployés sur une instance Analysis Services et [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modèles dans les classeurs Excel qui s’exécutent dans un environnement SharePoint.|  
|[DISCOVER_DATASOURCES, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)|Retourne la liste des sources de données du fournisseur XMLA qui sont disponibles sur le serveur ou le service Web.|  
|[DISCOVER_DB_CONNECTIONS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-db-connections-rowset.md)|Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes du serveur à une base de données.|  
|[DISCOVER_DIMENSION_STAT, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-dimension-stat-rowset.md)|Retourne des statistiques sur la dimension spécifiée.|  
|[DISCOVER_ENUMERATORS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)|Retourne une liste des noms, types de données et valeurs d'énumération d'énumérateurs pris en charge par le fournisseur XMLA pour une source de données spécifique.|  
|[DISCOVER_JOBS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-jobs-rowset.md)|Fournit des informations sur les travaux actifs exécutés sur le serveur.|  
|[Ensemble de lignes DISCOVER_KEYWORDS &#40; XMLA &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)|Retourne des informations sur les mots clés réservés par le fournisseur XMLA.|  
|[DISCOVER_LITERALS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)|Retourne des informations sur les littéraux pris en charge par le fournisseur XMLA, y compris les types de données et les valeurs.|  
|[DISCOVER_LOCATIONS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-locations-rowset.md)|Retourne des informations sur le contenu d'un fichier de sauvegarde.|  
|[DISCOVER_LOCKS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-locks-rowset.md)|Fournit des informations sur les verrous actuellement en place sur le serveur.|  
|[DISCOVER_MEMORYGRANT, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-memorygrant-rowset.md)|Retourne la liste des allocations de quotas de mémoire interne qui sont prises par les travaux en cours d'exécution sur le serveur.|  
|[DISCOVER_MEMORYUSAGE, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-memoryusage-rowset.md)|Retourne les statistiques d'utilisation de la mémoire pour plusieurs objets alloués par le serveur.|  
|[DISCOVER_OBJECT_ACTIVITY, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-object-activity-rowset.md)|Fournit l'utilisation des ressources par objet depuis le démarrage du service.|  
|[DISCOVER_OBJECT_MEMORY_USAGE, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-object-memory-usage-rowset.md)|Fournit des informations sur les ressources mémoire utilisées par les objets.|  
|[DISCOVER_PARTITION_DIMENSION_STAT, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|Retourne des statistiques sur la dimension associée à une partition.|  
|[DISCOVER_PARTITION_STAT, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-partition-stat-rowset.md)|Retourne des statistiques sur les agrégations dans une partition particulière.|  
|[DISCOVER_PERFORMANCE_COUNTERS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-performance-counters-rowset.md)|Retourne la valeur d'un ou de plusieurs compteurs de performance spécifiés.|  
|[DISCOVER_PROPERTIES, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)|Retourne une liste d'informations et valeurs sur les propriétés standard et spécifiques au fournisseur prises en charge par le fournisseur XMLA pour la source de données spécifiée.|  
|[DISCOVER_SCHEMA_ROWSETS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)|Retourne les noms, restrictions, description et d'autres informations pour toutes les valeurs d'énumération et toutes les valeurs d'énumération supplémentaires spécifiques au fournisseur prises en charge par le fournisseur XMLA.|  
|[DISCOVER_SESSIONS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-sessions-rowset.md)|Fournit des informations sur l'activité et l'utilisation des ressources des sessions actuellement ouvertes sur le serveur.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|Fournit des informations au niveau de la colonne et du segment sur les tables de stockage utilisé par un tableau ou [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] base de données.<br /><br /> S’applique aux modèles tabulaires déployés sur une instance Analysis Services et [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modèles dans les classeurs Excel qui s’exécutent dans un environnement SharePoint.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-storage-table-columns-rowset.md)|Permet au client de déterminer l’affectation de colonnes aux tables de stockage utilisés par un tableau ou [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] base de données.<br /><br /> S’applique aux modèles tabulaires déployés sur une instance Analysis Services et [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modèles dans les classeurs Excel qui s’exécutent dans un environnement SharePoint.|  
|[DISCOVER_STORAGE_TABLES, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-storage-tables-rowset.md)|Retourne des informations sur les tables utilisées dans un modèle.<br /><br /> S’applique aux modèles tabulaires déployés sur une instance Analysis Services et [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modèles dans les classeurs Excel qui s’exécutent dans un environnement SharePoint.|  
|[DISCOVER_TRACE_COLUMNS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-trace-columns-rowset.md)|Décrit les colonnes de trace fournies par le fournisseur de trace.|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|Retourne des informations de base sur le fournisseur de trace, telles que son nom et sa description.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-trace-event-categories-rowset.md)|Décrit les catégories d'événements fournies par le fournisseur de trace.|  
|[DISCOVER_TRACES, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)|Retourne des informations sur les traces qui s'exécutent sur un serveur.|  
|[DISCOVER_TRANSACTIONS, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-transactions-rowset.md)|Retourne l'ensemble actuel des transactions en attente sur le système.|  
|[DISCOVER_XML_METADATA, ensemble de lignes](../../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)|Retourne un document XML qui décrit un objet demandé.|  
  
 <sup>1</sup> des ensembles de schéma répertoriés ici sont pris en charge par le fournisseur de source de données MSOLAP pour le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] fournisseur XMLA.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Utiliser dynamique vues de gestion &#40; vues de gestion dynamique &#41; pour surveiller Analysis Services](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [Récupération de métadonnées à partir d’une source de données analytiques](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
