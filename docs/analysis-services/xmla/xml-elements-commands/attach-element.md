---
title: Élément Attach | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e541916cfb1bf60f365e2e4ac5bf3eb08ed3136
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="attach-element"></a>Élément Attach
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Dossier](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)<br /><br /> [readWriteMode](../../../analysis-services/xmla/xml-elements-properties/readwritemode-element.md)<br /><br /> [Mot de passe](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Élément Detach](../../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Attacher et détacher des bases de données Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Base de données ReadWriteModes](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
