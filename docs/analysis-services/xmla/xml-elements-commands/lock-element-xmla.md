---
title: Verrouiller l’élément (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b6888d6dcc023dabe98daa36a352a456d70f27b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="lock-element-xmla"></a>Élément Lock (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Verrouille un objet spécifié sur une instance [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md), [Mode](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md), [Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande **Lock** verrouille un objet, pour un usage partagé ou exclusif, dans le contexte de la transaction actuellement active. Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande **Lock** de manière explicite. Un verrou sur un objet empêche la validation des transactions aussi longtemps que le verrou n'est pas supprimé. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge deux types de verrous : les verrous partagés et les verrous exclusifs. Pour plus d’informations sur les types de verrous pris en charge par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], consultez [élément Mode & #40 ; XMLA & #41 ; ](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] autorise uniquement le verrouillage des bases de données. Le **objet** élément doit contenir une référence d’objet une [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données. Si l'élément **Object** n'est pas spécifié ou si cet élément **Object** fait référence à un objet autre qu'une base de données, une erreur survient.  
  
 Autres commandes implicitement problème un **verrou** commande sur une [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données. Toutes les opérations permettant de lire les données ou les métadonnées d'une base de données (par exemple, n'importe quelle méthode **Discover** ou une méthode **Execute** exécutant une commande **Statement** ) émettent implicitement un verrou partagé dans la base de données. Toute transaction qui valide les modifications de données ou les métadonnées pour un objet sur un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de base de données, comme un **Execute** méthode en cours d’exécution un **Alter** command, émettent implicitement un verrou exclusif sur la base de données.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Déverrouiller l’élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Commandes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
