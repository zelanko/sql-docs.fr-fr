---
title: NullProcessing, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullProcessing Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7fa4c851e6818a3c9607fed0fdb8b9c499a63d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139889"
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
  Définit le mode de traitement des valeurs NULL.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Automatic*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Conserver*|Conserve la valeur NULL. **Remarque :** cette valeur n’est pas pris en charge pour les mesures de comptage.|  
|*Erreur*|Déclenche une erreur de clé NULL. La valeur de [NullKeyNotAllowed](nullkeynotallowed-element-assl.md) détermine comment l’instance réagit à l’erreur. **Remarque :** cette valeur n’est pas pris en charge pour les mesures.|  
|*UnknownMember*|Génère un membre inconnu et déclenche une erreur de conversion de valeur NULL. La valeur de [NullKeyConvertedToUnknown](nullkeyconvertedtounknown-element-assl.md) détermine comment l’instance réagit à l’erreur. **Remarque :** cette valeur n’est pas pris en charge pour les colonnes associées aux mesures.|  
|*ZeroOrBlank*|Convertit la valeur NULL en zéro (pour les éléments de données numériques) ou en une chaîne vide (pour les éléments de données de type chaîne). **Remarque :** cette valeur assure la compatibilité avec les versions précédentes de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Automatic*|Utilise le traitement par défaut approprié pour l'élément :<br /><br /> -   *ZeroOrBlank* pour les éléments de données OLAP.<br />-   *UnknownMember* pour les éléments de données d’exploration de données.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `NullProcessing` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
