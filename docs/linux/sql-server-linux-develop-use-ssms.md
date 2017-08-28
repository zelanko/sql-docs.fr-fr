---
title: "Gérer SQL Server sur Linux avec SSMS | Documents Microsoft"
description: "Ce didacticiel montre comment utiliser SQL Server Management Studio sur Windows pour se connecter à SQL Server en cours d’exécution sur Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 30cc4564-f389-4707-9b25-8ba782cc5150
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: a999ca0248e83d2d9ef59f7ec04ad2dd58378132
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="use-sql-server-management-studio-ssms-on-windows-to-manage-sql-server-on-linux"></a>Utilisez SQL Server Management Studio (SSMS) sur Windows pour gérer SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique montre comment utiliser [SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx) pour se connecter à SQL Server 2017 RC2 sur Linux. SSMS est une application Windows, par conséquent, utilisez SSMS lorsque vous disposez d’un ordinateur Windows qui peut se connecter à une instance distante de SQL Server sur Linux. 

Après vous être connecté, vous exécutez une requête Transact-SQL (T-SQL) simple pour vérifier la communication avec la base de données.

## <a name="install-the-newest-version-of-sql-server-management-studio"></a>Installez la dernière version de SQL Server Management Studio

Lorsque vous travaillez avec SQL Server, vous devez toujours utiliser la dernière version de SQL Server Management Studio (SSMS). La dernière version de SSMS est continuellement mis à jour et optimisées et est actuellement compatible avec SQL Server 2017 Linux on. Pour télécharger et installer la version la plus récente, consultez [télécharger SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx). Pour rester à jour, la dernière version de SSMS vous invite lorsqu’il existe une nouvelle version disponible en téléchargement. 

## <a name="connect-to-sql-server-on-linux"></a>Se connecter à SQL Server sur Linux

Les étapes suivantes montrent comment se connecter à 2017 du serveur SQL sur Linux avec SSMS.

1. Lancez SSMS en tapant **Microsoft SQL Server Management Studio** dans les fenêtres de zone de recherche, puis cliquez sur l’application de bureau.

    ![SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png)

2. Dans le **se connecter au serveur** fenêtre, entrez les informations suivantes (si SSMS est déjà en cours d’exécution, cliquez sur **Connect > moteur de base de données** pour ouvrir le **se connecter au serveur** fenêtre) :

   | Paramètre |  Description |
   |-----|-----|
   | **Type de serveur** | La valeur par défaut est le moteur de base de données ; ne modifiez pas cette valeur. |
   | **Nom du serveur** | Entrez le nom de l’ordinateur Linux SQL Server cible ou son adresse IP. |
   | **Authentification** | Pour SQL Server les 2017 sur Linux, utilisez **l’authentification SQL Server**. |
   | **Connexion** | Entrez le nom d’un utilisateur ayant accès à une base de données sur le serveur (par exemple, la valeur par défaut **SA** compte créé pendant l’installation). |
   | **Mot de passe** | Entrez le mot de passe pour l’utilisateur spécifié (pour le **SA** compte, vous avez créé cette pendant l’installation). |

    ![SQL Server Management Studio : Se connecter au serveur de base de données SQL](./media/sql-server-linux-develop-use-ssms/connect.png)

3. Cliquez sur **Se connecter**.

    > [!TIP]
    > Si un échec de connexion s’affiche, tentez tout d’abord de diagnostiquer le problème à partir du message d’erreur. Examinez ensuite les [recommandations en matière de résolution des problèmes de connexion](sql-server-linux-troubleshooting-guide.md#connection).
 
5. Après vous être connecté à votre serveur SQL, **l’Explorateur d’objets** s’ouvre et vous pouvez désormais accéder à votre base de données pour effectuer des tâches administratives ou interroger des données.
 
     ![Explorateur d’objets](./media/sql-server-linux-develop-use-ssms/object-explorer.png)
     
## <a name="run-sample-queries"></a>Exécuter les exemples de requêtes

Une fois que vous vous connectez à votre serveur, vous pouvez vous connecter à une base de données et exécuter un exemple de requête. Si vous ne connaissez pas l’écriture de requêtes, consultez [l’écriture des instructions Transact-SQL](https://msdn.microsoft.com/library/ms365303.aspx).

1. Identifier une base de données à utiliser pour exécuter une requête. Cela peut être une nouvelle base de données que vous avez créé dans le [didacticiel de Transact-SQL](https://msdn.microsoft.com/library/ms365303.aspx). Ou il peut s’agir du **AdventureWorks** exemple de base de données que vous avez [téléchargé et restauré](sql-server-linux-migrate-restore-database.md).
2. Dans **l’Explorateur d’objets**, accédez à la base de données cible sur le serveur.
2. Avec le bouton droit de la base de données, puis sélectionnez **nouvelle requête**:

    ![Nouvelle requête. Se connecter au serveur de base de données SQL : SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/new-query.png)

3. Dans la fenêtre de requête, écrivez une requête Transact-SQL pour sélectionner les données à partir d’une des tables. L’exemple suivant sélectionne les données de la **Production.Product** table de la **AdventureWorks** base de données.

        SELECT TOP 10 Name, ProductNumber
        FROM Production.Product
        ORDER BY Name ASC

4. Cliquez sur le **Execute** bouton :

    ![Réussite. Se connecter au serveur de base de données SQL : SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/execute-query.png)

## <a name="next-steps"></a>Étapes suivantes

En plus des requêtes, vous pouvez utiliser des instructions T-SQL pour créer et gérer des bases de données.

Si vous utilisez T-SQL, consultez [didacticiel : écriture d’instructions Transact-SQL](https://msdn.microsoft.com/library/ms365303.aspx) et [de référence Transact-SQL (moteur de base de données)](https://msdn.microsoft.com/library/bb510741.aspx).

Pour plus d’informations sur l’utilisation de SSMS, consultez [utiliser SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx).

