---
title: Ensemble de lignes DMSCHEMA_MINING_MODELS | Microsoft Docs
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
- DMSCHEMA_MINING_MODELS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9af1a9817ad116561b57b1d04b2e3df1d7313bb2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208029"
---
# <a name="dmschemaminingmodels-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_MODELS
  Énumère les modèles d'exploration de données du catalogue actuel. L'ensemble de lignes `DMSCHEMA_MINING_MODELS` inclut des informations telles que les noms des modèles, la date de traitement et l'algorithme d'exploration de données associé à chaque modèle d'exploration de données.  
  
 . Le `DMSCHEMA_MINING_MODELS` ensemble de lignes de schéma est très similaire à la [DBSCHEMA_TABLES](../ole-db/dbschema-tables-rowset.md) ensemble de lignes de schéma et peut être utilisé de la même façon.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_MODELS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue. Défini d'après le nom de la base de données dont le modèle est membre.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié. Cette colonne n’est pas pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; il contient toujours `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Le nom du modèle d’exploration de données. Cette colonne contient le nom du modèle d'exploration de données ; elle n'est jamais vide.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Type de modèle.|  
|`MODEL_GUID`|`DBTYPE_GUID`||GUID du modèle.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale du modèle.|  
|`MODEL_PROPID`|`DBTYPE_UI4`||ID de propriété du modèle. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Date de création du modèle.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Date de la dernière modification de la définition du modèle.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Énumération qui identifie le type d'algorithme d'exploration de données utilisé par le modèle. Les valeurs possibles pour ce type sont les suivantes :<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (1)<br />-   `DM_SERVICETYPE_SEGMENTATION`(2)<br />-   `DM_SERVICETYPE_ ASSOCIATION`(4)<br />-   `DM_SERVICETYPE_ DENSITY_ESTIMATE`(8)<br />-   `DM_SERVICETYPE_SEQUENCE`(16)|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nom spécifique au fournisseur de l'algorithme d'exploration de données utilisé par le modèle.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||Instruction utilisée pour créer le modèle d'exploration de données.|  
|`PREDICTION_ENTITY`|`DBTYPE_WSTR`||Liste délimitée par des virgules indiquant les colonnes d'exploration de données pouvant être prédites.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Indicateur booléen qui indique si le modèle est rempli.<br /><br /> `TRUE` Si le modèle est renseigné ; Sinon, `FALSE`.|  
|`MINING_PARAMETERS`|`DBTYPE_WSTR`||Liste des paramètres qui ont été utilisés lors de la création du modèle, séparés par des virgules.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`||ID de la structure d'exploration de données sur laquelle repose le modèle.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Date du dernier traitement du modèle.|  
|`MSOLAP_IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Indicateur booléen qui indique si le modèle prend en charge l'extraction.|  
|`FILTER`|`DBTYPE_WSTR`||Expression de filtre qui est associée au modèle d'exploration de données.<br /><br /> Une valeur NULL ou une chaîne vide indique qu'aucun filtre n'est appliqué.|  
|`TRAINING_SET_SIZE`|`DBTYPE_UIS`||Nombre de cas contenus dans le jeu d'apprentissage du modèle d'exploration de données une fois que la structure a été traitée et une fois que les filtres ont été appliqués au modèle.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes `DMSCHEMA_MINING_MODELS` peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Facultatif.|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Facultatif.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`|Facultatif.|  
  
 Pour obtenir des exemples montrant comment interroger cet ensemble de lignes, consultez [interroger les paramètres utilisés pour créer un modèle d’exploration de données](../../data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
