---
title: Octroi de l’accès à une base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 12e678b8cd5210ba6db0cd326c0cd803ed210735
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63460048"
---
# <a name="granting-access-to-a-database"></a>Octroi de l'accès à une base de données
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
 [Création des vues et des procédures stockées](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
