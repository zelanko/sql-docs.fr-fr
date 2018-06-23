---
title: Ensemble de lignes DISCOVER_JOBS | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6bc9574f76d1e14ad887efdd2b5654b4439c69df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040963"
---
# <a name="discoverjobs-rowset"></a>Ensemble de lignes DISCOVER_JOBS
  Fournit des informations sur les travaux actifs exécutés sur le serveur. Un travail fait une partie d'une commande qui exécute une tâche spécifique pour le compte de la commande.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_JOBS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`JOB_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure UTC du serveur auxquelles le travail a été créé.|  
|`JOB_DESCRIPTION`|`DBTYPE_WSTR`||Description du travail attribuée par le service du serveur.|  
|`JOB_EXECUTION_TIME_MS`|`DBTYPE_I8`||Durée, en millisecondes, d'activité du travail.|  
|`JOB_ID`|`DBTYPE_I4`||Identificateur unique du travail.|  
|`JOB_START_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure UTC du serveur auxquelles le travail a démarré.|  
|`JOB_THREADPOOL_ID`|`DBTYPE_I4`||Pool de threads à partir duquel le travail actuel a été démarré.|  
|`JOB_TOTAL_TIME_MS`|`DBTYPE_I8`||Durée écoulée, en millisecondes, depuis le démarrage du travail.|  
|`SPID`|`DBTYPE_I4`||ID de session.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_JOBS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facultatif.|  
|JOB_ID|DBTYPE_I4|Facultatif.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Facultatif.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Facultatif.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  