---
title: Ensemble de lignes DISCOVER_DB_CONNECTIONS | Documents Microsoft
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
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a592cffbf5d8fe19d37fc48989d9c2776df81a4e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discoverdbconnections-rowset"></a>Ensemble de lignes DISCOVER_DB_CONNECTIONS
  Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes du serveur à une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_DB_CONNECTIONS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||Nom de la base de données actuellement connectée.|  
|**ID_CONNEXION**|**DBTYPE_I4**||Numéro unique qui identifie la connexion.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||Durée d'inactivité, en millisecondes, depuis l'établissement de la connexion.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||indique si la connexion est active (1) ou inactive (0).|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles l'exécution de la dernière commande s'est achevée.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles l'exécution de la dernière commande a débuté.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||Nom du serveur actuellement connecté.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||ID de session.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles la connexion a été établie.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||Durée de connexion active, en millisecondes, depuis l'établissement de la connexion.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
> [!IMPORTANT]  
>  L'ensemble de lignes **DISCOVER_DB_CONNECTIONS** affiche des informations uniquement lorsque le service est connecté aux sources de données relationnelles.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_DB_CONNECTIONS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Facultatif.|  
|CONNECTION_IN_USE|DBTYPE_I4|Facultatif.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Facultatif.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Obligatoire.|  
|CONNECTION_SPID|DBTYPE_I4|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

