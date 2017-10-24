---
title: "Comptes d’élément (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Accounts Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3d781e32f57f9df9cc5bf180e37761c8a26c0848
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="accounts-element-assl"></a>Élément Accounts (ASSL)
  Contient la collection des types de compte sont définies dans un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Database>  
   ...  
   <Accounts>  
      <Account>...</Account>  
   </Accounts>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucun (collection)|  
|Valeur par défaut|Aucun (collection)|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Base de données](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|Éléments enfants|[Compte](../../../analysis-services/scripting/objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Dimensions, dont [Type](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) a la valeur *comptes*, peuvent avoir un attribut qui spécifie le type de compte, par exemple recettes, dépenses, etc., représenté par les membres de la dimension. Le type de compte est ensuite utilisé par [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md) éléments, dont [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) a la valeur *ByAccount*, afin de déterminer la fonction d’agrégation à utiliser pour regrouper les membres de cette dimension. L'élément **Accounts** contient une collection d'éléments **Account** , qui représentent des types de compte et la fonction d'agrégation à utiliser pour chacun d'eux.  
  
 Un type de compte doit être répertorié si la fonction d’agrégation est différente de la valeur par défaut utilisée par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour chaque type de compte.  
  
 L'ensemble des types de compte valides est fixe.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AccountType &#40; ASSL &#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)   
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

