---
title: "Combiner des donn&#233;es (Compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Combiner des donn&#233;es (Compl&#233;ment MDS pour Excel)
  Dans la [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combiner des données de deux feuilles de calcul lorsque vous souhaitez comparer les données avant la publication. Dans cette procédure, vous combinez les données de deux feuilles de calcul en une seule. Vous pouvez ensuite réaliser d'autres comparaisons et déterminer les données, le cas échéant, à publier dans le référentiel MDS.  
  
## Configuration requise  
  
-   Vous devez disposer d'une feuille de calcul qui contient des données managées MDS. Pour plus d’informations, consultez [Exporter les données vers Excel à partir de Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
-   Vous devez disposer d'une feuille de calcul qui contient les données que vous souhaitez combiner avec les données managées MDS. Cette feuille doit avoir une ligne d'en-tête.  
  
### Pour combiner des données non managées dans une feuille managée MDS  
  
1.  Dans la feuille qui contient des données managées MDS, dans le **publier et valider** cliquez sur **combiner des données**.  
  
2.  Dans la **combiner des données** boîte de dialogue, à côté du **plage à combiner avec les données MDS** texte, cliquez sur l’icône. La boîte de dialogue se réduit.  
  
3.  Cliquez sur la feuille contenant les données que vous souhaitez combiner.  
  
4.  Mettez en surbrillance toutes les cellules de la feuille que vous souhaitez combiner, notamment la ligne d'en-tête.  
  
5.  Dans la **combiner des données** boîte de dialogue, cliquez sur l’icône. La boîte de dialogue se développe.  
  
6.  Pour une colonne répertoriée pour l’entité MDS, sélectionnez une colonne sous **colonne correspondante**. Toutes les colonnes MDS n'ont pas besoin de colonnes correspondantes.  
  
7.  Cliquez sur **combiner**. Un **SOURCE** colonne s’affiche, indiquant si les données sont à partir de MDS ou d’une source externe.  
  
## Étapes suivantes  
  
-   Pour rechercher des similitudes entre les données managées MDS et externes, consultez [correspondance des données similaires & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md).  
  
## Voir aussi  
 [Vue d’ensemble : Exportation des données vers Excel & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  