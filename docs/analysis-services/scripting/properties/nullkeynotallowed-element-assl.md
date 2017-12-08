---
title: "Élément NullKeyNotAllowed (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: NullKeyNotAllowed Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NullKeyNotAllowed
helpviewer_keywords: NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45ad433dc247749c466f05896a89bc25bee0680d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les erreurs de clé NULL se produisent lorsqu'une valeur NULL est rencontrée dans une colonne clé où les valeurs NULL ne sont pas autorisées, ce qui fait ignorer l'enregistrement pendant le traitement. Toutefois, cette erreur se produit uniquement si le [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) , élément pour les **DataItem** ancêtre de la **ErrorConfiguration** élément parent a la valeur *erreur*.  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*IgnoreError*|Le traitement ignore l'erreur et continue.|  
|*ReportAndContinue*|Le traitement signale l'erreur et continue.|  
|*ReportAndStop*|Le traitement signale l'erreur et s'arrête.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **NullKeyNotAllowed** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ErrorConfiguration &#40; ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
  
