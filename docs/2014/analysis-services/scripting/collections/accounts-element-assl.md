---
title: Comptes d’élément (ASSL) | Documents Microsoft
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
- Accounts Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 30fcd1815ac785ab71c90a935b9392ab5e85e98b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038447"
---
# <a name="accounts-element-assl"></a>Élément Accounts (ASSL)
  Contient la collection des types de compte sont définies dans un [base de données](../objects/database-element-assl.md) élément.  
  
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
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Base de données](../objects/database-element-assl.md)|  
|Éléments enfants|[Compte](../objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Dimensions, dont [Type](../properties/type-element-dimension-assl.md) a la valeur *comptes*, peuvent avoir un attribut qui spécifie le type de compte, par exemple recettes, dépenses, etc., représenté par les membres de la dimension. Le type de compte est ensuite utilisé par [mesure](../objects/measure-element-assl.md) éléments, dont [AggregationFunction](../properties/aggregatefunction-element-assl.md) a la valeur *ByAccount*, afin de déterminer la fonction d’agrégation à utiliser lorsque regrouper les membres de cette dimension. L'élément `Accounts` contient une collection d'éléments `Account`, qui représentent des types de compte et la fonction d'agrégation à utiliser pour chacun d'eux.  
  
 Un type de compte doit être répertorié si la fonction d’agrégation est différente de la valeur par défaut utilisée par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour chaque type de compte.  
  
 L'ensemble des types de compte valides est fixe.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AccountType &#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  