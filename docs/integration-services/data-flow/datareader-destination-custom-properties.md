---
description: Propriétés personnalisées de la destination DataReader
title: Propriétés personnalisées de la destination DataReader | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cf82f80425dcc00cb3129d051ca233af55ad783
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194844"
---
# <a name="datareader-destination-custom-properties"></a>Propriétés personnalisées de la destination DataReader

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La destination DataReader comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination DataReader. Toutes les propriétés sont en lecture/écriture, à l’exception de **DataReader** .  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|Nom de classe de la destination DataReader.|  
|FailOnTimeout|Boolean|Indique s’il faut faire échouer l’opération ou non quand un **ReadTimeout** se produit. La valeur par défaut de cette propriété est **False**.|  
|ReadTimeout|Integer|Nombre de millisecondes devant s'écouler avant l'expiration du délai d'attente. La valeur par défaut de cette propriété est 30000 (30 secondes).|  
  
 L'entrée et les colonnes d'entrée de la destination DataReader ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination DataReader](../../integration-services/data-flow/datareader-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](./set-the-properties-of-a-data-flow-component.md)  
  
