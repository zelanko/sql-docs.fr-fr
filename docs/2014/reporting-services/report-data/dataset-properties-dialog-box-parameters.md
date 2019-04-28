---
title: Boîte de dialogue Propriétés du dataset, Paramètres | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b756349acfc55a85c67e3a24921061bb1173e97
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62696520"
---
# <a name="dataset-properties-dialog-box-parameters"></a>Boîte de dialogue Propriétés du dataset, Paramètres
  Sélectionnez **Paramètres** dans la boîte de dialogue **Propriétés du dataset** pour ajouter, modifier et supprimer des paramètres de requête, y compris ceux qui sont liés aux paramètres de rapport.  
  
 Lorsque la requête est modifiée sous l'onglet Requête, la commande de requête est analysée. Pour chaque paramètre de requête identifié, un paramètre de rapport avec un nom respectant la casse identique est créé. Par défaut, le paramètre de requête est ajouté automatiquement à la liste des paramètres de requête et lié au paramètre de rapport correspondant.  
  
 Pour les valeurs par défaut, s’il existe des dépendances entre un paramètre de rapport et un autre qui est lié à un paramètre de requête, l’ordre des paramètres de rapport (tels qu’ils apparaissent dans la boîte de dialogue **Propriétés du paramètre de rapport** ) est important. Des paramètres de rapport figurant plus bas dans la liste peuvent faire référence à des paramètres de rapport situés plus haut dans la liste. Pour plus d’informations sur les paramètres de rapport, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Ajoutez un nouveau paramètre à la liste.  
  
 **Supprimer**  
 Supprimez le paramètre sélectionné de la liste.  
  
 **Nom du paramètre**  
 Tapez le nom d’un paramètre de requête que vous avez ajouté au dataset sous l’onglet **Requête** de la boîte de dialogue **Propriétés du dataset** .  
  
 **Valeur du paramètre**  
 Entrez une valeur pour le paramètre de requête. Il peut s'agir d'une valeur statique ou d'une expression faisant référence à un objet présent dans le rapport ; toutefois, elle ne peut pas faire référence à des éléments de rapport ou des champs. Par défaut, **Valeur** contient une expression qui pointe vers un paramètre de rapport.  
  
 **Flèche haut**  
 Déplacez le paramètre sélectionné vers le haut de la liste.  
  
 **Flèche bas**  
 Déplacez le paramètre sélectionné vers le bas de la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
