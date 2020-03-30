---
title: Modifier l’ordre d’un paramètre de rapport (Générateur de rapports) | Microsoft Docs
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d905dd50fd9001ed3c5b3ad5eaf3016f8f63094f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "77078871"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Modifier l'ordre d'un paramètre de rapport (Générateur de rapports et SSRS)
  Modifiez l'ordre des paramètres de rapport lorsqu'un paramètre dépendant figure dans la liste avant le paramètre dont il dépend. L'ordre des paramètres est important lorsque vous avez des paramètres en cascade ou lorsque vous souhaitez montrer aux utilisateurs la valeur par défaut d'un paramètre avant qu'ils ne choisissent des valeurs pour d'autres paramètres. Un paramètre de rapport dépendant contient une référence, dans sa requête de valeurs par défaut ou de valeurs valides, à un paramètre de requête qui pointe vers un autre paramètre du rapport situé plus loin dans la liste des paramètres du volet **Données du rapport** .  
  
 Lorsque vous exécutez le rapport, l’ordre d’affichage des paramètres dans la barre d’outils de la visionneuse de rapports dépend de l’ordre des paramètres dans le volet **Données du rapport** ainsi que de l’emplacement des paramètres dans le volet des paramètres personnalisés. Pour plus d’informations, consultez [Personnaliser le volet Paramètres dans un rapport &#40;Générateur de rapports&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>Pour modifier l'ordre des paramètres d'un rapport  
  
Vous pouvez modifier l’ordre des paramètres de rapport en effectuant une des opérations suivantes :  
  
-   Dans le volet **Données du rapport** , cliquez sur un paramètre et utilisez les flèches de direction Haut et Bas pour faire monter ou descendre le paramètre dans la liste, comme indiqué sur l’illustration suivante.  Lorsque vous modifiez l’ordre d’un paramètre dans le volet **Données du rapport** , ce paramètre change d’emplacement dans le volet des paramètres.  
  
     ![Modifier l'ordre des paramètres dans le volet Données du rapport](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "Modifier l'ordre des paramètres dans le volet Données du rapport")  
  
-   Dans le volet des paramètres, faites glisser le paramètre vers une nouvelle colonne ou ligne du volet. Lorsque vous modifiez l’emplacement d’un paramètre dans le volet, l’ordre des paramètres change dans le volet **Données du rapport** . Pour plus d’informations sur le déplacement des paramètres dans le volet, consultez [Personnaliser le volet Paramètres dans un rapport &#40;Générateur de rapports&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Didacticiel : ajouter un paramètre à un rapport &#40;Générateur de rapports&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Références à la collection Parameters &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
