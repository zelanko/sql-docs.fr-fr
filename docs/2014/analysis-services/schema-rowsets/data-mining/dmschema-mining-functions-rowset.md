---
title: Ensemble de lignes DMSCHEMA_MINING_FUNCTIONS | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b5a60e18a57c15976e7a7bd5d5e31729e255869a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151773"
---
# <a name="dmschemaminingfunctions-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_FUNCTIONS
  Décrit les fonctions d’exploration de données qui sont pris en charge par les algorithmes d’exploration de données disponibles sur un serveur qui est en cours d’exécution [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_FUNCTIONS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Nom de l'algorithme.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`||Nom de la fonction.|  
|`FUNCTION_SIGNATURE`|`DBTYPE_WSTR`||Signature de la fonction.|  
|`RETURNS_TABLE`|`DBTYPE_BOOL`||`FALSE` si la fonction retourne le contenu scalaire (tel que la longueur de l'argument de caractère) ; `TRUE` si la fonction retourne une table (telle qu'une table d'histogrammes).|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale de la fonction.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Nom du fichier qui contient la documentation de cette fonction.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||ID de contexte d'aide de cette fonction.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DMSCHEMA_MINING_FUNCTIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  