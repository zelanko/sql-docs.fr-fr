---
title: Guide de démarrage rapide pour une exécution de code « Hello World » base R dans T-SQL (SQL Server Machine Learning) | Microsoft Docs
description: Guide de démarrage rapide pour le script R dans SQL Server. Découvrez les principes fondamentaux de l’appel de script R à l’aide de la procédure stockée système sp_execute_external_script dans un exercice hello-world.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/08/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1a51fcb9e67bef48346ff74ebfb1e911a6ee3365
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878082"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Démarrage rapide : Un script R « Hello world » dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server inclut la prise en charge du langage R pour l’analytique de science des données sur les données de SQL Server résidentes. Votre script R peut être constitué des fonctions R open source, des bibliothèques R de tiers ou des bibliothèques de Microsoft R intégrés tel que [RevoScaleR](../r/revoscaler-overview.md) pour l’analytique prédictive à l’échelle. 

L’exécution du script est via des procédures stockées, à l’aide d’une des approches suivantes :

+ Intégrés [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) procédure stockée, en passant dans un script R comme paramètre d’entrée.
+ Encapsuler le script R dans un [procédure stockée personnalisée](sqldev-in-database-r-for-sql-developers.md) que vous créez.

Dans ce démarrage rapide, vous découvrez les concepts clés en exécutant un « Hello World » R script inT-SQL, une introduction à la **sp_execute_external_script** procédure stockée système. 

## <a name="prerequisites"></a>Prérequis

Cet exercice requiert l’accès à une instance de SQL Server avec l’un des déjà installé les composants suivants :

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), avec le langage R installé
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

  Votre instance SQL Server peut être dans une machine virtuelle Azure ou en local. Soyez conscient que la fonctionnalité de script externe est désactivée par défaut, vous devrez donc peut-être à [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifiez que **service SQL Server Launchpad** est en cours d’exécution avant de commencer.

+ Un outil pour l’exécution de requêtes SQL. Vous pouvez utiliser n’importe quelle application qui peut se connecter à une base de données SQL Server et exécutez le code T-SQL. Les professionnels SQL peuvent utiliser SQL Server Management Studio (SSMS) ou Visual Studio.

Pour ce démarrage rapide, pour montrer combien il est facile d’exécuter R dans SQL Server, nous avons utilisé le nouveau **extension mssql pour Visual Studio Code**. VS Code est un environnement de développement gratuit qui peut s’exécuter sur Linux, macOS ou Windows. Le **mssql** extension est une extension léger pour exécuter des requêtes T-SQL. Pour vous procurer Visual Studio Code, consultez [Télécharger et installer Visual Studio Code](https://code.visualstudio.com/Download). Pour ajouter le **mssql** extension, consultez cet article : [utiliser l’extension mssql pour Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>Se connecter à une base de données et exécuter un script de test Hello World

1. Dans Visual Studio Code, créez un fichier texte et appelez-le BasicRSQL.sql.

2. Après avoir ouvert ce fichier, appuyez sur Ctrl + Maj + P (Commande + P sur un macOS), tapez **sql** pour afficher la liste des commandes SQL, puis sélectionnez **CONNECT**. Visual Studio Code vous invite à créer un profil à utiliser lors de la connexion à une base de données spécifique. Facultatif, mais rend plus facile de basculer entre les bases de données et des connexions.
    + Choisissez un serveur ou l’instance où R dans SQL Server a été installé.
    + Utilisez un compte qui dispose des autorisations nécessaires pour créer une base de données, exécuter des instructions SELECT et afficher les définitions de table.

2. Si la connexion aboutit, les noms du serveur et de la base de données doivent figurer dans la barre d’état avec vos informations d’identification actuelles. Si la connexion échoue, vérifiez que le nom de l’ordinateur et le nom du serveur sont corrects.

3. Collez cette instruction et exécutez-la.

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([Hello World] int));
    GO
    ```

Entrées dans cette procédure stockée sont les suivantes :

+ *@language* paramètre définit l’extension de langage à appeler, dans ce cas, R.
+ *@script* paramètre définit les commandes passées au runtime R. Votre script R entier doit être placé dans cet argument en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar**, puis appeler cette variable.
+ *@input_data_1* données sont retournées par la requête passée au runtime R, qui retourne les données vers SQL Server comme une trame de données.
+ DES jeux de résultats clause définit le schéma de la table de données retournées pour SQL Server, ajout de « Hello World » comme nom de colonne, **int** pour le type de données.

**Résultats**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

Si vous obtenez des erreurs à partir de cette requête, éliminer tout problème d’installation. Configuration de post-installation est nécessaire pour permettre l’utilisation des bibliothèques de code externe. Consultez [installer SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) ou [installer SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). De même, assurez-vous que le service Launchpad est en cours d’exécution. 

Selon votre environnement, vous pouvez être amené à activer les comptes de travail R pour vous connecter à SQL Server, installer des bibliothèques réseau supplémentaires, activer l’exécution de code à distance ou redémarrer l’instance une fois que tout est configuré. Pour plus d’informations, consultez [Installation de R Services et de mettre à niveau le Forum aux questions](../r/upgrade-and-installation-faq-sql-server-r-services.md)

> [!TIP]
> Dans Visual Studio Code, vous pouvez mettre en surbrillance le code à exécuter et appuyer sur Ctrl + Maj + E. Si vous avez peur d’oublier cette combinaison, vous pouvez la changer. Consultez [Personnaliser les combinaisons de touches de raccourci](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts).
> 
> ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)
> 

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez confirmé que votre instance est prêt à travailler avec R, examinons plus en détail la structuration des entrées et sorties.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les entrées et sorties](rtsql-working-with-inputs-and-outputs.md)
