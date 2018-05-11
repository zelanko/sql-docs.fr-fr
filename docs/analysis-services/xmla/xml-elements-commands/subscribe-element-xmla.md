---
title: Élément Subscribe (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78fb69cc1a9843f4ebbc01711f3e5be5d0146ec6
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="subscribe-element-xmla"></a>Élément Subscribe (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  S’abonne à une trace et retourne un ensemble de lignes qui contient les événements de trace d’un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
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
|Éléments enfants|[Objet](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **s’abonner** commande s’abonne à et flux de sauvegarder un ensemble de lignes à partir d’une trace spécifiée sur un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. Si un objet autre qu'une trace est spécifié dans l'élément **Object** , une erreur survient.  
  
 Si le **objet** élément n’est pas spécifié, une trace de session est définie et l’abonné sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. La trace de session retourne un ensemble fixe d'événements de trace à partir de la session en cours.  
  
 Le flux de l’ensemble de lignes retourné par cette commande est terminé si l’application cliente ferme la connexion à la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, ou si la session sur laquelle le **s’abonner** commande est exécutée est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
