---
title: Ensemble de lignes DISCOVER_DB_CONNECTIONS | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: 8a932cfa872e0cceed0b132f486349716ba4210b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverdbconnections-rowset"></a>Ensemble de lignes DISCOVER_DB_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fournit des informations sur les connexions actuellement ouvertes à partir du serveur pour une base de données activité et l’utilisation des ressources.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_DB_CONNECTIONS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
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
|CONNECTION_SPID|DBTYPE_I4|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
