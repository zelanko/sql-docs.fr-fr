---
title: "Gérer SQL Server sur Linux avec SSMS | Documents Microsoft"
description: "Ce didacticiel montre comment utiliser SQL Server Management Studio sur Windows pour se connecter à SQL Server en cours d’exécution sur Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 30cc4564-f389-4707-9b25-8ba782cc5150
ms.workload: On Demand
ms.openlocfilehash: 9f774a7fde6a67bd5be6cd1bd395131c3c6ee0ba
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="use-sql-server-management-studio-ssms-on-windows-to-manage-sql-server-on-linux"></a>Utilisez SQL Server Management Studio (SSMS) sur Windows pour gérer SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique montre comment utiliser [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) pour se connecter à SQL Server 2017 sous Linux. SSMS est une application Windows, alors utilisez SSMS lorsque vous avez une machine Windows qui peut se connecter à une instance SQL Server distante sur Linux.

Une fois la connexion établie, vous lancez une simple requête Transact-SQL (T-SQL) pour vérifier la communication avec la base de données.

## <a name="install-the-newest-version-of-sql-server-management-studio"></a>Installez la dernière version de SQL Server Management Studio

Lorsque vous travaillez avec SQL Server, vous devez toujours utiliser la dernière version de SQL Server Management Studio (SSMS). La dernière version de SSMS est continuellement mise à jour et optimisée. Elle est actuellement compatible avec SQL Server 2017 sur Linux. Pour télécharger et installer la version la plus récente, consultez [télécharger SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Pour rester à jour, la dernière version de SSMS vous avertit lorsqu'une nouvelle version est disponible au téléchargement.

## <a name="connect-to-sql-server-on-linux"></a>Se connecter à SQL Server sur Linux

Les étapes suivantes montrent comment se connecter à SQL Server 2017 sur Linux avec SSMS.

1. Démarrez SSMS en tapant Microsoft SQL Server Management Studio dans la boîte de recherche Windows, puis cliquez sur l'application bureautique.

    ![SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png)

2. Dans la fenêtre **Connexion au serveur**, entrez les informations suivantes (si SSMS est déjà en cours d'exécution, cliquez sur **Connexion > Moteur de base de données** pour ouvrir la fenêtre **Connexion au serveur**) :

   | Paramètre |  Description |
   |-----|-----|
   | **Type de serveur** | La valeur par défaut est le moteur de base de données ; ne modifiez pas cette valeur. |
   | **Nom du serveur** | Entrez le nom de la machine cible Linux SQL Server ou son adresse IP. |
   | **Authentification** | Pour SQL Server 2017 sous Linux, utilisez l'authentification **SQL Server Authentification**. |
   | **Connexion** | Saisissez le nom d'un utilisateur ayant accès à une base de données sur le serveur (par exemple, le compte **SA** par défaut créé lors de la configuration).. |
   | **Mot de passe** | Saisissez le mot de passe pour l'utilisateur spécifié (pour le compte **SA**, vous l'avez créé lors de la configuration du serveur). |

    ![SQL Server Management Studio : Se connecter au serveur de base de données SQL](./media/sql-server-linux-develop-use-ssms/connect.png)

3. Cliquez sur **Se connecter**.

    > [!TIP]
    > Si vous obtenez un échec de connexion, essayez d'abord de diagnostiquer le problème à partir du message d'erreur. Passez ensuite en revue les [recommandations en matière de résolution des problèmes de connexion](sql-server-linux-troubleshooting-guide.md#connection).
 
5. Après vous être connecté à votre serveur SQL, **l’Explorateur d'objets** s'ouvre et vous pouvez désormais accéder à votre base de données pour effectuer des tâches administratives ou interroger des données.
 
     ![Explorateur d’objets](./media/sql-server-linux-develop-use-ssms/object-explorer.png)
     
## <a name="run-sample-queries"></a>Exécuter les exemples de requêtes

Une fois que vous vous connectez à votre serveur, vous pouvez vous connecter à une base de données et exécuter un exemple de requête. Si vous ne connaissez pas l’écriture de requêtes, consultez [l’écriture des instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

1. Identifiez une base de données à utiliser pour exécuter une requête. Cela peut être une nouvelle base de données que vous avez créé dans le [didacticiel de Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md). Ou il peut s’agir du **AdventureWorks** exemple de base de données que vous avez [téléchargé et restauré](sql-server-linux-migrate-restore-database.md).
2. Dans **l’Explorateur d’objets**, accédez à la base de données sur le serveur.
3. Cliquez vec le bouton droit sur la base de données, puis sélectionnez **nouvelle requête**:

    ![Nouvelle requête. Se connecter au serveur de base de données SQL : SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/new-query.png)

4. Dans la fenêtre de requête, écrivez une requête Transact-SQL pour sélectionner les données à partir d’une des tables. L’exemple suivant sélectionne les données de la table **Production.Product** de la base de données **AdventureWorks**.

        SELECT TOP 10 Name, ProductNumber
        FROM Production.Product
        ORDER BY Name ASC

5. Cliquez sur le bouton **Executer** :

    ![Réussite. Se connecter au serveur de base de données SQL : SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/execute-query.png)

## <a name="next-steps"></a>Étapes suivantes

En plus des requêtes, vous pouvez utiliser des instructions T-SQL pour créer et gérer des bases de données.

Si vous utilisez T-SQL, consultez [didacticiel : écriture d’instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md) et [de référence Transact-SQL (moteur de base de données)](https://msdn.microsoft.com/library/bb510741.aspx).

Pour plus d’informations sur l’utilisation de SSMS, consultez [utiliser SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx).
