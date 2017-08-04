---
title: Configurer Data Streaming Destination | Documents Microsoft
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL11.DTS.DESIGNER.DATASTREAMINGDEST.F1
ms.assetid: bcdbb833-20c8-47ff-a641-bb517f9a1af3
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3ef9bf1887ec05effe76c456011bac71b370eb3b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="configure-data-streaming-destination"></a>Configurer Data Streaming Destination
  Configurez Data Streaming Destination à l’aide de la boîte de dialogue **Éditeur avancé pour Data Streaming Destination** . Pour ouvrir cette boîte de dialogue, double-cliquez sur le composant ou cliquez avec le bouton droit sur le composant dans le concepteur de flux de données, puis cliquez sur **Modifier**.  
  
 Cette boîte de dialogue comporte trois onglets : **Propriétés du composant**, **Colonnes d’entrée**et **Propriétés d’entrée et de sortie**.  
  
## <a name="component-properties-tab"></a>Onglet Propriétés du composant  
 Cet onglet comprend les champs modifiables suivants :  
  
|Champ|Description|  
|-----------|-----------------|  
|Nom|Nom du composant Data Streaming Destination dans le package.|  
|ValidateExternalMetadata|Indique si le composant est validé à l’aide de sources de données externes au moment de la conception. Si la propriété est définie sur false, la validation avec des sources de données externes est différée jusqu’au moment de l’exécution.|  
|IDColumnName|La vue générée par l’Assistant Publication des flux de données contient cette colonne d’ID supplémentaire. La colonne d’ID est utilisée comme valeur EntityKey pour les données de sortie du flux de données lorsque les données sont consommées comme flux OData par d’autres applications.<br /><br /> Le nom par défaut de cette colonne est _ID. Vous pouvez spécifier un autre nom pour la colonne d’ID.|  
  
## <a name="input-columns-tab"></a>Onglet Colonnes d’entrée  
 Toutes les colonnes d’entrée disponibles s’affichent dans le volet supérieur de cet onglet. Sélectionnez les colonnes que vous souhaitez inclure dans la sortie de ce composant. Les colonnes sélectionnées sont affichées sous forme de liste dans le volet inférieur. Vous pouvez modifier le nom de la colonne de sortie en tapant le nouveau nom du champ **Alias de sortie** dans la liste.  
  
## <a name="input-output-properties-tab"></a>Onglet Propriétés d’entrée et de sortie  
 Cet onglet est similaire à l’onglet Colonnes d’entrée. Vous pouvez modifier les noms des colonnes de sortie dans cet onglet. Dans l’arborescence à gauche, développez **Entrée de Data Streaming Destination** , puis **Colonnes d’entrée**. Cliquez sur le nom de la colonne d’entrée et modifiez le nom de la colonne de sortie dans le volet droit.  
  
## <a name="see-also"></a>Voir aussi  
 [Data Streaming Destination](../../integration-services/data-flow/data-streaming-destination.md)   
 [Procédure pas à pas : publier un package SSIS en tant que vue SQL](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md)  
  
  
