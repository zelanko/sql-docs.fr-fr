---
title: "Accorder l’accès à une base de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 30de5de3d238905802e80d433c2df7deaf058929
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Leçon 2-2-accorder l’accès à une base de données
Mary a désormais accès à cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais elle n'est pas autorisée à accéder aux bases de données. Elle ne peut pas non plus accéder à sa base de données par défaut **TestData** tant que vous ne l'avez pas autorisée en tant qu'utilisateur de base de données.  
  
Pour octroyer l'accès à Mary, basculez vers la base de données **TestData** , et à l'aide de l'instruction CREATE USER mappez sa connexion à un utilisateur appelée Marie.  
  
### <a name="to-create-a-user-in-a-database"></a>Pour créer un utilisateur dans une base de données  
  
1.  Tapez et exécutez les instructions suivantes ( `computer_name` est remplacé par le nom de votre ordinateur) pour octroyer à `Mary` l'accès à la base de données `TestData` .  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    Mary a désormais accès à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et à la base de données `TestData` .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Création des vues et des procédures stockées](../t-sql/lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
  

