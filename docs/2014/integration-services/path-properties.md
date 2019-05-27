---
title: Propriétés du chemin d’accès | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fc13943df93acf2227b089b177cdca6c86ee1831
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66056661"
---
# <a name="path-properties"></a>Propriétés du chemin d'accès
  Les objets de flux de données dans le modèle d’objet [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ont des propriétés communes et des propriétés personnalisées au niveau du composant, des entrées et sorties, et des colonnes d’entrée et colonnes de sortie. De nombreuses propriétés ont des valeurs en lecture seule qui sont assignées au moment de l'exécution par le moteur de flux de données.  
  
 Cette rubrique répertorie et décrit les propriétés personnalisées des chemins d'accès qui connectent des objets de flux de données.  
  
## <a name="path-properties"></a>Propriétés du chemin d'accès  
 Dans le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], un chemin d'accès qui connecte des composants dans le flux de données implémente l'interface <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>.  
  
 Le tableau suivant décrit les propriétés configurables des chemins d'accès dans un flux de données. Le moteur de flux de données assigne également des valeurs à d'autres propriétés en lecture seule qui ne sont pas répertoriées ici.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Integer (énumération)|Valeur qui indique si une annotation doit être affichée avec le chemin d'accès sur l'aire du concepteur. Les valeurs possibles sont `AsNeeded`, `SourceName`, `PathName` et `Never`. La valeur par défaut est `AsNeeded`.|  
|DestinationName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|Entrée associée au chemin d'accès.|  
|SourceName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|Sortie associée au chemin d'accès.|  
  
## <a name="see-also"></a>Voir aussi  
 [Chemins Integration Services](data-flow/integration-services-paths.md)   
 [Propriétés communes](../../2014/integration-services/common-properties.md)   
 [Propriétés personnalisées de transformation](data-flow/transformations/transformation-custom-properties.md)   
 [Propriétés du flux de données pouvant être définies à l’aide d’expressions](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
