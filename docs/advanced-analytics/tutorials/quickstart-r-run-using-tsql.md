---
title: Guide de démarrage rapide pour une exécution de code « Hello World » base R dans T-SQL - SQL Server Machine Learning
description: Guide de démarrage rapide pour le script R dans SQL Server. Découvrez les principes fondamentaux de l’appel de script R à l’aide de la procédure stockée système sp_execute_external_script dans un exercice hello-world.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7517b9ab18c7448014e8c9113430b2c21047f972
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046813"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>Démarrage rapide : Script R « Hello world » dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce démarrage rapide, vous découvrez les concepts clés en exécutant un « Hello World » R script inT-SQL, une introduction à la **sp_execute_external_script** procédure stockée système. 

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [R vérifier existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour la configuration de l’environnement R requis pour ce démarrage rapide.

## <a name="basic-r-interaction"></a>Interaction de base R

Il existe deux façons vous pouvez exécuter le code R dans SQL Database :

+ Ajouter un script R en tant qu’argument de la procédure stockée système, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).
+ À partir d’un [client R à distance](https://docs.microsoft.com/sql/advanced-analytics/r/set-up-a-data-science-client), connectez-vous à votre base de données SQL et exécuter du code à l’aide de la base de données SQL en tant que le contexte de calcul.

L’exercice suivant se concentre sur le premier modèle d’interaction : comment passer le code R à une procédure stockée.

1. Exécuter un script simple pour voir comment un script R s’exécute dans votre base de données SQL.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'R',
    @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c, d)'
    ```

2. En supposant que vous avez tout configuré correctement le résultat correct est calculée et le R `print` fonction retourne le résultat à la **Messages** fenêtre.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Lors de l’obtention **stdout** messages est utile lorsque vous testez votre code, plus souvent vous avez besoin retourner les résultats dans un format tabulaire, afin que vous pouvez utiliser dans une application ou écrire dans une table. Consultez [Guide de démarrage rapide : Handle d’entrées et sorties à l’aide de R dans SQL Server](rtsql-working-with-inputs-and-outputs.md) pour plus d’informations.

N’oubliez pas, tout le contenu de la `@script` argument doit être un code R valide.

## <a name="run-a-hello-world-script"></a>Exécuter un script de Hello World

L’exercice suivant exécute une autre des scripts R simples.

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

| Salut tout le monde |
|-------------|
| 1 |

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez exécuté quelques scripts R simples, examinons plus en détail la structuration des entrées et sorties.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les entrées et sorties](quickstart-r-inputs-and-outputs.md)
