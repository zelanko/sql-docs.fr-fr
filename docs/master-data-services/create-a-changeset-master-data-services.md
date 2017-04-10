---
title: "Cr&#233;er un ensemble de modifications (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Cr&#233;er un ensemble de modifications (Master Data Services)
  Un ensemble de modifications regroupe des modifications en attente, qui portent sur les données de référence. Si l’entité requiert l’approbation des modifications, les modifications en attente doivent être enregistrées dans un ensemble de modifications, puis soumises à l’administrateur à des fins d’approbation.  
  
## Conditions préalables  
  
-   Vous devez être autorisé à accéder à la zone fonctionnelle Explorateur. Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Vous devez disposer au minimum d’un accès en lecture à l’entité ou à l’un de ses attributs.  
  
## Pour créer un ensemble de modifications local  
  
1.  Sur la page d’accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , sélectionnez le modèle et la version, puis cliquez sur **Explorateur**.  
  
2.  Dans le menu **Entités** , cliquez sur une entité.  
  
3.  Dans le volet de droite, sélectionnez **Ensembles de modifications** et cliquez sur **Créer**.  
  
4.  Donnez un nom au fichier, puis cliquez sur **Enregistrer**.  
  
     Le nom de l’ensemble de modifications doit être unique au sein d’un modèle.  
  
## Pour créer un ensemble de modifications pour approbation  
  
1.  Sur la page d’accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , sélectionnez le modèle et la version, puis cliquez sur **Explorateur**.  
  
2.  Dans le menu **Entités** , cliquez sur une entité.  
  
3.  Apportez des modifications à l’entité, puis cliquez sur **OK**.  
  
4.  **Choisir un ensemble de modifications** s’affiche.  
  
5.  Cliquez sur **Nouveau**, donnez un nom à l’ensemble de modifications et cliquez sur **Enregistrer**. Le nom de l’ensemble de modifications doit être unique dans le modèle.  
  
6.  Pour utiliser un ensemble de modifications existant, cliquez sur **Existant** et choisissez l’ensemble de modifications dans la liste. Seuls les ensembles de modifications qui se trouvent à l’état ouvert ou rejeté sont disponibles.  
  
## Étapes suivantes  
 [Appliquer et mettre à jour un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## Voir aussi  
 [Valider ou envoyer un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Approuver ou rejeter un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  