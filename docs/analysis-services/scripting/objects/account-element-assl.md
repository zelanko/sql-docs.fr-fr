---
title: "Compte de l’élément (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Account Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Account
helpviewer_keywords: Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 87a3e97ae62a4eb4dd28cef1c29ac9e0efd2147d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="account-element-assl"></a>Élément Account (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contient des détails sur un type de compte dans un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément.  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Comptes (Accounts)](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|Éléments enfants|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md), [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md), [alias](../../../analysis-services/scripting/collections/aliases-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Dimensions, dont [Type](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) a la valeur *comptes,* peut avoir un attribut qui spécifie le type de compte, par exemple recettes, dépenses et ainsi de suite, représentés par les membres de la dimension. Le type de compte est ensuite utilisé par [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md) éléments, dont [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) a la valeur *ByAccount*, afin de déterminer la fonction d’agrégation à utiliser pour regrouper les membres de cette dimension. Le **compte** élément représente un type de compte unique et la fonction d’agrégation qui doit être utilisée par de telles mesures.  
  
 Un type de compte doit être répertorié si la fonction d’agrégation est différente de la valeur par défaut utilisée par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour chaque type de compte.  
  
 L'ensemble des types de compte valides est fixe.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de la base de données &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
