---
title: "À l’aide de code R dans Transact-SQL (R dans démarrage rapide de SQL) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 4e6fe30d-a105-4d5b-bc05-5e5204753847
caps.latest.revision: 36
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c023af0a3a9b9c53cb2b6adf7298c18657a60803
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="using-r-code-in-transact-sql-r-in-sql-quickstart"></a>À l’aide de code R dans Transact-SQL (R dans démarrage rapide de SQL)

Ce didacticiel vise à vous familiariser avec les mécanismes basiques d’appel de script R à partir d’une procédure stockée T-SQL.

**Vous allez apprendre**

+ Comment incorporer R dans une fonction T-SQL
+ Quelques conseils pour travailler avec R et SQL objets de données et les types de données
+ Comment créer un modèle simple, puis enregistrez-le à SQL Server
+ Comment créer des prédictions et un traçage R à l’aide du modèle

**Durée estimée**

30 minutes, sans l’étape de configuration

## <a name="prerequisites"></a>Conditions préalables

Vous devez avoir accès à une instance de SQL Server avec l’un des déjà installé les composants suivants :

+ Services SQL Server 2017 Machine Learning, avec le langage R installé
+ SQL Server 2016 R Services

Votre instance de SQL Server peut être dans une machine virtuelle Azure ou localement. Soyez conscient que la fonctionnalité de script externe est désactivée par défaut, donc vous devrez peut-être effectuer quelques étapes supplémentaires pour qu’elle fonctionne.

Pour exécuter des requêtes SQL incluant des scripts de R, vous pouvez utiliser n’importe quelle autre application qui peut se connecter à une base de données et exécutez le code T-SQL. Professionnels de l’informatique SQL peuvent utiliser SQL Server Management Studio (SSMS) ou Visual Studio.

Dans ce didacticiel, pour indiquer combien il est facile à exécuter R dans SQL Server, nous avons utilisé la nouvelle **extension mssql pour le Code de Visual Studio**. Code de Visual Studio est un environnement de développement gratuit qui peut s’exécuter sur Linux, Mac OS ou Windows. Le **mssql*** extension est une extension léger pour l’exécution des requêtes SQL. Pour l’installer, consultez cet article : [Utiliser l’extension mssql pour Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>Se connecter à une base de données et exécuter un script de test Hello World

1. Dans Visual Studio Code, créez un fichier texte et appelez-le BasicRSQL.sql.
2. Après avoir ouvert ce fichier, appuyez sur Ctrl + Maj + P (Commande + P sur un macOS), tapez **sql** pour afficher la liste des commandes SQL, puis sélectionnez **CONNECT**. Code Visual Studio vous invite à créer un profil à utiliser lors de la connexion à une base de données spécifique. Cela est facultatif, mais rend plus facile de basculer entre les bases de données et des connexions.
    + Choisissez un serveur ou l’instance où R dans SQL Server a été installé.
    + Utilisez un compte qui dispose des autorisations nécessaires pour créer une base de données, exécuter des instructions SELECT et afficher les définitions de table.
2. Si la connexion aboutit, les noms du serveur et de la base de données doivent figurer dans la barre d’état avec vos informations d’identification actuelles. Si la connexion échoue, vérifiez que le nom de l’ordinateur et le nom du serveur sont corrects.
3. Collez cette instruction et exécutez-la.

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Dans Visual Studio Code, vous pouvez mettre en surbrillance le code à exécuter et appuyer sur Ctrl + Maj + E. Si vous avez peur d’oublier cette combinaison, vous pouvez la changer. Consultez [Personnaliser les combinaisons de touches de raccourci](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts).

    ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)

**Résultats**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

## <a name="troubleshooting"></a>Dépannage

+ Si vous obtenez des erreurs de cette requête, installation peut-être être incomplet. Après avoir ajouté la fonctionnalité à l’aide de l’Assistant Installation de SQL Server, vous devez exécuter des étapes supplémentaires pour permettre l’utilisation de bibliothèques de code externes.  Consultez [Configurer SQL Server R Services](../r/set-up-sql-server-r-services-in-database.md).

+ Vérifiez que le service Launchpad est en cours d’exécution. Selon votre environnement, vous pouvez être amené à activer les comptes de travail R pour vous connecter à SQL Server, installer des bibliothèques réseau supplémentaires, activer l’exécution de code à distance ou redémarrer l’instance une fois que tout est configuré. Consultez [Questions fréquentes sur l’installation et la mise à niveau de R Services](../r/upgrade-and-installation-faq-sql-server-r-services.md)

+ Pour vous procurer Visual Studio Code, consultez [Télécharger et installer Visual Studio Code](https://code.visualstudio.com/Download).

## <a name="next-lesson"></a>Leçon suivante

Maintenant que votre instance est prêt à travailler avec R, nous pouvons commencer.

Leçon 1 : [utilisation des entrées et sorties](rtsql-working-with-inputs-and-outputs.md)

Leçon 2 : [R et SQL objets de données et les types de données](rtsql-r-and-sql-data-types-and-data-objects.md)

Leçon 3 : [fonctions à l’aide de R avec des données SQL Server](rtsql-using-r-functions-with-sql-server-data.md)

Leçon 4 : [créer un modèle de prévision](rtsql-create-a-predictive-model-r.md)

Leçon 5 : [prédire et traçage à partir du modèle](rtsql-predict-and-plot-from-model.md)

