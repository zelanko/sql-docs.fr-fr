---
title: "Connexion à l’aide de l’Éditeur de requête | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5a822268755f46da6775150119b6c7fd771838c8
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="lesson-2-1---connecting-with-query-editor"></a>Leçon 2-1 - Connexion à l’aide de l’Éditeur de requête
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] permet d’écrire du code ou de le modifier tout en étant déconnecté du serveur. Cela peut s'avérer utile lorsque le serveur n'est pas disponible ou lorsque vous souhaitez limiter l'utilisation du serveur ou conserver les ressources réseau. Vous pouvez également modifier la connexion de l'Éditeur de requête pour choisir une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans ouvrir une nouvelle fenêtre de l'Éditeur de requête ou sans retaper du code.  
  
## <a name="coding-offline"></a>Codage hors ligne  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a>Pour écrire du code hors ligne puis se connecter à différents serveurs  
  
1.  Dans la barre d'outils [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , cliquez sur **Requête de moteur de base de données** pour ouvrir l'Éditeur de requête.  
  
2.  Dans la boîte de dialogue **Se connecter au moteur de base de données** , cliquez sur **Annuler**. L'Éditeur de requête s'ouvre et sa barre de titre indique que vous n'êtes pas connecté à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Dans le volet du code, tapez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes :  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
    À ce stade, vous pouvez vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cliquant sur **Se connecter**, **Exécuter**, **Analyser**ou **Afficher le plan d’exécution estimé**. Toutes ces options sont disponibles à partir du menu **Requête** , de la barre d’outils de l’Éditeur de requête, ou du menu contextuel qui s’affiche quand vous cliquez avec le bouton droit dans la fenêtre de l’Éditeur de requête. Pour cet exercice, vous allez utiliser la barre d'outils.  
  
4.  Dans la barre d'outils, cliquez sur le bouton **Exécuter** pour ouvrir la boîte de dialogue **Se connecter au moteur de base de données** .  
  
5.  Dans la zone **Nom du serveur** , tapez le nom de votre serveur, puis cliquez sur **Options**.  
  
6.  Dans la liste **Connexion à une base de données** de l'onglet **Propriétés de connexion** , parcourez le contenu du serveur pour sélectionner [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , puis cliquez sur **Se connecter**.  
  
7.  Pour ouvrir une autre fenêtre de l'Éditeur de requête avec la même connexion, dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
8.  Pour changer les connexions, cliquez avec le bouton droit dans la fenêtre de l’Éditeur de requête, pointez sur **Connexion**, puis cliquez sur **Modifier la connexion**.  
  
9. Dans la boîte de dialogue **Connexion à SQL Server** , sélectionnez une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'il en existe une disponible, puis cliquez sur **Se connecter**.  
  
Cette nouvelle fonctionnalité de l'Éditeur de requête permet d'exécuter facilement le même code sur plusieurs serveurs. Cela peut s'avérer utile pour les actions de maintenance impliquant l'utilisation de serveurs similaires.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Ajout d'une mise en retrait](../../tools/sql-server-management-studio/lesson-2-2-adding-indentation.md)  
  
  
  
