---
title: Élément KeyDuplicate (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- KeyDuplicate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KeyDuplicate
helpviewer_keywords:
- KeyDuplicate element
ms.assetid: d7000b8b-e81f-4401-8738-00c2e0f73a59
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 97c4d349cecfc9fb1dd51c1c018110068b5be7dc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="keyduplicate-element-assl"></a>Élément KeyDuplicate (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Détermine comment [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gère une erreur de clé dupliquée s’il rencontre une au cours du traitement.  
  
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
|Élément parent|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 Les erreurs de clés dupliquées surviennent uniquement au cours du traitement des dimensions lorsque vous rencontrez une clé d'attribut plus d'une fois. Du fait que les clés d'attribut doivent être uniques, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignore les enregistrements en double. En règle générale, les erreurs de clés dupliquées indiquent un défaut de conception de la dimension, en particulier dans les relations entre attributs.  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*IgnoreError*|Le traitement doit ignorer l'erreur et se poursuivre.|  
|*ReportAndContinue*|Le traitement doit signaler l'erreur et se poursuivre.|  
|*ReportAndStop*|Le traitement doit signaler l'erreur et s'arrêter.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **KeyDuplicate** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
