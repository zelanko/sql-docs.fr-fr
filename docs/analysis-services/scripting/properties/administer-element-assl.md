---
title: Élément Administer (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59b73f6cc648eaa35d53add20205aa483bc5bb76
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="administer-element-assl"></a>Élément Administer (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique si l’autorisation associée inclut le droit d’administrer un [base de données](../../../analysis-services/scripting/objects/database-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|False|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **Administer** indique si un utilisateur peut exercer des fonctions d'administration uniquement sur la base de données spécifiée. Le rôle d'administrateur de serveur peut exercer des fonctions administratives sur toutes les bases de données que contient l'instance.  
  
 L’élément qui correspond au parent de **administrer** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Élément role & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
