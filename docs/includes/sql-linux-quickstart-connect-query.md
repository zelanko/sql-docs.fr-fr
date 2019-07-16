---
ms.openlocfilehash: 549224ae30b710292324a178aa48432bde7d34ca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215635"
---
## <a name="connect-locally"></a>Se connecter localement

La procédure suivante utilise **sqlcmd** pour se connecter localement à votre nouvelle instance de SQL Server.

1. Exécutez **sqlcmd** avec des paramètres pour le nom SQL Server (-S), le nom d’utilisateur (-U) et le mot de passe (-P). Dans ce didacticiel, comme vous vous connectez localement, le nom du serveur est `localhost`. Le nom d’utilisateur est `SA` et le mot de passe est celui que vous avez fourni pour le compte d’administrateur système lors de l’installation.

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > Vous pouvez omettre le mot de passe dans la ligne de commande pour être invité à l’entrer.

   > [!TIP]
   > Si vous décidez ultérieurement de vous connecter à distance, spécifiez l’adresse IP ou le nom de l’ordinateur pour le paramètre **-S** et vérifiez que le port 1433 est ouvert sur votre pare-feu.

1. Si l’opération réussit, vous devez accéder à une invite de commandes **sqlcmd** : `1>`.

1. Si un échec de connexion s’affiche, tentez tout d’abord de diagnostiquer le problème à partir du message d’erreur. Examinez ensuite les [recommandations en matière de résolution des problèmes de connexion](../linux/sql-server-linux-troubleshooting-guide.md#connection).

## <a name="create-and-query-data"></a>Créer et interroger des données
Les sections suivantes vous guident lors de l’utilisation de **sqlcmd** pour créer une base de données, ajouter des données et exécuter une requête simple.

### <a name="create-a-new-database"></a>Créer une base de données

La procédure suivante crée une base de données nommée `TestDB`.

1. À partir de l’invite de commandes **sqlcmd**, collez la commande Transact-SQL suivante pour créer une base de données de test :

   ```sql
   CREATE DATABASE TestDB
   ```

1. Sur la ligne suivante, écrivez une requête pour retourner le nom de toutes les bases de données sur votre serveur :

   ```sql
   SELECT Name from sys.Databases
   ```

1. Les deux commandes précédentes n’ont pas été exécutées immédiatement. Vous devez taper `GO` sur une nouvelle ligne pour exécuter les commandes précédentes :

   ```sql
   GO
   ```

> [!TIP]
> Pour en savoir plus sur l’écriture d’instructions Transact-SQL et les requêtes, consultez [didacticiel : Écriture d’instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

### <a name="insert-data"></a>Insérer des données

Créez ensuite une table, `Inventory`, et insérez deux nouvelles lignes.

1. À partir de l’invite de commandes **sqlcmd**, basculez le contexte vers la nouvelle base de données `TestDB` :

   ```sql
   USE TestDB
   ```

1. Créez une table nommée `Inventory` :

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Insérez des données dans la nouvelle table :

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Tapez `GO` pour exécuter les commandes précédentes :

   ```sql
   GO
   ```

### <a name="select-data"></a>Sélectionner les données

Exécutez maintenant une requête pour retourner des données de la table `Inventory`.

1. Dans l’invite de commandes **sqlcmd**, entrez une requête qui retourne les lignes de la table `Inventory` dont la quantité est supérieure à 152 :

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Exécutez la commande :

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Quitter l’invite de commandes sqlcmd

Pour mettre fin à votre session **sqlcmd**, tapez `QUIT` :

```sql
QUIT
```

## <a name="performance-best-practices"></a>Meilleures pratiques de performances

Après avoir installé SQL Server sur Linux, passez en revue les meilleures pratiques pour la configuration Linux et SQL Server pour améliorer les performances pour les scénarios de production. Pour plus d’informations, consultez les [Bonnes pratiques en matière de performances et instructions de configuration de SQL Server sur Linux](../linux/sql-server-linux-performance-best-practices.md).

## <a name="cross-platform-data-tools"></a>Outils de données entre les plates-formes

En plus de **sqlcmd**, vous pouvez utiliser les outils multiplateformes suivants pour gérer SQL Server :

|||
|---|---|
| [Azure Data Studio](../azure-data-studio/index.md) | Un utilitaire de gestion de base de données de l’interface graphique utilisateur inter-plateformes. |
| [Visual Studio Code](../linux/sql-server-linux-develop-use-vscode.md) | Un éditeur de code de l’interface graphique utilisateur interplateforme qui exécutent des instructions Transact-SQL avec l’extension mssql. |
| [PowerShell Core](../linux/sql-server-linux-manage-powershell-core.md) | Un outil automation et la configuration multiplateforme basé sur les applets de commande. |
| [mssql-cli](https://github.com/dbcli/mssql-cli/tree/master/doc) | Une interface de ligne de commande interplateforme pour l’exécution des commandes Transact-SQL. |

## <a name="connecting-from-windows"></a>Connexion à partir de Windows

Les outils SQL Server sur Windows se connectent aux instances de SQL Server sous Linux de la même façon qu’à n’importe quelle instance distante de SQL Server.

Si vous avez un ordinateur Windows qui peut se connecter à l’ordinateur Linux, tentez la même procédure dans cette rubrique à partir d’une invite de commandes Windows exécutant **sqlcmd**. Vérifiez simplement que vous utilisez l’adresse IP ou le nom d’ordinateur Linux cible plutôt que localhost et vérifiez que le port TCP 1433 est ouvert. Si vous avez des problèmes de connexion à partir de Windows, lisez les [recommandations en matière de résolution des problèmes de connexion](../linux/sql-server-linux-troubleshooting-guide.md#connection).

Pour d’autres outils qui s’exécutent sur Windows, mais se connectent à SQL Server sur Linux, consultez :

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-manage-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [Outils SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="other-deployment-scenarios"></a>Autres scénarios de déploiement

Pour connaître les autres scénarios d’installation, consultez les ressources suivantes :

|||
|---|---|
| [Upgrade](../linux/sql-server-linux-setup.md#upgrade) | Apprenez à mettre à niveau une installation existante de SQL Server sur Linux |
| [Désinstaller](../linux/sql-server-linux-setup.md#uninstall) | Désinstallez SQL Server sous Linux |
| [Installation sans assistance](../linux/sql-server-linux-setup.md#unattended) | Apprenez à créer un script d’installation sans invites |
| [Installation hors connexion](../linux/sql-server-linux-setup.md#offline) | Apprenez à télécharger manuellement les packages d’installation hors connexion |

> [!TIP]
> Pour obtenir des réponses aux questions fréquemment posées, consultez le [SQL Server sur le Forum aux questions sur Linux](../linux/sql-server-linux-faq.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Explorez les didacticiels pour SQL Server sur Linux](../linux/sql-server-linux-migrate-restore-database.md)