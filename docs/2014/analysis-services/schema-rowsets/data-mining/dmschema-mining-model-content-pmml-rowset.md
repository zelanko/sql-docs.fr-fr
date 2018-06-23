---
title: Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT_PMML | Documents Microsoft
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
api_name:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML rowset
ms.assetid: fa05bb08-a955-4c8d-b57f-ffcd82470220
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3c90e4dd752726b59e68ad6fb03c9d29327006e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038900"
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT_PMML
  Retourne la structure XML du modèle d'exploration de données. Le format de la chaîne XML est conforme au standard PMML (Predictive Model Markup Language) 2.1.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_MODEL_CONTENT_PMML` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue défini d'après le nom de la base de données dont le modèle est membre.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié. Cette colonne n’est pas pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; il contient toujours `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nom du modèle. Cette colonne ne peut pas contenir `NULL`.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Type de modèle. Il s'agit d'une chaîne spécifique au fournisseur. Sa valeur peut être `NULL`.|  
|`MODEL_GUID`|`DBTYPE_GUID`||GUID qui identifie le modèle. Les fournisseurs qui n'utilisent pas de GUID pour identifier les tables retournent `NULL`.|  
|`MODEL_PMML`|`DBTYPE_WSTR`||Représentation XML du contenu du modèle au format PMML.|  
|`SIZE`|`DBTYPE_UI4`||Nombre d'octets dans la chaîne XML.|  
|`LOCATION`|`DBTYPE_WSTR`||Emplacement du fichier XML. La valeur est `NULL` si aucun emplacement n'est disponible.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DMSCHEMA_MINING_MODEL_CONTENT_PMML` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  