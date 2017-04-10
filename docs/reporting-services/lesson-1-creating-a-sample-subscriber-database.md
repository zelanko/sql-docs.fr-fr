---
title: "Le&#231;on&#160;1&#160;: Cr&#233;ation d&#39;un exemple de base de donn&#233;es de l&#39;abonn&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "05/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Le&#231;on&#160;1&#160;: Cr&#233;ation d&#39;un exemple de base de donn&#233;es de l&#39;abonn&#233;
Dans cette leçon de didacticiel [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)], vous allez créer une petite base de données d’« abonnés » pour stocker des données d’abonnement qui seront utilisées par un abonnement piloté par les données. Quand l’abonnement est traité, le serveur de rapports extrait ces données et les utilise pour personnaliser le résultat du rapport. Par exemple, les lignes de données incluent des numéros de commande spécifiques à utiliser pour les filtres, ainsi que le format de fichier des rapports générés.  
  
Cette leçon part du principe que vous utilisez [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)] pour créer une base de données [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
### Pour créer une base de données d'abonnés exemple  
  
1.  Démarrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et ouvrez une connexion à une instance du [!INCLUDE[ssDEnoversion_md](../includes/ssdenoversion-md.md)].  
  
2.  Cliquez avec le bouton droit sur Bases de données, puis sélectionnez **Nouvelle base de données**.  
  
3.  Dans la boîte de dialogue Nouvelle base de données, dans la zone **Nom de la base de données**, tapez *Abonnés*. 
4. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Cliquez sur le bouton **Nouvelle requête** dans la barre d’outils.  
  
6.  Copiez les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] suivantes dans la requête vide :  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
7.  Cliquez sur **! Exécuter** dans la barre d’outils.  
  
8.  Utilisez une instruction SELECT pour vérifier que votre table comporte bien trois lignes de données. Par exemple : `select * from OrderInfo`  
  
## Étapes suivantes  
+ Vous avez créé les données d'abonnement sur lesquelles seront basées la distribution des rapports et en fonction desquelles les résultats des rapports varieront pour chaque abonné. 
+ Ensuite, vous allez modifier les propriétés de la source de données du rapport pour utiliser des informations d’identification stockées. 
+ Vous allez également modifier la conception du rapport afin d'inclure un paramètre que l'abonnement utilisera avec les données d'abonné. [Leçon 2 : Modification des propriétés d’une source de données de rapport](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)  
  
## Voir aussi  
[Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
[Créer une base de données](../relational-databases/databases/create-a-database.md)  
[Créer un rapport de tableau de base &#40;didacticiel SSRS&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  
  
  
