---
title: "Élément MiningStructurePermission (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningStructurePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningStructurePermission
helpviewer_keywords:
- MiningStructurePermission element
ms.assetid: 4ba2bfd2-9003-4eed-8049-a74d452894ea
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22713569509019e9d0aac30f82c898c73a034fda
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="miningstructurepermission-element-assl"></a>Élément MiningStructurePermission (ASSL)
  Définit les autorisations que les membres d’un [rôle](../../../analysis-services/scripting/objects/role-element-assl.md) élément avoir un individu [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructurePermissions>  
   <MiningStructurePermission xsi:type="Permission">  
      <AllowDrillthrough>...</AllowDrillthrough>  
  
      <!-- This element also inherits all the child elements listed in Permission -->  
   </MiningStructurePermission>  
</MiningStructurePermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], l’autorisation **AllowDrillthrough** a été étendu pour appliquer à une structure d’exploration de données. Lorsque vous assignez cette autorisation à un rôle, tout utilisateur qui est membre de ce rôle peut interroger directement la structure d'exploration de données en utilisant la syntaxe suivante :  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 De plus, si **AllowDrillthrough** est activé sur la structure d'exploration de données et le modèle d'exploration de données, les utilisateurs peuvent interroger les colonnes de structure qui n'étaient pas incluses dans le modèle d'exploration de données en utilisant la syntaxe suivante :  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 Par exemple, vous créez un modèle qui utilise uniquement des colonnes pour la clé des clients, les revenus des clients et les achats des clients. En utilisant l'extraction, un utilisateur peut retourner d'autres colonnes de structure qui n'étaient pas incluses dans le modèle d'exploration de données, telles que les informations de contact client.  
  
 Par conséquent, pour protéger des données sensibles ou des informations personnelles, vous devez construire votre vue de source de données de manière à masquer les informations personnelles et accorder l'autorisation **AllowDrillthrough** sur une structure uniquement si cela est nécessaire.  
  
 Pour plus d’informations, consultez [Requêtes d’extraction &#40;exploration de données&#41;](../../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
