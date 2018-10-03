---
title: Élément (ASSL) du compte | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Account Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 262ba3be01879770a734ab7334782e26aa04b364
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109049"
---
# <a name="account-element-assl"></a>Élément Account (ASSL)
  Contient des détails sur un type de compte dans un [base de données](database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Accounts>  
   <Account>  
      <AccountType>...</AccountType>  
      <AggregationFunction>...</AggregationFunction>  
            <Aliases>...</Aliases>  
            <Annotations>...</Annotations>  
   </Account>  
</Accounts>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Comptes (Accounts)](../collections/accounts-element-assl.md)|  
|Éléments enfants|[AccountType](../properties/accounttype-element-assl.md), [AggregationFunction](../properties/aggregationfunction-element-assl.md), [alias](../collections/aliases-element-assl.md), [Annotations](../collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Dimensions, dont [Type](../properties/type-element-dimension-assl.md) élément est défini sur *comptes,* peut avoir un attribut qui spécifie le type de compte, par exemple recettes, dépenses et ainsi de suite, représentées par les membres dans la dimension. Le type de compte est ensuite utilisé par [mesure](measure-element-assl.md) éléments, dont [AggregationFunction](../properties/aggregatefunction-element-assl.md) élément est défini sur *ByAccount*, afin de déterminer la fonction d’agrégation à utiliser lors regrouper les membres de cette dimension. L'élément `Account` représente un type de compte unique et la fonction d'agrégation qui doit être utilisée par de telles mesures.  
  
 Un type de compte doit être répertorié si la fonction d’agrégation est différente de la valeur par défaut utilisé par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour chaque type de compte.  
  
 L'ensemble des types de compte valides est fixe.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de base de données &#40;ASSL&#41;](database-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
