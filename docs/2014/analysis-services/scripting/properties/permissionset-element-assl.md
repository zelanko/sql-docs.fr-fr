---
title: Élément PermissionSet (ASSL) | Documents Microsoft
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
- PermissionSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6246058af826a73b589f1854b0236de946a4d65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141642"
---
# <a name="permissionset-element-assl"></a>Élément PermissionSet (ASSL)
  Identifie le jeu d’autorisations associé à un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] assembly .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ClrAssembly>  
   ...  
   <PermissionSet>...</PermissionSet>  
  
</ClrAssembly>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Safe*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Safe*|Seul un accès aux données local et le calcul interne sont autorisés. *Safe* est le jeu d'autorisations le plus restrictif. Le code exécuté par un assembly à l'aide des autorisations *Safe* ne peut pas accéder aux ressources système externes telles que les fichiers, le réseau, les variables d'environnement ou le Registre.|  
|*ExternalAccess*|*Safe*avec possibilité en prime d'accéder aux ressources système externes, notamment aux fichiers, aux réseaux, aux variables d'environnement et au Registre.|  
|*Non restreint*|Unrestricted autorise l’accès sans restriction aux ressources, au sein et en dehors de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code qui s'exécute dans un assembly *Unrestricted* peut appeler du code non managé.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `PermissionSet` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Élément Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Élément serveur &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  