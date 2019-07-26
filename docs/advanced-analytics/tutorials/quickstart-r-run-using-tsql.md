---
title: Démarrage rapide pour une exécution de code R de base «Hello World» dans T-SQL
description: Démarrage rapide pour le script R dans SQL Server. Découvrez les principes fondamentaux de l’appel de script R à l’aide de la procédure stockée système sp_execute_external_script dans un exercice Hello World.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: ab73e0231f462504652e0e1af62fed80c706f061
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469034"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Démarrage rapide : Script R «Hello World» dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez apprendre les concepts clés en exécutant un script R «Hello World» R-SQL, avec une introduction à la procédure stockée système **sp_execute_external_script** . 

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que R existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour configurer l’environnement r requis pour ce guide de démarrage rapide.

## <a name="basic-r-interaction"></a>Interaction R de base

Vous pouvez exécuter du code R dans SQL Database de deux manières:

+ Ajoutez le script R en tant qu’argument de la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).
+ À partir d’un [client R distant](https://docs.microsoft.com/sql/advanced-analytics/r/set-up-a-data-science-client), connectez-vous à votre base de données SQL, puis exécutez le code en utilisant le SQL Database comme contexte de calcul.

L’exercice suivant est axé sur le premier modèle d’interaction: comment passer du code R à une procédure stockée.

1. Exécutez un script simple pour voir comment un script R s’exécute dans votre base de données SQL.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'R',
    @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

2. En supposant que tout est configuré correctement, le résultat correct est calculé et la fonction R `print` renvoie le résultat dans la fenêtre **messages** .

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Bien que l’obtention de messages **stdout** soit utile lors du test de votre code, il est souvent nécessaire de retourner les résultats sous forme de tableau, afin de pouvoir les utiliser dans une application ou les écrire dans une table. Consultez [démarrage rapide: Gérez les entrées et les sorties à l'](rtsql-working-with-inputs-and-outputs.md) aide de R dans SQL Server pour plus d’informations.

N’oubliez pas que tout `@script` ce qui se trouve à l’intérieur de l’argument doit être un code R valide.

## <a name="run-a-hello-world-script"></a>Exécuter un script de Hello World

L’exercice suivant exécute un autre script R simple.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'OutputDataSet<-InputDataSet',
  @input_data_1 =N'SELECT 1 AS hello'
  WITH RESULT SETS (([Hello World] int));
GO
```

Les entrées de cette procédure stockée sont les suivantes:

+ *@language* le paramètre définit l’extension de langage à appeler, dans le cas présent, R.
+ *@script* définit les commandes passées au runtime R. Votre script R entier doit être placé dans cet argument en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar**, puis appeler cette variable.
+ *@input_data_1* données retournées par la requête, passées au runtime R, qui retourne les données à SQL Server sous forme de trame de données.
+ La clause WITH RESULT SETS définit le schéma de la table de données retournée pour SQL Server, en ajoutant «Hello World» comme nom de colonne, **int** pour le type de données.

**Résultats**

| Hello World |
|-------------|
| 1 |

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez exécuté quelques scripts R simples, examinez de plus près la structuration des entrées et des sorties.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les entrées et les sorties](quickstart-r-inputs-and-outputs.md)
