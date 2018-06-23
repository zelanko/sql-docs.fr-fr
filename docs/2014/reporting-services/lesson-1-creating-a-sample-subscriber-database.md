---
title: 'Leçon 1 : création d’un exemple de base de données de l’abonné | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: c1b01246166c6d7e75f1083fc23b9bd15502c731
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041548"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a>Leçon 1 : Création d'un exemple de base de données de l'abonné
  Avant de pouvoir définir un abonnement piloté par les données, vous devez disposer d'une source de données qui fournit les données d'abonnement. Au cours de cette étape, vous allez créer une petite base de données pour y stocker les données d'abonnement qui seront utilisées dans ce didacticiel. Ensuite, une fois l'abonnement traité, le serveur de rapports extrait ces données et les utilise pour personnaliser le résultat du rapport, les options de remise et le format de présentation du rapport.  
  
 Cette leçon suppose que vous utilisez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour créer un [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] base de données.  
  
### <a name="to-create-a-sample-subscriber-database"></a>Pour créer une base de données d'abonnés exemple  
  
1.  Démarrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], puis ouvrez une connexion à un [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Cliquez avec le bouton droit sur Bases de données, puis sélectionnez **Nouvelle base de données**.  
  
3.  Dans la boîte de dialogue Nouvelle base de données, dans le nom de la base de données, tapez *abonnés*. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  Cliquez sur le bouton **Nouvelle requête** dans la barre d’outils.  
  
5.  Copiez les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] suivantes dans la requête vide :  
  
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
  
6.  Cliquez sur  **Exécuter** dans la barre d’outils.  
  
7.  Utilisez une instruction SELECT pour vérifier que votre table comporte bien trois lignes de données. Par exemple : `select * from OrderInfo`  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé les données d'abonnement sur lesquelles seront basées la distribution des rapports et en fonction desquelles les résultats des rapports varieront pour chaque abonné. Ensuite, vous allez modifier les propriétés de la source de données du rapport que vous distribuerez aux abonnés. La modification des propriétés de la source de données est destinée à préparer le rapport pour la remise de l'abonnement piloté par les données. Vous allez également modifier la conception du rapport afin d'inclure un paramètre que l'abonnement utilisera avec les données d'abonné. [Leçon 2 : Modification des propriétés d’une source de données de rapport](lesson-2-modifying-the-report-data-source-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Créer une base de données](../relational-databases/databases/create-a-database.md)   
 [Créer un rapport de tableau de base &#40;Didacticiel SSRS&#41;](create-a-basic-table-report-ssrs-tutorial.md)  
  
  