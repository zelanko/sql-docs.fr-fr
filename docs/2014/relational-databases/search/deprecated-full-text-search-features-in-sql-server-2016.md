---
title: Fonctionnalités de recherche en texte intégral dans SQL Server 2014 dépréciées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [full-text search]
- full-text search [SQL Server], deprecated features
- full-text queries [SQL Server], proximity
ms.assetid: ab0d799c-ba79-4459-837b-c4862730dafd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a49d7db68fe32d9794e89db66020d7f90555508
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011400"
---
# <a name="deprecated-full-text-search-features-in-sql-server-2014"></a>Fonctionnalités de la recherche en texte intégral déconseillées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités de la recherche en texte intégral déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
 Vous pouvez surveiller l’utilisation des fonctionnalités déconseillées à l’aide du compteur de performance Objet **SQL Server : fonctionnalités déconseillées** et des événements de suivi. Pour plus d’informations, consultez [Utilisation des objets SQL Server](../performance-monitor/use-sql-server-objects.md).  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Fonctionnalités non prises en charge dans la prochaine version de SQL Server  
 Les fonctionnalités de recherche en texte intégral suivantes ne seront pas prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|------------------------|-----------------|------------------|----------------|  
|Propriété FULLTEXTCATALOGPROPERTY : LogSize|Aucun.|FULLTEXTCATALOGPROPERTY **('LogSize')**|211|  
|Propriété FULLTEXTSERVICEPROPERTY :<br /><br /> ConnectTimeout<br /><br /> DataTimeout|Aucun.|FULLTEXTSERVICEPROPERTY **('ConnectTimeout')**<br /><br /> FULLTEXTSERVICEPROPERTY **('DataTimeout'**)|210<br /><br /> 209|  
|sp_fulltext_catalog|CREATE FULL CATALOG<br /><br /> ALTER FULLTEXT CATALOG<br /><br /> DROP FULLTEXT CATALOG|sp_fulltext_catalog|84|  
|sp_fulltext_column<br /><br /> sp_fulltext_database<br /><br /> sp_fulltext_table|CREATE FULL INDEX<br /><br /> ALTER FULLTEXT INDEX<br /><br /> DROP FULLTEXT INDEX|sp_fulltext_column<br /><br /> sp_fulltext_database<br /><br /> sp_fulltext_table|86<br /><br /> 87<br /><br /> 85 %|  
|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_tables<br /><br /> sp_help_fulltext_tables_cursor|sys.fulltext_catalogs<br /><br /> sys.fulltext_index_columns<br /><br /> sys.fulltext_indexes|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_table<br /><br /> sp_help_fulltext_tables_cursor|88<br /><br /> 203<br /><br /> 90<br /><br /> 92<br /><br /> 93<br /><br /> 91<br /><br /> 89|  
|Valeurs d’action sp_fulltext_service : clean_up, connect_timeout et data_timeout retournent la valeur zéro|None|sp_fulltext_service @action=clean_up<br /><br /> sp_fulltext_service @action=connect_timeout<br /><br /> sp_fulltext_service @action=data_timeout|116<br /><br /> 117<br /><br /> 118|  
|Colonnes sys.dm_fts_active_catalogs :<br /><br /> is_paused<br /><br /> previous_status<br /><br /> previous_status_description<br /><br /> row_count_in_thousands<br /><br /> status<br /><br /> status_description<br /><br /> worker_count|Aucun.|dm_fts_active_catalogs.is_paused<br /><br /> dm_fts_active_catalogs.previous_status<br /><br /> dm_fts_active_catalogs.previous_status_description<br /><br /> dm_fts_active_catalogs.row_count_in_thousands<br /><br /> dm_fts_active_catalogs.status<br /><br /> dm_fts_active_catalogs.status_description<br /><br /> dm_fts_active_catalogs.worker_count|218<br /><br /> 221<br /><br /> 222<br /><br /> 224<br /><br /> 219<br /><br /> 220<br /><br /> 223|  
|Colonne sys.dm_fts_memory_buffers :<br /><br /> row_count|Aucun.|dm_fts_memory_buffers.row_count|225|  
|Colonnes sys.fulltext_catalogs :<br /><br /> path<br /><br /> data_space_id<br /><br /> Colonnes file_id|Aucun.|fulltext_catalogs.path<br /><br /> fulltext_catalogs.data_space_id<br /><br /> fulltext_catalogs.file_id|215<br /><br /> 216<br /><br /> 217|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Fonctionnalités non prises en charge dans une future version de SQL Server  
 Les fonctionnalités suivantes de recherche en texte intégral sont prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais seront supprimées dans une version ultérieure. La version spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas été déterminée.  
  
 La valeur **Nom de la fonctionnalité** apparaît dans les événements de suivi comme ObjectName et dans les compteurs de performance et sys.dm_os_performance_counters comme nom de l’instance. La valeur **ID de la fonctionnalité** apparaît dans les événements de suivi comme ObjectId.  
  
|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|------------------------|-----------------|------------------|----------------|  
|Opérateur NEAR générique CONTAINS et CONTAINSTABLE :<br /><br /> {<terme_simple> &#124; <terme_préfixe>}<br /><br /> {<br /><br /> { { NEAR &#124; ~ }    {<terme_simple> &#124; <terme_préfixe>} } [...*n*]<br /><br /> }|Opérateur NEAR personnalisé :<br /><br /> NEAR(<br /><br /> {   {<terme_simple> &#124; <terme_préfixe>} [ ,...*n* ]<br /><br /> &#124; ( {<terme_simple> &#124; <terme_préfixe>} [,...*n*] )<br /><br /> [,\<distance> [,\<order>] ]<br /><br /> }<br /><br /> )<br /><br /> \<distance> ::= {*integer* &#124; **MAX**}<br /><br /> \<order> ::= {TRUE &#124; **FALSE**}|FULLTEXT_OLD_NEAR_SYNTAX|247|  
|Option CREATE FULLTEXT CATALOG :<br /><br /> IN PATH '*chemin_racine*'<br /><br /> ON FILEGROUP *filegroup*|Aucun.|CREATE FULLTEXT CATLOG IN PATH<br /><br /> Aucun.*|237<br /><br /> Aucun.<sup>*</sup>|  
|Propriété DATABASEPROPERTYEX : IsFullTextEnabled|Aucun.|DATABASEPROPERTYEX **('IsFullTextEnabled')**|202|  
|Option sp_detach_db :<br /><br /> [ @keepfulltextindexfile = ] '*conserver_fichier_index_recherche_en_texte-intégral*'|Aucun.|sp_detach_db @keepfulltextindexfile|226|  
|Valeurs d’action sp_fulltext_service : resource_usage n’a pas de fonction.|None|sp_fulltext_service @action=resource_usage|200|  
  
 \** L’objet **SQL Server : fonctionnalités déconseillées** ne surveille pas les occurrences de CREATE FULLTEXT CATLOG ON FILEGROUP *groupe de fichiers*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server, objet Deprecated Features](../performance-monitor/sql-server-deprecated-features-object.md)   
 [Modifications avec rupture pour la recherche en texte intégral](../../database-engine/breaking-changes-to-full-text-search.md)   
 [Fonctionnalités dépréciées du moteur de base de données dans SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
