---
title: 'Tutoriel : Configurer des autorisations sur des objets db'
ms.custom: seo-lt-2019
ms.date: 07/31/2018
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 991bdef702b1ed298bb492172ef65c6d25d5d0ab
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75244748"
---
# <a name="lesson-2-configure-permissions-on-database-objects"></a>Leçon 2 : Configurer des autorisations sur des objets de base de données
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
L'octroi à un utilisateur de l'accès à une base de données implique trois étapes. Commencez par créer une connexion. La connexion permet à l’utilisateur de se connecter au [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]. Puis, configurez la connexion en tant qu'utilisateur dans la base de données spécifiée. Enfin, accordez à cet utilisateur l'autorisation sur les objets de base de données. Cette leçon illustre ces trois étapes et vous montre comment créer une vue et une procédure stockée comme objet.  

  >[!NOTE]
  > Cette leçon repose sur les objets créés dans [Leçon 1 - Créer des objets de base de données](lesson-1-creating-database-objects.md). Suivez la leçon 1 avant de passer à la leçon 2. 

## <a name="prerequisites"></a>Conditions préalables requises
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio et d’un accès à une instance SQL Server. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Si vous n’avez pas accès à une instance SQL Server, sélectionnez votre plateforme parmi les liens suivants. Si vous choisissez l’authentification SQL, utilisez vos informations d’identification de connexion SQL Server.
- **Windows** : [Télécharger SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- **macOS** : [Télécharger SQL Server 2017 sur Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="create-a-login"></a>Créer un compte de connexion
Pour accéder au [!INCLUDE[ssDE](../includes/ssde-md.md)], les utilisateurs ont besoin d’une connexion. Cette connexion peut représenter l’identité de l’utilisateur sous forme d’un compte Windows ou d’un membre d’un groupe Windows, ou la connexion peut être une connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui existe uniquement dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Chaque fois que vous en avez la possibilité, utilisez l’authentification Windows.  
  
Par défaut, les administrateurs de votre ordinateur ont un accès complet à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dans le cadre de cette leçon, l'utilisateur a moins de privilèges ; par conséquent, vous allez créer un nouveau compte d'authentification Windows local sur votre ordinateur. Pour ce faire, vous devez être administrateur de votre ordinateur. Puis vous allez octroyer à ce nouvel utilisateur l'accès à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="create-a-new-windows-account"></a>Créer un nouveau compte Windows  
  
1.  Cliquez sur **Démarrer**, sur **Exécuter**, dans la zone **Ouvrir** , tapez **%SystemRoot%\system32\compmgmt.msc /s**, puis cliquez sur **OK** pour ouvrir le programme de gestion de l’ordinateur. 
2.  Sous **Outils système**, développez **Utilisateurs et groupes locaux**, cliquez avec le bouton droit sur **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.    
3.  Dans la zone **Nom d’utilisateur** , tapez **Mary**.    
4.  Dans les zones **Mot de passe** et **Confirmer le mot de passe** , tapez un mot de passe fort, puis cliquez sur **Créer** pour créer un utilisateur Windows local.  
  
### <a name="create-a-sql-login"></a>Créer un compte de connexion SQL  

Dans une fenêtre de l'Éditeur de requête [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], tapez et exécutez le code suivant en remplaçant `computer_name` par le nom de votre ordinateur. `FROM WINDOWS` indique que Windows va authentifier l’utilisateur. L'argument `DEFAULT_DATABASE` facultatif connecte `Mary` à la base de données `TestData` , sauf si sa chaîne de connexion indique une autre base de données. Cette instruction introduit le point-virgule comme arrêt facultatif pour une instruction [!INCLUDE[tsql](../includes/tsql-md.md)] .
  
  ```sql  
  CREATE LOGIN [computer_name\Mary]  
      FROM WINDOWS  
      WITH DEFAULT_DATABASE = [TestData];  
  GO  
  ```  
  
  Cela autorise un nom d'utilisateur, `Mary`, authentifié par votre ordinateur, d'accéder à cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si votre ordinateur a plus d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez créer la connexion sur chaque instance à laquelle `Mary` doit accéder.    
  > [!NOTE]  
  > Étant donné que `Mary` n'est pas un compte de domaine, ce nom d'utilisateur ne peut être authentifié que sur cet ordinateur. 


## <a name="grant-access-to-a-database"></a>Accorder l’accès à une base de données
Mary a désormais accès à cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais elle n'est pas autorisée à accéder aux bases de données. Elle ne peut pas non plus accéder à sa base de données par défaut **TestData** tant que vous ne l'avez pas autorisée en tant qu'utilisateur de base de données.  
  
Pour octroyer l'accès à Mary, basculez vers la base de données **TestData** , et à l'aide de l'instruction CREATE USER mappez sa connexion à un utilisateur appelée Marie.  
  
### <a name="to-create-a-user-in-a-database"></a>Pour créer un utilisateur dans une base de données  
  
Tapez et exécutez les instructions suivantes ( `computer_name` est remplacé par le nom de votre ordinateur) pour octroyer à `Mary` l'accès à la base de données `TestData` .
  
 ```sql  
 USE [TestData];  
 GO  
 
 CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
 GO    
 ```  
  
 Mary a désormais accès à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et à la base de données `TestData` .  


## <a name="create-views-and-stored-procedures"></a>Créer des vues et des procédures stockées
En tant qu’administrateur, vous pouvez exécuter l’instruction SELECT dans la table **Products** et la vue **vw_Names** , et exécuter la procédure **pr_Names** . Toutefois, Mary ne peut pas le faire. Pour lui octroyer les autorisations nécessaires, utilisez l'instruction GRANT.  

### <a name="grant-permission-to-stored-procedure"></a>Accorder une autorisation à la procédure stockée  
Exécutez l'instruction suivante pour donner à `Mary` l'autorisation `EXECUTE` pour la procédure stockée `pr_Names` .
  
  ```sql  
  GRANT EXECUTE ON pr_Names TO Mary;  
  GO  
  ```  
  
Dans ce scénario, Mary peut accéder uniquement à la table **Products** à l'aide de la procédure stockée. Pour que Mary puisse exécuter une instruction SELECT sur la vue, vous devez exécuter aussi `GRANT SELECT ON vw_Names TO Mary`. Pour supprimer l'accès aux objets de base de données, utilisez l'instruction REVOKE.  
  
> [!NOTE]  
> Si la table, la vue et la procédure stockée n'appartiennent pas au même schéma, l'octroi des autorisations devient plus complexe.  
  
### <a name="about-grant"></a>À propos de GRANT  
Vous devez avoir l'autorisation EXECUTE pour exécuter une procédure stockée. Vous devez avoir les autorisations SELECT, INSERT, UPDATE, et DELETE pour accéder et modifier des données. L'instruction GRANT sert également à d'autres autorisations, telles que les autorisations de créer des tables.  
  
## <a name="next-steps"></a>Étapes suivantes
L’article suivant vous apprend à supprimer des objets de base de données que vous avez créés dans les autres leçons. 

Passez à l’article suivant pour en savoir plus :
> [!div class="nextstepaction"]
>[Étapes suivantes](lesson-3-deleting-database-objects.md)
  
