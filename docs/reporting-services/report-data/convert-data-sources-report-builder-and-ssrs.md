---
title: "Convertir des sources de donn&#233;es (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sources de données [Reporting Services], incorporées"
  - "sources de données [Reporting Services], partagées"
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
caps.latest.revision: 16
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# Convertir des sources de donn&#233;es (G&#233;n&#233;rateur de rapports et SSRS)
  Chaque source de données dans le volet des données de rapport est incorporée et est spécifique au rapport ou est partagée. Dans le Générateur de rapports, une source de données partagée pointe vers une source de données partagée publiée sur un serveur de rapports ou un site SharePoint. Dans le Concepteur de rapports, une source de données partagée pointe vers une source de données partagée dans l’Explorateur de solutions sous le dossier **Sources de données partagées**.  
  
 Pour plus d’informations sur les différences entre les sources de données incorporées et partagées, consultez [Connexions de données ou sources de données incorporées et partagées &#40;Générateur de rapports et SSRS&#41;](../Topic/Embedded%20and%20Shared%20Data%20Connections%20or%20Data%20Sources%20\(Report%20Builder%20and%20SSRS\).md).  
  
 Pour plus d’informations sur la création d’une source de données partagée, consultez [Créer une source de données incorporée ou partagée &#40;SSRS&#41;](../Topic/Create%20an%20Embedded%20or%20Shared%20Data%20Source%20\(SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Concepteur de rapports  
  
#### Pour convertir une source de données incorporée en source partagée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données, puis cliquez sur **Convertir en source de données partagée**.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**. Si le volet s'ouvre comme une fenêtre flottante, vous pouvez l'ancrer. Pour plus d’informations, consultez [Ancrer le volet des données de rapport dans le Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/tools/dock-the-report-data-pane-in-report-designer-ssrs.md).  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée. Dans l’Explorateur de solutions, une source de données partagée avec le même nom s’affiche sous le dossier **Sources de données partagées**.  
  
### Pour convertir une source de données partagée en source incorporée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données, ouvrez la boîte de dialogue **Propriétés de la source de données**, puis cliquez sur **Connexion incorporée**. Entrez les informations nécessaires.  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée.  
  
## Générateur de rapports  
  
#### Pour convertir une source de données incorporée en source partagée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données pour ouvrir la boîte de dialogue **Propriétés de la source de données**, puis cliquez sur **Connexion incorporée**. Entrez les informations nécessaires.  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée.  
  
#### Pour convertir une source de données partagée en source incorporée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données, ouvrez la boîte de dialogue **Propriétés de la source de données**, puis cliquez sur **Connexion incorporée**. Entrez les informations nécessaires.  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée.  
  
## Voir aussi  
 [Gérer des sources de données de rapports](../../reporting-services/report-data/manage-report-data-sources.md)   
 [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  