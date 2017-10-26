---
title: "Élément PermissionSet (ASSL) | Documents Microsoft"
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
- PermissionSet Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1448c3db59f149697fa429e6d122d9d20fd403f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Safe*|Seul un accès aux données local et le calcul interne sont autorisés. *Safe* est le jeu d'autorisations le plus restrictif. Le code exécuté par un assembly à l'aide des autorisations *Safe* ne peut pas accéder aux ressources système externes telles que les fichiers, le réseau, les variables d'environnement ou le Registre.|  
|*ExternalAccess*|*Safe*avec possibilité en prime d'accéder aux ressources système externes, notamment aux fichiers, aux réseaux, aux variables d'environnement et au Registre.|  
|*Non restreint*|Unrestricted autorise l’accès sans restriction aux ressources, au sein et en dehors de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code qui s'exécute dans un assembly *Unrestricted* peut appeler du code non managé.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **PermissionSet** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Élément Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Élément de la base de données &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Server, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

