---
title: Élément NullKeyNotAllowed (ASSL) | Documents Microsoft
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
- NullKeyNotAllowed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyNotAllowed
helpviewer_keywords:
- NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 235c76fb2b8cad1682fab97f36cb1867d7c82c38
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039385"
---
# <a name="nullkeynotallowed-element-assl"></a>Élément NullKeyNotAllowed (ASSL)
  Détermine comment la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] moteur de traitement gère une erreur de clé null survenue pendant le traitement.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ErrorConfiguration>  
   ...  
   <NullKeyNotAllowed>...</NullKeyNotAllowed>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*ReportAndContinue*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les erreurs de clé NULL se produisent lorsqu'une valeur NULL est rencontrée dans une colonne clé où les valeurs NULL ne sont pas autorisées, ce qui fait ignorer l'enregistrement pendant le traitement. Toutefois, cette erreur se produit uniquement si le [NullProcessing](nullprocessing-element-assl.md) , élément pour les `DataItem` ancêtre de la `ErrorConfiguration` élément parent a la valeur *erreur*.  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*IgnoreError*|Le traitement ignore l'erreur et continue.|  
|*ReportAndContinue*|Le traitement signale l'erreur et continue.|  
|*ReportAndStop*|Le traitement signale l'erreur et s'arrête.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `NullKeyNotAllowed` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ErrorConfiguration &#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)  
  
  