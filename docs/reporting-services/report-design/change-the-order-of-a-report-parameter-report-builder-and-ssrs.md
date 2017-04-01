---
title: "Modifier l&#39;ordre d&#39;un param&#232;tre de rapport (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Modifier l&#39;ordre d&#39;un param&#232;tre de rapport (G&#233;n&#233;rateur de rapports et SSRS)
  Modifiez l'ordre des paramètres de rapport lorsqu'un paramètre dépendant figure dans la liste avant le paramètre dont il dépend. L'ordre des paramètres est important lorsque vous avez des paramètres en cascade ou lorsque vous souhaitez montrer aux utilisateurs la valeur par défaut d'un paramètre avant qu'ils ne choisissent des valeurs pour d'autres paramètres. Un paramètre de rapport dépendant contient une référence, dans sa requête de valeurs par défaut ou de valeurs valides, à un paramètre de requête qui pointe vers un autre paramètre du rapport situé plus loin dans la liste des paramètres du volet **Données du rapport** .  
  
 Lorsque vous exécutez le rapport, l’ordre d’affichage des paramètres dans la barre d’outils de la visionneuse de rapports dépend de l’ordre des paramètres dans le volet **Données du rapport** ainsi que de l’emplacement des paramètres dans le volet des paramètres personnalisés. Pour plus d’informations, consultez [Personnaliser le volet Paramètres dans un rapport &#40;Générateur de rapports&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Pour modifier l'ordre des paramètres d'un rapport  
  
Vous pouvez modifier l’ordre des paramètres de rapport en effectuant une des opérations suivantes :  
  
-   Dans le volet **Données du rapport** , cliquez sur un paramètre et utilisez les flèches de direction Haut et Bas pour faire monter ou descendre le paramètre dans la liste, comme indiqué sur l’illustration suivante.  Lorsque vous modifiez l’ordre d’un paramètre dans le volet **Données du rapport** , ce paramètre change d’emplacement dans le volet des paramètres.  
  
     ![Change the order of the parameters in the Report Data pane](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "Change the order of the parameters in the Report Data pane")  
  
-   Dans le volet des paramètres, faites glisser le paramètre vers une nouvelle colonne ou ligne du volet. Lorsque vous modifiez l’emplacement d’un paramètre dans le volet, l’ordre des paramètres change dans le volet **Données du rapport** . Pour plus d’informations sur le déplacement des paramètres dans le volet, consultez [Personnaliser le volet Paramètres dans un rapport &#40;Générateur de rapports&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](http://msdn.microsoft.com/fr-fr/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Didacticiel : Ajouter un paramètre à un rapport &#40;Générateur de rapports&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add dataset filters, data region filters, and group filters.md)   
 [Références à la collection Parameters &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/parameters-collection-references-report-builder-and-ssrs.md)  
  
  