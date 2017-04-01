---
title: "&#201;diteur de source ODBC (page Colonnes) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcsource.columns.f1"
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# &#201;diteur de source ODBC (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de source ODBC** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
 Pour en savoir plus sur la source ODBC, consultez [ODBC Source](../../integration-services/data-flow/odbc-source.md).  
  
## Liste des tâches  
 **Pour ouvrir l'Éditeur de source ODBC (page Colonnes)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] qui possède la source ODBC.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la source ODBC.  
  
3.  Dans l' **Éditeur de source ODBC**, cliquez sur **Colonnes**.  
  
## Options  
  
### Colonnes externes disponibles  
 Liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table. Sélectionnez les colonnes à utiliser dans la source. Les colonnes sélectionnées sont ajoutées à la liste **Colonne externe** dans l'ordre de leur sélection.  
  
 Activez la case à cocher **Sélectionner tout** pour sélectionner toutes les colonnes.  
  
### Colonne externe  
 Vue des colonnes externes (sources) selon l'ordre dans lequel vous les visualisez lorsque vous configurez des composants qui consomment des données à partir de la source ODBC.  
  
### Colonne de sortie  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif. Le nom entré est affiché dans le concepteur SSIS.  
  
## Voir aussi  
 [Éditeur de source ODBC &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [Éditeur de source ODBC &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  