---
title: Propriétés personnalisées de la destination DataReader | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6bda3a31cf3d498d59d4ec86c6c7b32bd2134385
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158630"
---
# <a name="datareader-destination-custom-properties"></a>Propriétés personnalisées de la destination DataReader
  La destination DataReader comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination DataReader. Toutes les propriétés à l’exception de `DataReader` sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|Nom de classe de la destination DataReader.|  
|FailOnTimeout|Booléen|Indique s'il faut faire échouer l'opération ou non lorsqu'un `ReadTimeout` se produit. La valeur par défaut de cette propriété est **False**.|  
|ReadTimeout|Entier|Nombre de millisecondes devant s'écouler avant l'expiration du délai d'attente. La valeur par défaut de cette propriété est 30000 (30 secondes).|  
  
 L'entrée et les colonnes d'entrée de la destination DataReader ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination DataReader](datareader-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
