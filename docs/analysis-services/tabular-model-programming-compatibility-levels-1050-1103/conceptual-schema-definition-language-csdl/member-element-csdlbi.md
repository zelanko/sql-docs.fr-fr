---
title: "Élément Member (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bc33ebc0cd970c58f4f27d4b49a972c9ed724c0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="member-element-csdlbi"></a>Élément Member (CSDLBI)
  L'élément Member est un type complexe qui sert de base aux autres éléments.  
  
 Ses attributs s'affichent dans les colonnes, les mesures, les propriétés de navigation, les hiérarchies et les niveaux.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Member.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Nom||Nom donné au membre (une colonne, une mesure, une propriété de navigation, une hiérarchie ou un niveau) défini par l'implémentation du type TMember|  
|Légende|Oui|Nom complet du membre.|  
|ContextualNameRule|Oui|Format d'affectation des noms qui est utilisé pour lever toute ambiguïté des membres. Le contenu de cet attribut est défini par le type simple ContextualNameRule.|  
|Hidden||Valeur booléenne qui indique si le membre est caché dans le client.<br /><br /> La valeur par défaut est False, ce qui signifie que les colonnes sont visibles dans le client.|  
|ReferenceName||Identificateur utilisé pour référencer le membre dans une requête DAX. Si cet attribut est omis, le nom du champ est utilisé.|  
  
## <a name="contextualnamerule-element"></a>Élément ContextualNameRule  
 Ce type simple définit le format d'affectation des noms qui est utilisé pour lever toute ambiguïté des membres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Aucune|Utilise le nom de l'attribut.|  
|Contexte|Utilise le nom de la relation entrante.|  
|Fusion|Concatène le nom de la relation entrante et le nom de la propriété.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire au niveau de compatibilité 1050 1103 via des niveaux](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  

