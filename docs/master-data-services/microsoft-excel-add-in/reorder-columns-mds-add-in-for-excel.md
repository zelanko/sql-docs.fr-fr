---
title: "R&#233;organiser des colonnes (Compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# R&#233;organiser des colonnes (Compl&#233;ment MDS pour Excel)
  Dans la [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez réorganiser les colonnes en filtrant la liste avant le chargement.  
  
 Lorsque vous réorganisez les attributs dans le **filtre** boîte de dialogue, les données est chargée dans Excel avec la nouvelle commande. Toutefois, lors du prochain filtrage des données d'attribut, l'ordre rétabli sera celui de la conception d'origine. Pour modifier l’ordre de façon permanente, un administrateur doit modifier l’ordre dans le **Administration système** zone de Master Data Manager. Pour plus d’informations, consultez [Modifier l’ordre des attributs](../../master-data-services/change-the-order-of-attributes.md).  
  
## Configuration requise  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### Pour réorganiser les colonnes managées MDS  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [se connecter à un référentiel MDS & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le **Explorateur de données de référence** volet est désactivé, c’est parce que la feuille existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans la **Explorateur de données de référence** volet, cliquez sur une entité.  
  
4.  Dans le **se connecter et charger** cliquez sur **filtre**.  
  
5.  Dans la **filtre** boîte de dialogue, dans le **colonnes** section, dans la liste des attributs, cliquez sur l’attribut que vous souhaitez déplacer.  
  
6.  À droite de la liste, cliquez sur le **de** ou **bas** flèche pour déplacer l’attribut à gauche et à droite dans la feuille de calcul.  
  
7.  Répétez l'étape 7 pour chaque attribut jusqu'à ce que l'ordre de haut en bas représente l'ordre de gauche à droite que vous souhaitez dans la feuille de calcul.  
  
8.  Cliquez sur **charger des données**. La feuille est renseignée avec les données managées MDS et les colonnes sont affichées dans l'ordre que vous avez spécifié.  
  
## Voir aussi  
 [Vue d’ensemble : Exportation des données vers Excel & #40 ; Complément MDS pour Excel & #41 ;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  