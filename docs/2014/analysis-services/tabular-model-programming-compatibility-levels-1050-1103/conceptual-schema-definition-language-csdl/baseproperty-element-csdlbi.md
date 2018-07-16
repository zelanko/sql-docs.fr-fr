---
title: Élément BaseProperty (CSDLBI) | Microsoft Docs
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
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6de9e321e3cd5122a6252663c533be2d536800d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320839"
---
# <a name="baseproperty-element-csdlbi"></a>Élément BaseProperty (CSDLBI)
  L'élément BaseProperty est un type complexe qui sert de base aux autres éléments.  
  
 Ses attributs peuvent apparaître dans les colonnes et dans les mesures.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément BaseProperty.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Alignment|non|Nom donné au membre (une colonne, une mesure, une propriété de navigation, une hiérarchie ou un niveau) défini par l'implémentation du type Member.|  
|FormatString|non|Nom complet du membre.|  
|IsRightToLeft|non|Valeur booléenne qui indique si le champ contient du texte qui doit être lu de droite à gauche.<br /><br /> Si cet attribut est omis, la valeur par défaut (du modèle) est utilisée.|  
|SortDirection|non|Valeur qui indique comment les valeurs des champs sont généralement triées. Le contenu de cet attribut est défini par le type simple SortDirection.<br /><br /> En cas d'omission, un ordre de tri est affecté par défaut en fonction du type de données du champ.|  
|Unités|non|Symbole qui est appliqué aux valeurs de champ pour exprimer des unités.<br /><br /> En cas d'omission, les unités sont inconnues.|  
  
## <a name="alignment-element"></a>Élément Alignment  
 Ce type simple définit le format d'affectation des noms qui est utilisé pour lever toute ambiguïté des membres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Utilise le nom de l'attribut.|  
|Contexte|Utilise le nom de la relation entrante.|  
|Fusion|Selon les règles de grammaire, concatène le nom de la relation entrante et le nom de l'attribut.|  
  
## <a name="sortdirection-element"></a>Élément SortDirection  
 Ce type simple définit le format d'affectation des noms qui est utilisé pour lever toute ambiguïté des membres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Utilise le nom de l'attribut.|  
|Contexte|Utilise le nom de la relation entrante.|  
|Fusion|Concatène le nom de la relation entrante et le nom de la propriété.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
