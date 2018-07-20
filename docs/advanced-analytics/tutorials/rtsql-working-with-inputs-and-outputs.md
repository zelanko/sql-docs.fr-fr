---
title: Guide de démarrage rapide pour l’utilisation des entrées et sorties dans R (SQL Server Machine Learning) | Microsoft Docs
description: Dans ce démarrage rapide pour le script R dans SQL Server, découvrez comment structurer les entrées et sorties pour la procédure stockée système sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b41a8c30cd0ecbe040819478c0cadece1b9eb704
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086581"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Démarrage rapide : Gérer les entrées et sorties à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Lorsque vous souhaitez exécuter le code R dans SQL Server, vous devez encapsuler le script R dans une procédure stockée. Vous pouvez écrire une, ou passer à un script R [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Ce système de procédure stockée est utilisée pour démarrer le runtime R dans le contexte de SQL Server, qui transmet les données à R, gère les sessions utilisateur R en toute sécurité et retourne les résultats au client.

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [Hello World dans R et SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), fournit des informations et des liens pour la configuration de l’environnement R requis pour ce démarrage rapide.

<a name="bkmk_SSMSBasics"></a>

## <a name="create-some-simple-test-data"></a>Créer des données de test simples

Créer une petite table de données de test en exécutant l’instruction T-SQL suivante :

```sql
CREATE TABLE RTestData ([col1] int not null) ON [PRIMARY]
INSERT INTO RTestData   VALUES (1);
INSERT INTO RTestData   VALUES (10);
INSERT INTO RTestData   VALUES (100) ;
GO
```

Une fois la table créée, utilisez l’instruction suivante pour interroger la table :
  
```sql
SELECT * FROM RTestData
```

**Résultats**

![Contenu de la table RTestData](media/quickstart-r-working-input-outputs-results-1.png)


## <a name="get-the-same-data-using-r-script"></a>Obtenir les mêmes données avec un script R

Une fois la table créée, exécutez l’instruction suivante :

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

Il obtient les données de la table, effectue un aller-retour via le runtime R et retourne les valeurs avec le nom de colonne *NewColName*.

**Résultats**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**Commentaires**

+ Le paramètre *@language*  définit l’extension de langage à appeler, dans le cas présent, R.
+ Dans le paramètre *@script*, vous définissez les commandes à passer au runtime R. Votre script R entier doit être placé dans cet argument en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar**, puis appeler cette variable.
+ Les données retournées par la requête sont passées au runtime R, qui retourne les données à SQL Server sous la forme d’une trame de données.
+ La clause WITH RESULT SETS définit le schéma de la table de données retournée pour SQL Server.

## <a name="change-input-or-output-variables"></a>Modifier les variables d’entrée ou de sortie

L’exemple précédent utilisait les noms de variables d’entrée et de sortie par défaut, _InputDataSet_ et _OutputDataSet_. Pour définir les données d’entrée associées à _InputDatSet_, vous utilisez la variable *@input_data_1*.

Dans cet exemple, les noms des variables de sortie et d’entrée de la procédure stockée ont été remplacés par *SQLOut* et *SQLIn* :

```sql
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N' SQL_out <- SQL_in;'
  , @input_data_1 = N' SELECT 12 as Col;'
  , @input_data_1_name  = N'SQL_In'
  , @output_data_1_name =  N'SQL_Out'
  WITH RESULT SETS (([NewColName] int NOT NULL));
```

Avez-vous reçu l’erreur, « SQL de l’objet\_dans introuvable » ? C’est parce que R respecte la casse ! Dans l’exemple, le script R utilise les variables *SQL_in* et *SQL_out*, mais les paramètres de la procédure stockée utilisent les variables *SQL_In* et *SQL_Out*.

Essayez de corriger **uniquement** le *SQL_In* à la variable *@script* et réexécutez la procédure stockée.

Maintenant vous obtenez un **différents** erreur :

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

Nous vous affichons cette erreur, car vous pouvez vous attendre reverrez souvent lorsque vous testez de nouveau code R. Cela signifie que le script R a été correctement exécutée, mais SQL Server ne reçu aucune donnée ou a reçu des données incorrectes ou inattendues.

Dans ce cas, le schéma de sortie (la ligne commençant par **WITH**) indique qu’une colonne de données de type entier doit être retournée, mais dans la mesure où R a placé les données dans une variable différente, rien n’est renvoyé à SQL Server ; d’où l’erreur. Pour corriger cette erreur, corrigez le nom de la deuxième variable.

**N’oubliez pas ces exigences !**

- Les noms de variables doivent suivre les règles applicables aux identificateurs SQL.
- L’ordre des paramètres est important. Vous devez commencer par spécifier les paramètres obligatoires *@input_data_1* et *@output_data_1* pour pouvoir utiliser les paramètres facultatifs *@input_data_1_name* et *@output_data_1_name*.
- Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres datasets à partir de votre code R et retourner des sorties d’autres types en plus du dataset. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats. Vous trouverez un exemple simple plus loin dans ce didacticiel.
- L’instruction `WITH RESULT SETS` définit le schéma des données, au profit de SQL Server. Vous devez fournir des types de données compatibles avec SQL pour chaque colonne que vous retournez à partir de R. Vous pouvez aussi utiliser la définition de schéma pour fournir des nouveaux noms de colonnes. Il n’est pas nécessaire d’utiliser les noms de colonnes de la trame de données R. Dans certains cas, cette clause est facultative. Essayez en l’omettant et voyez ce qui se passe.

## <a name="generate-results-using-r"></a>Générer des résultats à l’aide de R

Vous pouvez également générer des valeurs en utilisant le script R et en laissant vide la chaîne de requête d’entrée dans _@input_data_1_. Vous pouvez également utiliser une instruction SQL SELECT valide comme espace réservé et ne pas utiliser les résultats SQL dans le script R.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
   , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
   , @input_data_1 = N' SELECT 1 as Temp1'
   WITH RESULT SETS (([Col1] char(20) NOT NULL));
```

**Résultats**

![Résultats de la requête à l’aide de @script en tant qu’entrée](media/quickstart-r-working-input-outputs-results-3.png)

## <a name="next-steps"></a>Étapes suivantes

Examiner certains des problèmes que vous pouvez rencontrer lors du passage des données entre R et SQL Server, telles que les conversions implicites et les différences dans les données tabulaires entre R et SQL.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les objets et les types de données](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)