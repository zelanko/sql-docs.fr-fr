---
title: Élément (ASSL) de contenu | Documents Microsoft
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
- Content Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Content
helpviewer_keywords:
- Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 98d2de4a0ce93e857a63ebd9fe79dd18d0f9a86e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041892"
---
# <a name="content-element-assl"></a>Élément Content (ASSL)
  Décrit le contenu de la colonne dans la [MiningStructure](../objects/miningstructure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Cette énumération décrit le type de contenu représenté par une colonne de structure d'exploration de données et peut être étendue autant que nécessaire par les fournisseurs d'algorithmes d'exploration de données. Pour plus d’informations sur les types de contenu, consultez [Types de contenu &#40;exploration de données&#41;](../../data-mining/content-types-data-mining.md).  
  
 Les valeurs répertoriées dans le tableau suivant sont généralement prises en charge par les fournisseurs d'algorithmes d'exploration de données.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Discrètes*|La colonne contient des valeurs discrètes.|  
|*Continue*|Les valeurs de la colonne définissent un jeu continu de données numériques.|  
|*Discrétisé*|Les valeurs de la colonne représentent des groupes (ou compartiments) de valeurs dérivés d'une colonne continue.|  
|*Commandée*|Les valeurs de la colonne définissent un jeu ordonné.|  
|*Cyclique*|Les valeurs de la colonne définissent un jeu ordonné cyclique.|  
|*Probabilité*|Les valeurs de la colonne spécifient une probabilité pour les colonnes contenues dans le [ClassifiedColumns](../collections/columns-element-assl.md) élément du parent `ScalarMiningStructureColumn`.|  
|*Variance*|Les valeurs de la colonne spécifient une variance pour les colonnes contenues dans l'élément `ClassifiedColumns` de la `ScalarMiningStructureColumn` parente.|  
|*StdDev*|Les valeurs de la colonne spécifient un écart type pour les colonnes contenues dans l'élément `ClassifiedColumns` de la `ScalarMiningStructureColumn` parente.|  
|*ProbabilityVariance*|Les valeurs de la colonne spécifient une variance de probabilité pour les colonnes contenues dans l'élément `ClassifiedColumns` de la `ScalarMiningStructureColumn` parente.|  
|*ProbabilityStdDev*|Les valeurs de la colonne spécifient un écart type de probabilité pour les colonnes contenues dans l'élément `ClassifiedColumns` de la `ScalarMiningStructureColumn` parente.|  
|*Prise en charge*|Les valeurs de la colonne spécifient des informations de support technique pour la colonne contenue dans l'élément `ClassifiedColumns` de la `ScalarMiningStructureColumn` parente. **Remarque :** cette colonne est fournie en tant que partie de la norme pour les fournisseurs d’algorithmes d’exploration de données tiers. **Remarque :** fournis par Microsoft algorithmes n’ont pas de toute utilisation de cette colonne. <br /><br /> .|  
|*Clé*|La colonne est une colonne clé. **Remarque :** ce type de contenu s’applique uniquement aux colonnes clés, dans lequel le `IsKey` a la valeur `True`.|  
  
 Outre ces valeurs standards, d’exploration de données des fournisseurs d’algorithmes inclus avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prennent en charge les valeurs dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Séquence de touches*|La colonne est une colonne clé, et les valeurs de la colonne représentent une séquence d'événements. **Remarque :** ce type de contenu s’applique uniquement aux colonnes clés, dans lequel le `IsKey` a la valeur `True`.|  
|*Temps clé*|La colonne est une colonne clé, et les valeurs de la colonne représentent des unités de mesure du temps. **Remarque :** ce type de contenu s’applique uniquement aux colonnes clés, dans lequel le `IsKey` a la valeur `True`.|  
|*Sequence*|Les valeurs de la colonne représentent une séquence d'événements.|  
|*Time*|Les valeurs de la colonne représentent des unités de mesure du temps.|  
  
 L'énumération qui correspond aux valeurs autorisées de l'élément `Content` dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ClassifiedColumns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  