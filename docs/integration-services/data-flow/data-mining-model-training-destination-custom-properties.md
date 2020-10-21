---
description: Propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données
title: Propriétés personnalisées de la destination d’apprentissage du modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ed5f1b09cbbaa4d20c891a03d9846949eedc8bc
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196439"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La destination d'apprentissage du modèle d'exploration de données comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données. Toutes les propriétés sont en lecture/écriture.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|Identificateur unique du gestionnaire de connexions.|  
|ASConnectionString|String|Chaîne de connexion d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|ObjectRef|String|Balise XML qui identifie la structure d'exploration de données utilisée par la transformation.|  
  
 L'entrée et les colonnes d'entrée de la destination d'apprentissage du modèle d'exploration de données ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination d’apprentissage du modèle d’exploration de données](../../integration-services/data-flow/data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](./set-the-properties-of-a-data-flow-component.md)  
  
