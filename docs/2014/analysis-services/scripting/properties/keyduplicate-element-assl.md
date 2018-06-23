---
title: Élément KeyDuplicate (ASSL) | Documents Microsoft
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
- KeyDuplicate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyDuplicate
helpviewer_keywords:
- KeyDuplicate element
ms.assetid: d7000b8b-e81f-4401-8738-00c2e0f73a59
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 353c8d1eac5803db6f76014519d1c812813f535d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051593"
---
# <a name="keyduplicate-element-assl"></a>Élément KeyDuplicate (ASSL)
  Détermine comment [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gère une erreur de clé dupliquée s’il rencontre une au cours du traitement.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyDuplicate>...</KeyDuplicate>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*IgnoreError*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les erreurs de clés dupliquées surviennent uniquement au cours du traitement des dimensions lorsque vous rencontrez une clé d'attribut plus d'une fois. Du fait que les clés d'attribut doivent être uniques, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignore les enregistrements en double. En règle générale, les erreurs de clés dupliquées indiquent un défaut de conception de la dimension, en particulier dans les relations entre attributs.  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*IgnoreError*|Le traitement doit ignorer l'erreur et se poursuivre.|  
|*ReportAndContinue*|Le traitement doit signaler l'erreur et se poursuivre.|  
|*ReportAndStop*|Le traitement doit signaler l'erreur et s'arrêter.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `KeyDuplicate` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  