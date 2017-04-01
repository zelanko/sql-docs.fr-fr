---
title: "Filtrer les donn&#233;es avant l’exportation (compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Filtrer les donn&#233;es avant l’exportation (compl&#233;ment MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filtrer les données lorsque vous souhaitez limiter la taille ou l’étendue des données que vous exportez vers Excel.  
  
## Configuration requise  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### Pour filtrer les données avant l’exportation  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [se connecter à un référentiel MDS & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le **Explorateur de données de référence** volet est désactivé, c’est parce que la feuille existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans la **Explorateur de données de référence** volet, dans la liste des entités, cliquez sur l’entité que vous souhaitez filtrer.  
  
4.  Sur le ruban, dans le **se connecter et charger** cliquez sur **filtre**.  
  
5.  Terminer la **filtre** boîte de dialogue en sélectionnant les attributs (colonnes) à afficher, définissez l’ordre des colonnes et si nécessaire, filtrer les données afin de retourner moins de lignes. Afficher la **Résumé** volet affichera la quantité de données. Pour plus d’informations, consultez [boîte de dialogue filtre & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Cliquez sur **charger des données**. La feuille est renseignée avec les données managées MDS.  
  
    > [!NOTE]  
    >  -   Seul le premier million de membres est chargé dans Excel.  
    > -   Dans les colonnes qui représentent des listes contraintes (attributs basés sur un domaine), seules les 25 000 premières valeurs sont chargées par défaut.  
  
## Étapes suivantes  
 [Importer des données à partir d’Excel pour Master Data Services & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## Voir aussi  
 [Vue d’ensemble : Exportation des données vers Excel & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Boîte de dialogue filtre & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Réorganiser les colonnes & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  