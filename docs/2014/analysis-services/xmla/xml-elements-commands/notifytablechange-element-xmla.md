---
title: Élément NotifyTableChange (XMLA) | Documents Microsoft
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
- NotifyTableChange Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64779ceab6d83365755ed212a93685ee3f31837f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142338"
---
# <a name="notifytablechange-element-xmla"></a>Élément NotifyTableChange (XMLA)
  Notifie une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui a été modifiée pour les tables d’une source de données spécifié.  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Objet](../xml-elements-properties/object-element-xmla.md), [TableNotifications](../xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande `NotifyTableChange` permet à une application cliente de notifier explicitement une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qu'une ou plusieurs tables contenues dans une source de données ont été modifiées. Pour la mise en cache proactive, cette notification indique que les objets OLAP relationnels (ROLAP) basés sur ces tables doivent être examinés et mis à jour.  
  
 Cette méthode de notification convient le mieux aux objets ROLAP basés sur des vues ou des requêtes nommées définies dans une vue de source de données dont les modifications peuvent être délicates à détecter et suivre.  
  
 L'élément `Object` doit faire référence à une source de données dans la base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Si l'élément `Object` fait référence à un objet autre qu'une source de données, une erreur survient.  
  
 Pour plus d’informations sur la mise en cache proactive, consultez [Mise en cache proactive &#40;partitions&#41;](../../multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  