---
title: Élément Administer (ASSL) | Documents Microsoft
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
- Administer Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Administer
helpviewer_keywords:
- Administer element
ms.assetid: 52924cd6-6176-47c8-ab17-4ee0e0ce42b1
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 099e5b9283acf8da6268e8b5abaaad73049ca076
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042305"
---
# <a name="administer-element-assl"></a>Élément Administer (ASSL)
  Indique si l’autorisation associée inclut le droit d’administrer un [base de données](../objects/database-element-assl.md) élément.  
  
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
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `Administer` indique si un utilisateur peut exercer des fonctions d'administration uniquement sur la base de données spécifiée. Le rôle d'administrateur de serveur peut exercer des fonctions administratives sur toutes les bases de données que contient l'instance.  
  
 L’élément qui correspond au parent de `Administer` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données d’autorisation &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Élément role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  