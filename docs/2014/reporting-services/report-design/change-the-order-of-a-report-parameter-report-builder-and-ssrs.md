---
title: Modifier l’ordre d’un paramètre de rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 199b83364fceb93e59b9a1b32824166448a4c23f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191289"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Modifier l'ordre d'un paramètre de rapport (Générateur de rapports et SSRS)
  Modifiez l'ordre des paramètres de rapport lorsqu'un paramètre dépendant figure dans la liste avant le paramètre dont il dépend. L'ordre des paramètres est important lorsque vous avez des paramètres en cascade ou lorsque vous souhaitez montrer aux utilisateurs la valeur par défaut d'un paramètre avant qu'ils ne choisissent des valeurs pour d'autres paramètres. Un paramètre de rapport dépendant contient une référence, dans sa requête de valeurs par défaut ou de valeurs valides, à un paramètre de requête qui pointe vers un autre paramètre du rapport situé plus loin dans la liste des paramètres du volet Données du rapport.  
  
 L'ordre d'affichage des paramètres dans la barre d'outils de la visionneuse de rapports dépend de l'ordre des paramètres dans le volet Données du rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a>Pour modifier l'ordre des paramètres d'un rapport  
  
1.  Dans le volet Données du rapport, développez le nœud Paramètres.  
  
2.  Cliquez sur un paramètre et utilisez les flèches de direction Haut et Bas de la barre d'outils du volet des données de rapportpour faire monter ou descendre le paramètre dans la liste. L'illustration suivante montre le volet des données de rapport du Générateur de rapports.  
  
     ![Volet données du rapport](../media/reportdatapane.png "volet données du rapport")  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Didacticiel : ajouter un paramètre à un rapport &#40;Générateur de rapports&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Références à la Collection Parameters &#40;Générateur de rapports et SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
