---
title: Guide de démarrage rapide pour un Python de base « Hello World » de code d’exécution dans T-SQL - SQL Server Machine Learning
description: Guide de démarrage rapide pour le script Python dans SQL Server. Découvrez les principes fondamentaux de l’appel de script Python à l’aide de la procédure stockée système sp_execute_external_script dans un exercice hello-world.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/10/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: a2d0987441f8f26304590f5ccbde15a2e15cf3c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962066"
---
# <a name="quickstart-hello-world-python-script-in-sql-server"></a>Démarrage rapide : Script Python « Hello world » dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce démarrage rapide, vous découvrez les concepts clés en exécutant « Hello World » Python script inT-SQL, une introduction à la **sp_execute_external_script** procédure stockée système. 

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [Python vérifier existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour la configuration de l’environnement Python requis pour ce démarrage rapide.

## <a name="basic-python-interaction"></a>Interaction de Python de base

Il existe deux façons d’exécuter le code Python dans SQL Server :

+ Ajouter un script Python en tant qu’argument de la procédure stockée système, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ À partir d’un [à distance client Python](../python/setup-python-client-tools-sql.md), connectez-vous à SQL Server et d’exécuter du code à l’aide de SQL Server comme contexte de calcul. Cela nécessite [revoscalepy](../python/ref-py-revoscalepy.md).

L’exercice suivant se concentre sur le premier modèle d’interaction : comment passer de code Python à une procédure stockée.

1. Exécuter du code simple pour voir comment les données sont transmises dans les deux sens entre SQL Server et Python.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. En supposant que vous avez tout configuré correctement et que Python et SQL Server sont communiquent entre eux, le résultat correct est calculé et Python `print` fonction retourne le résultat à la **Messages** windows.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Lors de l’obtention **stdout** messages est pratique lorsque vous testez votre code, plus souvent vous avez besoin retourner les résultats dans un format tabulaire, afin que vous pouvez utiliser dans une application ou écrire dans une table.

Pour l’instant, n’oubliez pas ces règles :

+ Tous les éléments à l’intérieur de la `@script` argument doit être le code Python valide. 
+ Le code doit respecter toutes les règles Python concernant la mise en retrait, les noms de variables et ainsi de suite. Lorsque vous recevez une erreur, vérifiez votre espace blanc et la casse.
+ Parmi les langages de programmation Python est un des plus flexible en ce qui concerne les guillemets simples et des guillemets doubles ; ils sont pratiquement interchangeables. Toutefois, T-SQL utilise des guillemets simples pour uniquement certaines choses et le `@script` argument utilise les guillemets simples pour encadrer le code Python sous forme de chaîne Unicode. Par conséquent, vous devrez peut-être vérifier votre code Python et remplacer des guillemets simples par des guillemets doubles.
+ Si vous utilisez toutes les bibliothèques qui ne sont pas chargés par défaut, vous devez utiliser une instruction d’importation au début de votre script pour les charger. SQL Server ajoute plusieurs bibliothèques spécifiques au produit. Pour plus d’informations, consultez [bibliothèques Python](../python/python-libraries-and-data-types.md).
+ Si la bibliothèque n’est pas déjà installée, arrêter et installez le package Python en dehors de SQL Server, comme décrit ici : [Installer de nouveaux packages Python sur SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Exécuter un script de Hello World

L’exercice suivant exécute un autre scripts Python simple.

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

Entrées dans cette procédure stockée sont les suivantes :

+ *@language* paramètre définit l’extension du langage pour appeler, dans ce cas, Python.
+ *@script* paramètre définit les commandes passées au runtime Python. Votre script Python entier doit être placé entre cet argument, en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar**, puis appeler cette variable.
+ *@input_data_1* données sont retournées par la requête, passée au runtime Python, qui retourne les données vers SQL Server comme une trame de données.
+ DES jeux de résultats clause définit le schéma de la table de données retournées pour SQL Server, ajout de « Hello World » comme nom de colonne, **int** pour le type de données.

**Résultats**

| Hello World |
|-------------|
| 1 |

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez exécuté des scripts de Python simples, examinons plus en détail la structuration des entrées et sorties.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les entrées et sorties](quickstart-python-inputs-and-outputs.md)
