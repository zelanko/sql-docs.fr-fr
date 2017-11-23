---
title: Ensemble de lignes DISCOVER_JOBS | Documents Microsoft
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edf0125dff1f193106f5738aef99b8c830c29236
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="discoverjobs-rowset"></a>Ensemble de lignes DISCOVER_JOBS
  Fournit des informations sur les travaux actifs exécutés sur le serveur. Un travail fait une partie d'une commande qui exécute une tâche spécifique pour le compte de la commande.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_JOBS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**JOB_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles le travail a été créé.|  
|**JOB_DESCRIPTION**|**DBTYPE_WSTR**||Description du travail attribuée par le service du serveur.|  
|**JOB_EXECUTION_TIME_MS**|**DBTYPE_I8**||Durée, en millisecondes, d'activité du travail.|  
|**JOB_ID**|**DBTYPE_I4**||Identificateur unique du travail.|  
|**JOB_START_TIME**|**DBTYPE_DBTIMESTAMP**||Date et heure UTC du serveur auxquelles le travail a démarré.|  
|**JOB_THREADPOOL_ID**|**DBTYPE_I4**||Pool de threads à partir duquel le travail actuel a été démarré.|  
|**JOB_TOTAL_TIME_MS**|**DBTYPE_I8**||Durée écoulée, en millisecondes, depuis le démarrage du travail.|  
|**SPID**|**DBTYPE_I4**||ID de session.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_JOBS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facultatif.|  
|JOB_ID|DBTYPE_I4|Facultatif.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Facultatif.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Facultatif.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
