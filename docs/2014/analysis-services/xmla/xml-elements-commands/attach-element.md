---
title: Élément Attach | Documents Microsoft
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
helpviewer_keywords:
- Attach command
ms.assetid: a315d1f1-e220-4296-97cb-6d35606b9640
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 0052882eec86aeb74dca98a21ebf236d1b0a65e1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043922"
---
# <a name="attach-element"></a>Élément Attach
  Attache une base de données [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] précédemment détachée de l'instance de serveur actuelle ou d'une autre instance, à l'instance de serveur actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Attach>  
      <Folder>...</Folder>  
            <ReadWriteMode>...</ReadWriteMode>  
            <Password>...</Password>  
   </Attach>  
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
|Éléments enfants|[Dossier](../xml-elements-properties/folder-element-xmla.md)<br /><br /> [ReadWriteMode](../xml-elements-properties/readwritemode-element.md)<br /><br /> [Mot de passe](../xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Élément Detach](detach-element.md)   
 [Attacher et détacher des bases de données Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Base de données ReadWriteModes](../../multidimensional-models/database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  