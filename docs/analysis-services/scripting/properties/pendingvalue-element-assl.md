---
title: Élément PendingValue (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 34331b1d222df8c36bf7b770ef01cffd213ae6d4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="pendingvalue-element-assl"></a>Élément PendingValue (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient la lecture seule en attente de la valeur de la [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ServerProperty>  
   ...  
   <PendingValue>...</PendingValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout simpleType|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Cet élément contient la valeur de la **ServerProperty** qui sera utilisée la prochaine fois que l’instance actuelle de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est démarré. Cette valeur est généralement récupérée à partir du lieu de stockage de la valeur de la propriété de serveur : un fichier d'initialisation, le Registre [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ou tout autre mécanisme de stockage.  
  
 L’élément qui correspond au parent de **PendingValue** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ServerProperties & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)   
 [Server, élément & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
