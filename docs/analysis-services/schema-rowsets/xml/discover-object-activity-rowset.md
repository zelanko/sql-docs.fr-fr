---
title: Ensemble de lignes DISCOVER_OBJECT_ACTIVITY | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f42115f46be220580d42d54f5cab62c7c12492ec
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discoverobjectactivity-rowset"></a>Ensemble de lignes DISCOVER_OBJECT_ACTIVITY
  Fournit l'utilisation des ressources par objet depuis le démarrage du service.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_OBJECT_ACTIVITY** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_AGGREGATION_HIT**|**DBTYPE_I8**||Nombre d'accès à une agrégation de l'objet depuis le démarrage du service.|  
|**OBJECT_AGGREGATION_MISS**|**DBTYPE_I8**||Nombre de fois où une agrégation existante de l'objet n'a pas servi (autrement dit, n'a pas été utilisée) depuis le démarrage du service.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||Temps processeur, en millisecondes, consommé par l'objet depuis le début du service.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Numéro de lignage des données de l'objet ; ce nombre est incrémenté chaque fois que l'objet est traité.|  
|**OBJECT_HIT**|**DBTYPE_I8**||Nombre d'accès à l'objet dans le cache depuis le démarrage du service.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||ID de l'objet tel que défini lors de la création|  
|**OBJECT_MISS**|**DBTYPE_I8**||Nombre de non-accès à l'objet dans le cache depuis le démarrage du service.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||Chemin d'accès au parent de l'objet actuel.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||Valeur cumulée de lectures de données par l'objet depuis le démarrage du service, en kilo-octets.|  
|**OBJECT_READS**|**DBTYPE_I8**||Nombre cumulé d'opérations de lecture par l'objet depuis le démarrage du service.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||Nombre de lignes retournées par l'objet à l'appelant depuis le démarrage du service.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||Nombre de lignes analysées par l'objet depuis le démarrage du service.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Numéro de version des métadonnées de l'objet ; ce nombre change chaque fois que l'objet est modifié.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||Valeur cumulée d'écritures de données par l'objet depuis le démarrage du service, en kilo-octets.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||Nombre cumulé d'opérations d'écriture par l'objet depuis le démarrage du service.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_OBJECT_ACTIVTY** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|Facultatif.|  
|OBJECT_ID|DBTYPE_WSTR|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
