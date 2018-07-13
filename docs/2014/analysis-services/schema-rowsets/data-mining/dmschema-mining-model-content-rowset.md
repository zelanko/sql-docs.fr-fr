---
title: Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT | Microsoft Docs
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
- DMSCHEMA_MINING_MODEL_CONTENT
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT rowset
ms.assetid: 1e85d9e7-3b74-42ac-b94e-f52f76d8a25d
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 76724967936008e52cb43f7af02bbb7a833475d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165450"
---
# <a name="dmschemaminingmodelcontent-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT
  Permet à l'application cliente de parcourir le contenu d'un modèle d'exploration de données. Les applications clientes peuvent utiliser les restrictions d'opérations d'arborescence spéciales décrites à la fin de cette rubrique pour accéder au contenu du modèle d'exploration de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_MODEL_CONTENT` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] remplit cette colonne avec le nom de la base de données dont le modèle est un membre.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `VT_NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nom du modèle auquel le contenu décrit par cette ligne est associé.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Noms des attributs qui correspondent à ce nœud.|  
|`NODE_NAME`|`DBTYPE_WSTR`||Nom du nœud. Actuellement, cette colonne contient la même valeur que `NODE_UNIQUE_NAME`, bien que cela puisse changer dans les versions ultérieures.|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du nœud.|  
|`NODE_TYPE`|`DBTYPE_I4`||Type de nœud. Génère l'une des valeurs suivantes (les algorithmes d'exploration de données tiers peuvent étendre cette liste) :<br /><br /> -   `DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT` (`2`)<br />-   `DM_NODE_TYPE_TREE_INTERIOR` (`3`)<br />-   `DM_NODE_TYPE_TREE_DISTRIBUTION` (`4`)<br />-   `DM_NODE_TYPE_CLUSTER` (`5`)<br />-   `DM_NODE_TYPE_UNKNOWN` (`6`)<br />-   `DM_NODE_TYPE_ITEMSET` (`7`)<br />-   `DM_NODE_TYPE_ASSOCIATION_RULE` (`8`)<br />-   `DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE` (`9`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE` (`10`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE` (`11`)<br />-   `DM_NODE_TYPE_SEQUENCE` (`13`)<br />-   `DM_NODE_TYPE_TRANSITION` (`14`)<br />-   `DM_NODE_TYPE_TIME_SERIES` (`15`)<br />-   `DM_NODE_TYPE_TS_TREE` (`16`)<br />-   `DM_NODE_TYPE_NN_SUBNETWORK` (`17`) Réseau neuronal, sous-réseau<br />-   `DM_NODE_TYPE_NN_INPUT_LAYER` (`18`) Réseau neuronal, couche d’entrée (parent de nœuds d’entrée)<br />-   **DM_NODE_TYPE_NN_HIDDEN_LAYER** (`19`) réseau neuronal, couche masquée (parent de nœuds masqués)<br />-   `DM_NODE_TYPE_NN_OUTPUT_LAYER` (`20`) Réseau neuronal, couche de sortie (parent de nœuds de sortie)<br />-   `DM_NODE_TYPE_NN_INPUT_NODE` (`21`) Réseau neuronal, le nœud d’entrée<br />-   `DM_NODE_TYPE_NN_HIDDEN_NODE` (`22`) Réseau neuronal, nœud masqué<br />-   `DM_NODE_TYPE_NN_OUTPUT_NODE` (`23`) Réseau neuronal, le nœud de sortie<br />-   `DM_NODE_TYPE_NN_MARGINAL_STAT_NODE` (`24`) Réseau neuronal, le nœud des statistiques marginales<br />-   **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (`25`)<br />-   `DM_NODE_TYPE_NB_MARGINAL_STAT_NODE` (`26`) Réseau neuronal, le nœud des statistiques marginales|  
|`NODE_GUID`|`DBTYPE_GUID`||GUID du nœud. Cette colonne n'est pas prise en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ; elle contient systématiquement `NULL`.|  
|`NODE_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée au nœud. Cette propriété est principalement utilisée à des fins d'affichage.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Estimation du nombre d'enfants du nœud.|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du parent du nœud. `NULL` est retournée pour tous les nœuds situés au niveau de la racine.|  
|`NODE_DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale du nœud.|  
|`NODE_RULE`|`DBTYPE_WSTR`||Description XML de la règle incorporée dans le nœud.|  
|`MARGINAL_RULE`|`DBTYPE_WSTR`||Description XML de la règle se déplaçant vers le nœud à partir du nœud parent.|  
|`NODE_PROBABILITY`|`DBTYPE_R8`||Probabilité associée à ce nœud.|  
|`MARGINAL_PROBABILITY`|`DBTYPE_R8`||Probabilité d'accès au nœud à partir du nœud parent.|  
|`NODE_DISTRIBUTION`|`DBTYPE_HCHAPTER`||Table qui contient l'histogramme de probabilité du nœud.|  
|`NODE_SUPPORT`|`DBTYPE_R8`||Nombre de cas qui prennent en charge ce nœud.|  
|`MSOLAP_MODEL_COLUMN`|`DBTYPE_WSTR`||Nom de la colonne de la définition du modèle à laquelle ce nœud se rapporte.|  
|`MSOLAP_NODE_SCORE`|`DBTYPE_R8`||Score qui a été calculé pour ce nœud.|  
|`MSOLAP_NODE_SHORT_CAPTION`|`DBTYPE_WSTR`||Courte légende du nœud pouvant être utilisée à des fins d'affichage pour améliorer la lisibilité.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DMSCHEMA_MINING_MODEL_CONTENT` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facultatif.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`NODE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`NODE_TYPE`|`DBTYPE_I4`|Facultatif.|  
|`NODE_GUID`|`DBTYPE_WSTR`|Facultatif.|  
|`NODE_CAPTION`|`DBTYPE_WSTR`|Facultatif.|  
|`TREE_OPERATION`|`DBTYPE_UI4`|Facultatif. (voir les remarques supplémentaires ci-dessous)|  
  
 La restriction, `TREE_OPERATION`, n'est pas appliquée à une colonne spécifique de l'ensemble de lignes `DMSCHEMA_MINING_MODEL_CONTENT` ; elle spécifie en fait un opérateur d'arborescence. Le consommateur peut spécifier une restriction `NODE_UNIQUE_NAME` et l'opérateur d'arborescence (`ANCESTORS`, `CHILDREN`, `SIBLINGS`, `PARENT`, `DESCENDANTS`, `SELF`) pour obtenir le jeu de membres demandé. L'opérateur `SELF` inclut la ligne pour le nœud proprement dit dans la liste des lignes retournées. Le tableau suivant décrit les constantes qui forment la définition de bitmap de la restriction `TREE_OPERATION`. Elles peuvent être associées à l'aide de l'opérateur logique `OR`.  
  
|Constante|Valeur|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|`0x00000020`|  
|**DMTREEOP_CHILDREN**|`0x00000001`|  
|**DMTREEOP_SIBLINGS**|`0x00000002`|  
|**DMTREEOP_PARENT**|`0x00000004`|  
|**DMTREEOP_SELF**|`0x00000008`|  
|**DMTREEOP_DESCENDANTS**|`0x00000010`|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
