---
title: "Ajouter SQLRUserGroup en tant qu’un utilisateur de base de données | Documents Microsoft"
ms.custom: 
ms.date: 11/13/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- authentification implicite
- SQLRUserGroup
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 97a571a9a91ac31e955f6833e27a975f87267218
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>Ajouter SQLRUserGroup en tant qu’un utilisateur de base de données

Lors de l’installation de [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] ou [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)], nouveaux comptes d’utilisateur Windows sont créés pour l’exécution de tâches sous le jeton de sécurité de le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service. Lorsqu’un utilisateur envoie un script à partir d’un client externe, d’apprentissage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active un compte de travail disponible, il est mappé à l’identité de l’utilisateur appelant et exécute le script de la part de l’utilisateur. Ce nouveau service du moteur de base de données prend en charge l’exécution sécurisée de scripts externes, appelé *l’authentification implicite*.

Vous pouvez afficher ces comptes dans le groupe d’utilisateurs Windows **SQLRUserGroup**. Par défaut, 20 comptes de travail sont créés, qui est généralement plus que suffisant pour R en cours d’exécution des travaux.

Toutefois, si vous avez besoin d’exécuter des scripts R à partir d’un client de science des données distantes et utilisez l’authentification Windows, vous devez accorder ces comptes de travailleur autorisé à se connecter à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à votre place.

## <a name="add-sqlrusergroup-as-a-sql-server-login"></a>Ajouter des SQLRUserGroup en tant qu’une connexion SQL Server

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.

2. Dans le **nouvelle connexion** boîte de dialogue, sélectionnez **recherche**. (Ne tapez pas quoi que ce soit dans la zone encore.)
    
     ![Cliquez sur Rechercher pour ajouter le nouveau compte de connexion pour l’apprentissage](media/implied-auth-login1.png "cliquez sur Rechercher pour ajouter le nouveau compte de connexion pour l’apprentissage")

3. Dans le **sélectionner utilisateur ou groupe** , cliquez sur le **Types d’objet** bouton.

     ![Rechercher des types d’objets pour ajouter le nouveau compte de connexion pour l’apprentissage](media/implied-auth-login2.png "recherche les types d’objets pour ajouter le nouveau compte de connexion pour l’apprentissage")

4. Dans le **les Types d’objets** boîte de dialogue, sélectionnez **groupes**. Désactivez toutes les autres cases à cocher.

     ![Sélectionnez les groupes dans la boîte de dialogue Types d’objet](media/implied-auth-login3.png "sélectionner des groupes dans la boîte de dialogue Types d’objet")

4. Cliquez sur **avancé**, vérifiez que l’emplacement de recherche est l’ordinateur actuel et puis cliquez sur **Rechercher maintenant**.

     ![Cliquez sur Rechercher maintenant pour obtenir la liste des groupes](media/implied-auth-login4.png "cliquez sur Rechercher pour obtenir la liste des groupes")

5. Faites défiler la liste des comptes de groupe sur le serveur jusqu'à ce que vous trouviez une commençant par `SQLRUserGroup`.
    
    + Le nom du groupe associé avec le service Launchpad pour le _instance par défaut_ est toujours simplement **SQLRUserGroup**. Sélectionner ce compte uniquement pour l’instance par défaut.
    + Si vous utilisez un _instance nommée_, le nom d’instance est ajouté au nom par défaut `SQLRUserGroup`. Par conséquent, si votre instance est nommée « MLTEST », le nom du groupe utilisateur par défaut pour cette instance serait **SQLRUserGroupMLTest**.
 
     ![Exemple de groupes sur le serveur](media/implied-auth-login5.png "exemple de groupes sur le serveur")
   
5. Cliquez sur **OK** pour fermer la boîte de dialogue Recherche avancée.

    > [!IMPORTANT]
    > Veillez à ce que vous avez sélectionné le compte approprié pour l’instance. Chaque instance peut utiliser uniquement son propre service Launchpad et le groupe créé pour ce service. Les instances ne peuvent pas partager un compte de service ou de travail Launchpad.

6. Cliquez sur **OK** pour fermer la **sélectionner utilisateur ou groupe** boîte de dialogue.

7. Dans le **nouvelle connexion** boîte de dialogue, cliquez sur **OK**. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données.

## <a name="change-the-number-of-worker-accounts-in-sqlrusergroup"></a>Modifier le nombre de comptes de travail dans SQLRUserGroup

Si vous avez l’intention de faire un usage intensif de l’apprentissage, vous pouvez augmenter le nombre de comptes utilisés pour exécuter des scripts externes, comme décrit dans cet article : 

+ [Modifier le pool de comptes d’utilisateur pour l’apprentissage](modify-the-user-account-pool-for-sql-server-r-services.md)

Par défaut, 20 comptes sont créés, qui prend en charge 20 sessions simultanées. Tâches parallélisées n’utilisent pas des comptes supplémentaires. Par exemple, si un utilisateur exécute une tâche de calcul de score qui utilise le traitement parallèle, le même compte de processus de travail est réutilisé pour tous les threads.