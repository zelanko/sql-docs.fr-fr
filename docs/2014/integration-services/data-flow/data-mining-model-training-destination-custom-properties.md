---
title: Propriétés personnalisées de la destination d’apprentissage du modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f70d32549bb99458b06b835240e826d15967d9b6
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376687"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données
  La destination d'apprentissage du modèle d'exploration de données comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données. Toutes les propriétés sont en lecture/écriture.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|Identificateur unique du gestionnaire de connexions.|  
|ASConnectionString|String|Chaîne de connexion d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|ObjectRef|String|Balise XML qui identifie la structure d'exploration de données utilisée par la transformation.|  
  
 L'entrée et les colonnes d'entrée de la destination d'apprentissage du modèle d'exploration de données ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination d’apprentissage du modèle d’exploration de données](data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
