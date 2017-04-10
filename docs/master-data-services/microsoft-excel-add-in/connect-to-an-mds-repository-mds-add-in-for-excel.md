---
title: "Se connecter &#224; un r&#233;f&#233;rentiel MDS (Compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Se connecter &#224; un r&#233;f&#233;rentiel MDS (Compl&#233;ment MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous devez vous connecter à un référentiel MDS avant de pouvoir charger ou publier des données.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### Pour vous connecter à un référentiel MDS  
  
1.  Dans le Complément MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], sous l’onglet **Données de référence**, dans le groupe **Se connecter et charger**, cliquez sur la flèche du bas sous le bouton **Se connecter** et cliquez sur **Gérer les connexions**.  
  
2.  Dans la boîte de dialogue **Gérer les connexions**, dans la section **Nouvelle connexion**, cliquez sur **Créer une connexion**.  
  
3.  Cliquez sur **Nouveau**.  
  
4.  Dans la boîte de dialogue **Ajouter une nouvelle connexion**, dans le champ **Description**, tapez une description pour votre connexion. Cette connexion s’affiche lorsque vous cliquez sur la flèche sous le bouton **Se connecter** dans la barre d’outils.  
  
5.  Dans la zone **Adresse du serveur MDS**, tapez l’URL de l’application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], par exemple http://contoso/mds.  
  
    > [!NOTE]  
    >  Vérifiez que vous utilisez le nom d'ordinateur ; n'utilisez pas « localhost ».  
  
6.  Cliquez sur **OK**. Le nom est affiché dans la section **Connexions existantes**.  
  
7.  Vous pouvez également cliquer sur **Tester** pour tester la connexion. Une boîte de dialogue de confirmation ou d'erreur s'affiche. Cliquez sur **OK** pour la fermer.  
  
8.  Cliquez sur **Se connecter**. Le volet **Master Data Services** est affiché.  
  
## Étapes suivantes  
  
-   [Exporter des données vers Excel à partir de Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [Filtrer les données avant l’exportation &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## Voir aussi  
 [Connexions &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  