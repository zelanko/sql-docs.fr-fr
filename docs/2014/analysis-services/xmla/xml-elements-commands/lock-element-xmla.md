---
title: Verrouiller l’élément (XMLA) | Documents Microsoft
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
- Lock Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d454cdcc6a87335670f483ccc06a7547e89dc7c9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052025"
---
# <a name="lock-element-xmla"></a>Élément Lock (XMLA)
  Verrouille un objet spécifié sur un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[ID](../xml-elements-properties/id-element-xmla.md), [Mode](../xml-elements-properties/mode-element-xmla.md), [objet](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande `Lock` verrouille un objet, pour un usage partagé ou exclusif, dans le contexte de la transaction actuellement active. Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande `Lock` de manière explicite. Un verrou sur un objet empêche la validation des transactions aussi longtemps que le verrou n'est pas supprimé. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge deux types de verrous : les verrous partagés et les verrous exclusifs. Pour plus d’informations sur les types de verrous pris en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], consultez [élément Mode &#40;XMLA&#41;](../xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] autorise uniquement le verrouillage des bases de données. L'élément `Object` doit contenir une référence d'objet à une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Si l'élément `Object` n'est pas spécifié ou si cet élément `Object` fait référence à un objet autre qu'une base de données, une erreur survient.  
  
 D'autres commandes permettent d'émettre une commande `Lock` dans une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de manière implicite. Toutes les opérations permettant de lire les données ou les métadonnées d'une base de données (par exemple, n'importe quelle méthode `Discover` ou une méthode `Execute` exécutant une commande `Statement`) émettent implicitement un verrou partagé dans la base de données. Toutes les transactions qui valident des modifications apportées aux données ou aux métadonnées d'un objet dans une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (par exemple, une méthode `Execute` exécutant une commande `Alter`) émettent implicitement un verrou exclusif dans la base de données.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Unlock &#40;XMLA&#41;](lock-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  