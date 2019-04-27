---
title: Créer la base de données de modifications SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 72785cffa01da7bf00248d442b1d3ce4103c45a8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771365"
---
# <a name="create-the-sql-server-change-database"></a>Créer la base de données de modification SQL Server
  Lorsque vous démarrez l'Assistant Nouvelle instance, la page Créer une base de données CDC s'ouvre. Cette page permet de fournir des informations sur la nouvelle instance de capture de données modifiées et de créer une nouvelle base de données de modification.  
  
 Lorsque vous créez une base de données CDC, elle est activée pour SQL Server CDC et cette activation requiert une connexion membre du rôle serveur fixe `sysadmin` .  
  
 Lorsqu'un utilisateur qui démarre l'Assistant Création d'une instance Oracle CDC n'est pas membre du rôle serveur fixe `sysadmin` , la boîte de dialogue Connexion à SQL Server s'ouvre et vous invite à entrer les informations d'identification pour un membre du rôle sysadmin de façon à effectuer la tâche Activer la base de données pour SQL Server CDC. Lorsque la base de données CDC est créée, la connexion `sysadmin` est ignorée et la tâche reprend avec la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'origine utilisée lorsque la console du concepteur Oracle a été ouverte.  
  
> [!IMPORTANT]  
>  Pour les tâches autres que l’activation de la base de données pour SQL Server CDC, la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour exécuter l’Assistant Nouvelle instance doit disposer du rôle serveur fixe `dbcreator` et des autorisations UPDATE sur la base de données MSXDBCDC.  
  
 Pour plus d'informations sur la saisie de données dans la boîte de dialogue Connexion à SQL Server, consultez [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).  
  
## <a name="options"></a>Options  
 **Instance Oracle CDC**  
 Entrez les informations suivantes sur l'instance CDC que vous créez.  
  
-   **Nom**: nom du nouveau service. Ce sera également le nom de la nouvelle base de données modifiée.  
  
-   **Description** : description de la nouvelle instance permettant de l’identifier plus facilement. Ce paramètre est facultatif.  
  
 **Base de données modifiée SQL Server**  
 Cette section est utilisée pour créer la base de données.  
  
1.  **Modifier la base de données** : nom de la nouvelle base de données modifiée. Le nom de la base de données est identique au nom donné à l'instance. Ce champ en lecture seule affiche le chemin d'accès complet à la base de données.  
  
2.  **Créer une base de données** : cliquez sur **Créer une base de données** pour créer la base de données.  
  
     Pour créer la base de données, la connexion doit posséder le rôle serveur `sysasmin` . Pour plus d'informations, consultez la remarque sur la sécurité ci-dessus.  
  
     Après avoir créé la base de données, vous pouvez cliquer sur **Suivant** pour [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](how-to-create-the-sql-server-change-database-instance.md)   
 [Service de capture de données modifiées Oracle](the-oracle-cdc-service.md)  
  
  
