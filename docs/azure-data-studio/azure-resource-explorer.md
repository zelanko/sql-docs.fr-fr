---
title: Explorez les ressources de SQL Azure avec Azure Resource Explorer
titleSuffix: Azure Data Studio
description: Découvrez comment Explorer et gérer le serveur SQL Azure, Azure SQL Database et Azure SQL Managed Instance via Azure Resource Explorer.
ms.custom: seodec18
author: yanancai
ms.author: yanacai
manager: jroth
ms.date: 09/24/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: azure-data-studio
ms.openlocfilehash: 91e766fae5dca7a3d9e2dec56af17161d684e145
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66789222"
---
# <a name="explore-and-manage-azure-sql-resources-with-azure-resource-explorer"></a>Explorer et gérer les ressources de SQL Azure avec Azure Resource Explorer

Dans ce document, vous découvrez comment vous pouvez Explorer et gérer Azure SQL Server, base de données SQL Azure et les ressources Azure SQL Managed Instance via Azure Resource Explorer dans [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

>[!NOTE]
>L’Explorateur de ressources Azure prendra en charge dans la version préliminaire de SQL Server 2019 en octobre. Après cela, vous pouvez installer l’extension de la version préliminaire via [Gestionnaire d’extensions](extensions.md) ou via **fichier** > **installer le Package à partir du Package VSIX**.


## <a name="connect-to-azure"></a>Se connecter à Azure

Après avoir installé le plug-in de la version préliminaire SQL, une icône Azure apparaît dans la barre de menu de gauche. Cliquez sur l’icône pour ouvrir l’Explorateur de ressources Azure. Si vous ne voyez pas l’icône Windows Azure, cliquez avec le bouton droit sur la barre de menu de gauche, puis sélectionnez **Azure Resource Explorer**.

### <a name="add-an-azure-account"></a>Ajouter un compte Azure

Pour afficher les ressources SQL associés à un compte Azure, vous devez d’abord ajouter le compte à [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)].

1. Ouvrez **comptes liés** boîte de dialogue via l’icône de gestion de compte sur le coin inférieur gauche, ou via **connectez-vous à Azure...**  lien dans l’Explorateur de ressources Azure.

    ![Connectez-vous à Azure](media/azure-resource-explorer/sign-in-to-azure.png)

2. Dans le **comptes liés** boîte de dialogue, cliquez sur **ajouter un compte**.

    ![Ajouter un compte Azure](media/azure-resource-explorer/add-an-azure-account.png)

3. Cliquez sur **copier et ouvrir** pour ouvrir le navigateur pour l’authentification.

    ![Page d’authentification ouverte dans le navigateur](media/azure-resource-explorer/open-authentication-in-browser.png)

4. Coller le **code utilisateur** dans la page web et cliquez sur **continuer** pour s’authentifier.

    ![S’authentifier dans le navigateur](media/azure-resource-explorer/authenticate-in-browser.png)

5. Dans [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)] vous trouverez maintenant connecté dans un compte Azure dans **comptes liés** boîte de dialogue.

    ![Azure compte de connexion](media/azure-resource-explorer/signed-in-azure-account.png)

### <a name="add-more-azure-accounts"></a>Ajouter des comptes Azure

Plusieurs comptes Azure sont pris en charge dans [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]. Pour ajouter des comptes Azure, cliquez sur le bouton dans le coin supérieur droit de **comptes liés** boîte de dialogue et suivez la même procédure avec ajoutent une section du compte Azure pour ajouter des comptes Azure.

![Ajouter le compte Azure](media/azure-resource-explorer/add-more-azure-account.png)

### <a name="remove-an-azure-account"></a>Supprimer un compte Azure

Pour supprimer un compte Azure connecté existant :

1. Ouvrez **comptes liés** boîte de dialogue via l’icône de gestion de compte sur le coin inférieur gauche.
2. Cliquez sur le **X** situé à droite du compte Azure pour le supprimer.

    ![Supprimer le compte Azure](media/azure-resource-explorer/remove-azure-account.png)

## <a name="filter-subscription"></a>Abonnement de filtre

Une fois connecté à un compte Azure, tous les abonnements associés qui compte Azure s’affichent dans l’Explorateur de ressources Azure. Vous pouvez filtrer les abonnements pour chaque compte Azure.

1. Cliquez sur le **Select Subscription** bouton situé à droite du compte Azure.

   ![Abonnement de filtre](media/azure-resource-explorer/filter-subscription.png)

2. Sélectionnez les cases à cocher pour les abonnements de compte que vous souhaitez parcourir, puis cliquez sur **OK**.

   ![Sélectionner un abonnement](media/azure-resource-explorer/select-subscription.png)

## <a name="explore-azure-sql-resources"></a>Explorez les ressources de SQL Azure

Pour accéder à une ressource de SQL Azure dans Azure Resource Explorer, développez le groupe de types de ressources et comptes Azure.

Explorateur de ressources Azure Azure SQL Server, base de données SQL Azure et Azure SQL Managed Instance prend actuellement en charge.

## <a name="connect-to-azure-sql-resources"></a>Se connecter aux ressources de SQL Azure

Explorateur de ressources Azure fournissent un accès rapide qui vous permet de se connecter aux serveurs SQL et les bases de données pour la gestion et de la requête. 

1. Explorez la ressource SQL que vous souhaitez vous connecter dans l’arborescence.
2. Cliquez avec le bouton droit sur la ressource et sélectionnez **Connect**, vous pouvez également trouver le bouton se connecter à droite de la ressource.

   ![Se connecter à des ressources de SQL Azure](media/azure-resource-explorer/connect-to-azure-sql-resource.png)

3. Dans la liste ouverte **connexion** boîte de dialogue, entrez votre mot de passe et cliquez sur **Connect**.

   ![Boîte de dialogue de connexion SQL](media/azure-resource-explorer/sql-connection-dialog.png)
4. Le **serveurs** fenêtre s’ouvre automatiquement avec le nouveau SQL server/base de données connectée à l’issue de connexion.

## <a name="next-steps"></a>Étapes suivantes

- [Utilisez [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] pour vous connecter et interroger la base de données SQL Azure](quickstart-sql-database.md)
- [Utilisez [!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)] pour vous connecter et interroger des données dans Azure SQL Data Warehouse](quickstart-sql-dw.md)