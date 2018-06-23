---
title: Élément Member (CSDLBI) | Documents Microsoft
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
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 5
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: acca47250cc38966cf1043ac25212aa0d4950093
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041193"
---
# <a name="member-element-csdlbi"></a>Élément Member (CSDLBI)
  L'élément Member est un type complexe qui sert de base aux autres éléments.  
  
 Ses attributs s'affichent dans les colonnes, les mesures, les propriétés de navigation, les hiérarchies et les niveaux.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Member.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Nom   ||Nom donné au membre (une colonne, une mesure, une propriété de navigation, une hiérarchie ou un niveau) défini par l'implémentation du type TMember|  
|Légende|Oui|Nom complet du membre.|  
|ContextualNameRule|Oui|Format d'affectation des noms qui est utilisé pour lever toute ambiguïté des membres. Le contenu de cet attribut est défini par le type simple ContextualNameRule.|  
|Hidden||Valeur booléenne qui indique si le membre est caché dans le client.<br /><br /> La valeur par défaut est False, ce qui signifie que les colonnes sont visibles dans le client.|  
|ReferenceName||Identificateur utilisé pour référencer le membre dans une requête DAX. Si cet attribut est omis, le nom du champ est utilisé.|  
  
## <a name="contextualnamerule-element"></a>Élément ContextualNameRule  
 Ce type simple définit le format d'affectation des noms qui est utilisé pour lever toute ambiguïté des membres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Utilise le nom de l'attribut.|  
|Contexte|Utilise le nom de la relation entrante.|  
|Fusion|Concatène le nom de la relation entrante et le nom de la propriété.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  