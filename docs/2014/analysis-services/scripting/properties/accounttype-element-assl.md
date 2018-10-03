---
title: Élément AccountType (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AccountType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c412993422eb963265f99274544ce6f673d5ad9a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075979"
---
# <a name="accounttype-element-assl"></a>Élément AccountType (ASSL)
  Contient le nom d’un type de compte défini dans un [base de données](../objects/database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[compte](../objects/account-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Revenu*|Le compte est un compte de produit.|  
|*Notes de frais*|Le compte est un compte de frais.|  
|*Flux*|Le compte est un compte de trésorerie.|  
|*Solde*|Le compte est un compte de bilan.|  
|*Élément multimédia*|Le compte est un compte d'actif.|  
|*Responsabilité*|Le compte est un compte de passif.|  
|*Statistiques*|Le compte est un compte statistique.|  
  
 L'énumération qui correspond aux valeurs autorisées de l'élément `AccountType` dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comptes élément &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
