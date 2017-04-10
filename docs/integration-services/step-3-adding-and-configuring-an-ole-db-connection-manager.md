---
title: "&#201;tape&#160;3&#160;: ajout et configuration d&#39;un gestionnaire de connexions OLE&#160;DB | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# &#201;tape&#160;3&#160;: ajout et configuration d&#39;un gestionnaire de connexions OLE&#160;DB
La tâche qui suit l'ajout du Gestionnaire de connexions de fichiers plats pour la connexion à la source de données, consiste à ajouter un Gestionnaire de connexions OLE DB pour la connexion à la destination. Un Gestionnaire de connexions OLE DB permet à un package d’extraire ou de charger des données dans une source de données compatible OLE DB. Au moyen du Gestionnaire de connexions OLE DB, vous pouvez spécifier le serveur, la méthode d'authentification et la base de données par défaut pour la connexion.  
  
Au cours de cette leçon, vous allez créer un Gestionnaire de connexions OLE DB qui utilise l’authentification Windows pour la connexion à l’instance locale de **AdventureWorksDB2012**. Le Gestionnaire de connexions OLE DB que vous créez sera également référencé par d'autres composants que vous créerez ultérieurement au cours de ce didacticiel, tels que la transformation de recherche et la destination OLE DB.  
  
### Ajouter et configurer un Gestionnaire de connexions OLE DB au package SSIS  
  
1.  Cliquez avec le bouton droit dans la zone **Gestionnaires de connexions** et choisissez **Nouvelle connexion OLE DB**.  
  
2.  Dans la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**, cliquez sur **Nouveau**.  
  
3.  Dans la zone **Nom du serveur**, entrez **localhost**.  
  
    Lorsque vous spécifiez « localhost » comme nom de serveur, le gestionnaire de connexions se connecte à l'instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l'ordinateur local. Pour utiliser une instance distante de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], remplacez « localhost » par le nom du serveur auquel vous souhaitez établir la connexion.  
  
4.  Dans le groupe **Connexion au serveur**, vérifiez que l’option **Utiliser l’authentification Windows** est sélectionnée.  
  
5.  Dans le groupe **Se connecter à une base de données**, dans la zone **Sélectionner ou entrer un nom de base de données**, tapez ou sélectionnez **AdventureWorksDW2012**.  
  
6.  Cliquez sur **Tester la connexion** pour vérifier si les paramètres de connexion que vous avez spécifiés sont valides.  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez sur **OK**.  
  
9. Dans le volet **Connexions de données** de la boîte de dialogue **Configurer le Gestionnaire de connexions OLE DB**, vérifiez que **localhost.AdventureWorksDW2012** est sélectionné.  
  
10. Cliquez sur **OK**.  
  
## Tâche suivante de la leçon  
[Étape 4 : ajout d'une tâche de flux de données au package](../integration-services/step-4-adding-a-data-flow-task-to-the-package.md)  
  
## Voir aussi  
[Gestionnaire de connexions OLE DB](../integration-services/connection-manager/ole-db-connection-manager.md)  
  
