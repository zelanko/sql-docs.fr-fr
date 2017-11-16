---
title: Ensemble de lignes DISCOVER_CONNECTIONS | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_CONNECTIONS rowset
ms.assetid: e4703970-c31d-448c-ab68-503303c91aa4
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b02c9f5d9a9e22e626143a6ca5701ac5b1db50e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discoverconnections-rowset"></a>Ensemble de lignes DISCOVER_CONNECTIONS
  Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes sur le serveur.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_CONNECTIONS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restrictions| Description|  
|-----------------|--------------------|------------------|-----------------|  
|**ID_CONNEXION**|**DBTYPE_I4**|Oui|Numéro unique qui identifie la connexion.|  
|**CONNECTION_USER_NAME**|**DBTYPE_WSTR**|Oui|Nom d'utilisateur de la connexion.|  
|**CONNECTION_IMPERSONATED_USER_NAME**|**DBTYPE_WSTR**|Oui|Réservé pour un usage ultérieur. Analysis Services retourne toujours NULL pour la valeur de CONNECTION_IMPERSONATED_USER_NAME.|  
|**CONNECTION_HOST_NAME**|**DBTYPE_WSTR**|Oui|Nom de l'ordinateur qui a initialisé la connexion.|  
|**CONNECTION_HOST_APPLICATION**|**DBTYPE_WSTR**||Nom de l'application qui a initialisé la connexion.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles la connexion a été établie.|  
|**CONNECTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Oui|Durée écoulée, en millisecondes, depuis l'établissement de la connexion.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles l'exécution de la dernière commande a débuté.|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles l'exécution de la dernière commande s'est achevée.|  
|**CONNECTION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**|Oui|Durée écoulée, en millisecondes, depuis la fin de la dernière commande exécutée.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**|Oui|Durée d'inactivité, en millisecondes, depuis l'établissement de la connexion.|  
|**CONNECTION_BYTES_SENT**|**DBTYPE_I8**||Nombre cumulé d'octets envoyés par la connexion depuis l'établissement de la connexion.|  
|**CONNECTION_DATA_BYTES_SENT**|**DBTYPE_I8**||Nombre cumulé d'octets de données envoyés par la connexion depuis l'établissement de la connexion.<br /><br /> Les données transitent au format compressé dans la connexion ; cette valeur représente les données étendues envoyées.|  
|**CONNECTION_BYTES_RECEIVED**|**DBTYPE_I8**||Nombre cumulé d'octets reçus par la connexion depuis l'établissement de la connexion.|  
|**CONNECTION_DATA_BYTES_RECEIVED**|**DBTYPE_I8**||Nombre cumulé d'octets de données reçus par la connexion depuis l'établissement de la connexion.<br /><br /> Les données transitent au format compressé dans la connexion ; cette valeur représente les données étendues reçues.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd25-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Connexions|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

