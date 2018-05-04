---
title: Élément NotifyTableChange (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- NotifyTableChange Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 079f1ffa948694e48eee8193f5d11be76ef93e5c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="notifytablechange-element-xmla"></a>Élément NotifyTableChange (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Notifie une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qu'une modification a été apportée à des tables dans une source de données spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <NotifyTableChange>  
      <Object>...</Object>  
      <TableNotifications>...</TableNotifications>  
   </NotifyTableChange>  
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
|Éléments enfants|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **NotifyTableChange** commande permet à une application cliente notifier explicitement une [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de l’instance que l’une ou plusieurs tables contenues dans une source de données ont été modifiés. Pour la mise en cache proactive, cette notification indique que les objets OLAP relationnels (ROLAP) basés sur ces tables doivent être examinés et mis à jour.  
  
 Cette méthode de notification convient le mieux aux objets ROLAP basés sur des vues ou des requêtes nommées définies dans une vue de source de données dont les modifications peuvent être délicates à détecter et suivre.  
  
 Le **objet** doit faire référence à une source de données dans le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données. Si l'élément **Object** fait référence à un objet autre qu'une source de données, une erreur survient.  
  
 Pour plus d’informations sur la mise en cache proactive, consultez [Mise en cache proactive &#40;partitions&#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
