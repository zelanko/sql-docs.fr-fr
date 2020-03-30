---
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
ms.openlocfilehash: e603b7e7342ee349b885392c43e42f33009700ae
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71293128"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Propriétés personnalisées de la destination d'apprentissage du modèle d'exploration de données

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
