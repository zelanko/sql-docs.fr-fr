## <a name="connect-locally"></a>Se connecter localement

La procédure suivante utilise **sqlcmd** pour se connecter localement à votre nouvelle instance de SQL Server.

1. Exécutez **sqlcmd** avec des paramètres pour le nom SQL Server (-S), le nom d’utilisateur (-U) et le mot de passe (-P). Dans ce didacticiel, comme vous vous connectez localement, le nom du serveur est `localhost`. Le nom d’utilisateur est `SA` et le mot de passe est celui que vous avez fourni pour le compte d’administrateur système lors de l’installation.

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > Vous pouvez omettre le mot de passe sur la ligne de commande pour être invité à l’entrer.

   > [!TIP]
   > Si vous décidez ultérieurement de vous connecter à distance, spécifiez l’adresse IP ou le nom de l’ordinateur pour le paramètre **-S** et vérifiez que le port 1433 est ouvert sur votre pare-feu.

1. Si l’opération réussit, vous devez accéder à une invite de commandes **sqlcmd** : `1>`.

1. Si un échec de connexion s’affiche, tentez tout d’abord de diagnostiquer le problème à partir du message d’erreur. Examinez ensuite les [recommandations en matière de résolution des problèmes de connexion](../linux/sql-server-linux-troubleshooting-guide.md#connection).

## <a name="create-and-query-data"></a>Créer et interroger des données
Les sections suivantes vous guident lors de l’utilisation de **sqlcmd** et Transact-SQL pour créer une base de données, ajouter des données et exécuter une requête simple.

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

1. À partir de l’invite de commandes **sqlcmd**, entrez une requête qui retourne des lignes de la table `Inventory` où la quantité est supérieure à 152 :

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

## <a name="connect-from-windows"></a>Se connecter à partir de Windows

Il est important de noter que les outils SQL Server sur Windows se connectent aux instances de SQL Server sur Linux de la même façon qu’ils se connectent à n’importe quelle instance distante de SQL Server.

Si vous avez un ordinateur Windows qui peut se connecter à l’ordinateur Linux, tentez la même procédure dans cette rubrique à partir d’une invite de commandes Windows exécutant **sqlcmd**. Vérifiez simplement que vous utilisez l’adresse IP ou le nom d’ordinateur Linux cible plutôt que localhost et vérifiez que le port TCP 1433 est ouvert. Si vous avez des problèmes de connexion à partir de Windows, lisez les [recommandations en matière de résolution des problèmes de connexion](../linux/sql-server-linux-troubleshooting-guide.md#connection).

Pour d’autres outils qui s’exécutent sur Windows, mais se connectent à SQL Server sur Linux, consultez :

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-develop-use-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="next-steps"></a>Étapes suivantes

Si vous débutez avec T-SQL, consultez [Didacticiel : écriture d’instructions Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md) et [Référence Transact-SQL (moteur de base de données)](../t-sql/language-reference.md).

Pour découvrir d’autres façons de se connecter à SQL Server et de le gérer, consultez [Visual Studio Code](../linux/sql-server-linux-develop-use-vscode.md) et [SQL Server Management Studio](../linux/sql-server-linux-develop-use-ssms.md).