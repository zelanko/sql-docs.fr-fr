---
title: "&#201;diteur de source CDC (page Colonnes) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.cdcsource.columns.f1"
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#201;diteur de source CDC (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de source CDC** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
 Pour en savoir plus sur la source CDC, consultez [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## Liste des tâches  
 **Pour ouvrir l'Éditeur de source CDC (page Colonnes)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] qui possède la source CDC.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la source CDC.  
  
3.  Dans l' **Éditeur de source CDC**, cliquez sur **Colonnes**.  
  
## Options  
 **Colonnes externes disponibles**  
 Liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table. Sélectionnez les colonnes à utiliser dans la source. Les colonnes sélectionnées sont ajoutées à la liste **Colonne externe** dans l'ordre de leur sélection.  
  
 **Colonne externe**  
 Vue des colonnes externes (sources) selon l'ordre dans lequel vous les visualisez lorsque vous configurez des composants qui consomment des données à partir de la source CDC. Vous pouvez modifier cet ordre en supprimant d'abord les colonnes sélectionnées dans la liste **Colonnes externes disponibles** , puis en choisissant des colonnes externes dans la liste selon un ordre différent. Les colonnes sélectionnées sont ajoutées à la liste **Colonne externe** dans l'ordre de leur sélection.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; toutefois, vous pouvez choisir n'importe quel nom unique et descriptif. Le nom entré est affiché dans le concepteur SSIS.  
  
## Voir aussi  
 [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [Éditeur de source CDC &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/cdc-source-editor-error-output-page.md)  
  
  