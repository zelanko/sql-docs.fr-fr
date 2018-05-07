---
title: Ensemble de lignes DISCOVER_JOBS | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f262e4d0b486676eb9f541fbd7d5c0e2866a07ae
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="discoverjobs-rowset"></a>Ensemble de lignes DISCOVER_JOBS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|SPID|DBTYPE_I4|Ce paramètre est facultatif.|  
|JOB_ID|DBTYPE_I4|Ce paramètre est facultatif.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Ce paramètre est facultatif.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Ce paramètre est facultatif.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
