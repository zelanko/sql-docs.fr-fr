---
title: "Octroi de l&#39;acc&#232;s &#224; une base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "accès à la base de données"
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Octroi de l&#39;acc&#232;s &#224; une base de donn&#233;es
Mary a désormais accès à cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais elle n'est pas autorisée à accéder aux bases de données. Elle ne peut pas non plus accéder à sa base de données par défaut **TestData** tant que vous ne l'avez pas autorisée en tant qu'utilisateur de base de données.  
  
Pour octroyer l'accès à Mary, basculez vers la base de données **TestData** , et à l'aide de l'instruction CREATE USER mappez sa connexion à un utilisateur appelée Marie.  
  
### Pour créer un utilisateur dans une base de données  
  
1.  Tapez et exécutez les instructions suivantes (`computer_name` est remplacé par le nom de votre ordinateur) pour octroyer à`Mary` l'accès à la base de données `TestData`.  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    Mary a désormais accès à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et à la base de données `TestData` .  
  
## Tâche suivante de la leçon  
[Création des vues et des procédures stockées](../t-sql/creating-views-and-stored-procedures.md)  
  
  
  
