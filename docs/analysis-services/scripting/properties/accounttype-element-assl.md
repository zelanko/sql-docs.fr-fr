---
title: Élément AccountType (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e07561d0cd4272c202786f931fdd0dbc3c4eda8d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="accounttype-element-assl"></a>Élément AccountType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient le nom d’un type de compte défini dans un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément.  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Compte](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Revenu*|Le compte est un compte de produit.|  
|*Dépenses*|Le compte est un compte de frais.|  
|*Flux*|Le compte est un compte de trésorerie.|  
|*Balance*|Le compte est un compte de bilan.|  
|*Actif*|Le compte est un compte d'actif.|  
|*Dettes*|Le compte est un compte de passif.|  
|*Statistique*|Le compte est un compte statistique.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **AccountType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comptes d’élément &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
