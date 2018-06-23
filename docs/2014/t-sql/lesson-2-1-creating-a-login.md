---
title: Création d’une connexion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 33e3b3bcccfc88a3071a053de7154bf16d50265d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043501"
---
# <a name="creating-a-login"></a>Création d'une connexion
  Pour accéder au [!INCLUDE[ssDE](../includes/ssde-md.md)], les utilisateurs ont besoin d’une connexion. Cette connexion peut représenter l’identité de l’utilisateur sous forme d’un compte Windows ou d’un membre d’un groupe Windows, ou la connexion peut être une connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui existe uniquement dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Chaque fois que vous en avez la possibilité, utilisez l’authentification Windows.  
  
 Par défaut, les administrateurs de votre ordinateur ont un accès complet à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dans le cadre de cette leçon, l'utilisateur a moins de privilèges ; par conséquent, vous allez créer un nouveau compte d'authentification Windows local sur votre ordinateur. Pour ce faire, vous devez être administrateur de votre ordinateur. Puis vous allez octroyer à ce nouvel utilisateur l'accès à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="to-create-a-new-windows-account"></a>Pour créer un nouveau compte Windows  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, dans le **ouvrir** , tapez `%SystemRoot%\system32\compmgmt.msc /s`, puis cliquez sur **OK** pour ouvrir le programme de gestion de l’ordinateur.  
  
2.  Sous **Outils système**, développez **Utilisateurs et groupes locaux**, cliquez avec le bouton droit sur **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.  
  
3.  Dans la zone **Nom d’utilisateur** , tapez **Mary**.  
  
4.  Dans les zones **Mot de passe** et **Confirmer le mot de passe** , tapez un mot de passe fort, puis cliquez sur **Créer** pour créer un utilisateur Windows local.  
  
### <a name="to-create-a-login"></a>Pour créer une connexion  
  
1.  Dans une fenêtre de l'Éditeur de requête [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], tapez et exécutez le code suivant en remplaçant `computer_name` par le nom de votre ordinateur. `FROM WINDOWS` indique que Windows va authentifier l’utilisateur. L'argument `DEFAULT_DATABASE` facultatif connecte `Mary` à la base de données `TestData` , sauf si sa chaîne de connexion indique une autre base de données. Cette instruction introduit le point-virgule comme arrêt facultatif pour une instruction [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
     Cela autorise un nom d'utilisateur, `Mary`, authentifié par votre ordinateur, d'accéder à cette instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si votre ordinateur a plus d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez créer la connexion sur chaque instance à laquelle `Mary` doit accéder.  
  
    > [!NOTE]  
    >  Étant donné que `Mary` n'est pas un compte de domaine, ce nom d'utilisateur ne peut être authentifié que sur cet ordinateur.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Accorder l’accès à une base de données](lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [Choisir un mode d’authentification](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
