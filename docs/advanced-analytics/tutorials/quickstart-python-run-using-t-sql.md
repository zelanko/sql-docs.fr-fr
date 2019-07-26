---
title: Démarrage rapide pour une exécution de code «Hello World» de base python dans T-SQL
description: Démarrage rapide pour le script Python dans SQL Server. Découvrez les principes fondamentaux de l’appel de script Python à l’aide de la procédure stockée système sp_execute_external_script dans un exercice Hello World.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/10/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1281da6a366f7fa9d5fca20cc719a3c86825e56d
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469620"
---
# <a name="quickstart-hello-world-python-script-in-sql-server"></a>Démarrage rapide : Script Python «Hello World» dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez apprendre les concepts clés en exécutant un «Hello World» de script Python inT-SQL, avec une introduction à la procédure stockée système **sp_execute_external_script** . 

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que Python existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour configurer l’environnement python requis pour ce guide de démarrage rapide.

## <a name="basic-python-interaction"></a>Interaction python de base

Il existe deux façons d’exécuter du code python dans SQL Server:

+ Ajoutez un script Python en tant qu’argument de la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ À partir d’un [client python distant](../python/setup-python-client-tools-sql.md), connectez-vous à SQL Server et exécutez le code à l’aide du SQL Server comme contexte de calcul. Cela requiert [revoscalepy](../python/ref-py-revoscalepy.md).

L’exercice suivant est axé sur le premier modèle d’interaction: comment passer du code Python à une procédure stockée.

1. Exécutez du code simple pour voir comment les données sont transmises entre SQL Server et Python.

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

2. En supposant que tout est configuré correctement et que Python et SQL Server communiquent entre eux, le résultat correct est calculé et la fonction python `print` retourne le résultat dans les fenêtres de **messages** .

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    Bien que l’obtention de messages **stdout** soit pratique lors du test de votre code, il est souvent nécessaire de retourner les résultats sous forme de tableau, afin de pouvoir les utiliser dans une application ou les écrire dans une table.

Pour le moment, rappelez-vous des règles suivantes:

+ Tout ce qui `@script` se trouve à l’intérieur de l’argument doit être un code python valide. 
+ Le code doit suivre toutes les règles python relatives à la mise en retrait, aux noms de variable, etc. Lorsque vous recevez une erreur, vérifiez les espaces blancs et la casse.
+ Parmi les langages de programmation, Python est l’une des plus flexibles en ce qui concerne les guillemets simples et les guillemets doubles. ils sont à peu près interchangeables. Toutefois, T-SQL utilise des guillemets simples uniquement pour certains éléments, `@script` et l’argument utilise des guillemets simples pour encadrer le code python sous la forme d’une chaîne Unicode. Par conséquent, vous devrez peut-être examiner votre code Python et remplacer des guillemets simples par des guillemets doubles.
+ Si vous utilisez des bibliothèques qui ne sont pas chargées par défaut, vous devez utiliser une instruction import au début de votre script pour les charger. SQL Server ajoute plusieurs bibliothèques spécifiques à un produit. Pour plus d’informations, consultez [bibliothèques python](../python/python-libraries-and-data-types.md).
+ Si la bibliothèque n’est pas déjà installée, arrêtez et installez le package Python en dehors de SQL Server, comme décrit ici: [Installer de nouveaux packages Python sur SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Exécuter un script de Hello World

L’exercice suivant exécute un autre script Python simple.

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

Les entrées de cette procédure stockée sont les suivantes:

+ *@language* le paramètre définit l’extension de langage à appeler, dans ce cas, Python.
+ *@script* définit les commandes passées au runtime Python. L’intégralité de votre script Python doit être placée dans cet argument, en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar**, puis appeler cette variable.
+ *@input_data_1* données retournées par la requête, passées au runtime Python, qui retourne les données à SQL Server sous la forme d’une trame de données.
+ La clause WITH RESULT SETS définit le schéma de la table de données retournée pour SQL Server, en ajoutant «Hello World» comme nom de colonne, **int** pour le type de données.

**Résultats**

| Hello World |
|-------------|
| 1 |

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez exécuté quelques scripts Python simples, examinez de plus près la structuration des entrées et des sorties.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les entrées et les sorties](quickstart-python-inputs-and-outputs.md)
