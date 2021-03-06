---
title: Boîte de dialogue Propriétés du dataset, Paramètres | Microsoft Docs
description: Découvrez comment utiliser la propriété Paramètres dans la boîte de dialogue Propriétés du dataset pour ajouter, changer et supprimer des paramètres de requête.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10150"
- sql13.rtp.rptdesigner.datasetproperties.parameters.f1
- "10023"
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fc0f85dbd100593549ab3f543dfaf4f95e0d91ba
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812240"
---
# <a name="dataset-properties-dialog-box-parameters"></a>Boîte de dialogue Propriétés du dataset, Paramètres
  Sélectionnez **Paramètres** dans la boîte de dialogue **Propriétés du dataset** pour ajouter, modifier et supprimer des paramètres de requête, y compris ceux qui sont liés aux paramètres de rapport.  
  
 Lorsque la requête est modifiée sous l'onglet Requête, la commande de requête est analysée. Pour chaque paramètre de requête identifié, un paramètre de rapport avec un nom respectant la casse identique est créé. Par défaut, le paramètre de requête est ajouté automatiquement à la liste des paramètres de requête et lié au paramètre de rapport correspondant.  
  
 Pour les valeurs par défaut, s’il existe des dépendances entre un paramètre de rapport et un autre qui est lié à un paramètre de requête, l’ordre des paramètres de rapport (tels qu’ils apparaissent dans la boîte de dialogue **Propriétés du paramètre de rapport** ) est important. Des paramètres de rapport figurant plus bas dans la liste peuvent faire référence à des paramètres de rapport situés plus haut dans la liste. Pour plus d’informations sur les paramètres de rapport, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
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
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Jeux de données du rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
