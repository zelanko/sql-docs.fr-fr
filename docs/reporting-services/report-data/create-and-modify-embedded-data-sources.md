---
title: "Cr&#233;er et modifier des sources de donn&#233;es incorpor&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c38c2e8-7a29-4f79-a4a3-85ed2b13723b
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 10
---
# Cr&#233;er et modifier des sources de donn&#233;es incorpor&#233;es
  Une source de données incorporée est définie dans une définition de rapport et utilisée uniquement par ce rapport.  
  
## Pour créer une source de données incorporée dans le Concepteur de rapports  
  
1.  Dans la barre d'outils du volet des données de rapport, cliquez sur **Nouveau** , puis sur **Source de données**. La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur l’option **Données du rapport** du menu **Affichage**.  
  
2.  Dans la zone de texte **Nom** , tapez un nom pour la source de données ou acceptez la valeur par défaut. Le nom de la source de données est utilisé en interne dans le rapport. Par souci de clarté, il est recommandé que le nom de la source de données contienne le nom de la base de données spécifiée dans la chaîne de connexion.  
  
3.  Vérifiez que l’option **Connexion incorporée** est sélectionnée et procédez comme suit.  
  
    1.  Dans la liste déroulante **Type**, sélectionnez un type de source de données ; par exemple, **Microsoft SQL Server** ou **OLE DB**.  
  
    2.  Spécifiez une chaîne de connexion à l'aide de l'une des méthodes suivantes :  
  
        -   Tapez directement la chaîne de connexion dans la zone de texte **Chaîne de connexion** . Pour obtenir une liste d’exemples de chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md) ou [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
        -   Cliquez sur le bouton d’expression (**fx)** pour créer une expression qui prend la valeur d’une chaîne de connexion. Dans la boîte de dialogue **Expression** , tapez l'expression dans le volet Expression. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   Cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés de connexion** correspondant au type de source de données choisi à l'étape 2.  
  
             Renseignez les champs de la boîte de dialogue **Propriétés de connexion** comme il convient pour le type de source de données. Les propriétés de connexion incluent le type de la source de données, son nom, ainsi que les informations d'identification à utiliser. Une fois que vous avez spécifié les valeurs dans cette boîte de dialogue, cliquez sur **Tester la connexion** pour vérifier que la source de données est disponible et que les informations d'identification indiquées sont correctes. Pour plus d’informations sur les types de source de données spécifiques, consultez les rubriques dans [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md).  
  
    3.  Cliquez sur **Informations d'identification**.  
  
         Spécifiez les informations d'identification à utiliser pour cette source de données. Le propriétaire de la source de données choisit le type d'informations d'identification pris en charge.  
  
4.  La nouvelle source de données incorporée apparaît dans le volet des données de rapport.  
  
## Pour créer une source de données incorporée dans le Générateur de rapports  
  
1.  Dans la barre d'outils du volet Données du rapport, cliquez sur **Nouveau**, puis sur **Source de données**. La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
2.  Dans la zone de texte **Nom** , tapez un nom pour la source de données ou acceptez la valeur par défaut.  
  
3.  Vérifiez que l'option **Utiliser une connexion incorporée dans mon rapport** est sélectionnée.  
  
    1.  Dans la liste déroulante **Sélectionner un type de connexion**, sélectionnez un type de source de données ; par exemple, **Microsoft SQL Server** ou **OLE DB**.  
  
    2.  Spécifiez une chaîne de connexion en utilisant l'une des méthodes suivantes :  
  
        -   Tapez directement la chaîne de connexion dans la zone de texte **Chaîne de connexion** . Pour obtenir une liste d’exemples de chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md).  
  
        -   Cliquez sur le bouton d’expression (**fx)** pour créer une expression qui prend la valeur d’une chaîne de connexion. Dans la boîte de dialogue **Expression** , tapez l'expression dans le volet Expression. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   Cliquez sur **Générer** pour ouvrir la boîte de dialogue **Propriétés de connexion** correspondant au type de source de données choisi à l'étape 2.  
  
             Renseignez les champs de la boîte de dialogue **Propriétés de connexion** comme il convient pour le type de source de données. Les propriétés de connexion incluent le type de la source de données, son nom, ainsi que les informations d'identification à utiliser. Une fois que vous avez spécifié les valeurs dans cette boîte de dialogue, cliquez sur **Tester la connexion** pour vérifier que la source de données est disponible et que les informations d'identification indiquées sont correctes.  
  
4.  Cliquez sur **Informations d'identification**.  
  
     Spécifiez les informations d'identification à utiliser pour cette source de données. Le propriétaire de la source de données choisit le type d'informations d'identification pris en charge. Pour plus d’informations, consultez [Spécifier des informations d’identification dans le Générateur de rapports](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     La source de données apparaît dans le volet des données de rapport.  
  
## Voir aussi  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Spécifier des informations d'identification dans le Générateur de rapports](../Topic/Specify%20Credentials%20in%20Report%20Builder.md)  
  
  