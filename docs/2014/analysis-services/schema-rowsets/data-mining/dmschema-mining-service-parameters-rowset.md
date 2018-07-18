---
title: Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS | Microsoft Docs
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
- DMSCHEMA_MINING_SERVICE_PARAMETERS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7203b2f717ec7605fcc52c1387472779488ae4c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224469"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS
  Décrit les paramètres des algorithmes sur le serveur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_SERVICE_PARAMETERS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nom de l'algorithme.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`||Nom du paramètre.|  
|`PARAMETER_TYPE`|`DBTYPE_WSTR`||Type du paramètre.|  
|`IS_REQUIRED`|`DBTYPE_BOOL`||Valeur booléenne qui retourne `TRUE` si le paramètre est requis.|  
|`PARAMETER_FLAGS`|`DBTYPE_UI4`||Masque de bits qui décrit les caractéristiques du paramètre :<br /><br /> -   `DM_PARAMETER_TRAINING` (`0x0000001`) indique le paramètre est utilisé pour l’apprentissage<br />-   `DM_PARAMETER_PREDICTION` (`0x00000002`) indique le paramètre est utilisé pour la prédiction<br />-   `DM_PARAMETER_CONTENT` (`0x00000003`) indique le paramètre est utilisé pour la restriction de contenu|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale du paramètre.|  
|`DEFAULT_VALUE`|`DBTYPE_WSTR`||Valeur par défaut du paramètre. Retourne `NULL` si la valeur par défaut n'est pas un type de données simple.|  
|`VALUE_ENUMERATION`|`DBTYPE_WSTR`||Énumérateur des valeurs possibles du paramètre.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Nom du fichier qui contient la documentation de ce paramètre.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||ID de contexte d'aide de cette fonction.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DMSCHEMA_MINING_SERVICE_PARAMETERS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
