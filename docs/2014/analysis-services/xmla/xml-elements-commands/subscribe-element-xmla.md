---
title: Élément Subscribe (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Subscribe Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords:
- Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf88b3e4e2fd990ad786b8e505c908f96f53ce6e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079339"
---
# <a name="subscribe-element-xmla"></a>Élément Subscribe (XMLA)
  S’abonne à une trace et retourne un ensemble de lignes qui contient les événements de trace à partir d’un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Objet](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le `Subscribe` commande s’abonne à et flux de données retourne un ensemble de lignes à partir d’une trace spécifiée sur un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. Si un objet autre qu’une trace est spécifié dans le `Object` élément, une erreur se produit.  
  
 Si aucun élément `Object` n'est spécifié, une trace de session est définie et l'abonnement à cette dernière a lieu sur l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La trace de session retourne un ensemble fixe d'événements de trace à partir de la session en cours.  
  
 Le flux d’ensemble de lignes retourné par cette commande est interrompu si l’application cliente ferme la connexion à la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, ou si la session sur laquelle la `Subscribe` commande est exécutée est arrêtée.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
