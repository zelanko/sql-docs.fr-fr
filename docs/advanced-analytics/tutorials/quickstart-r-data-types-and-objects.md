---
title: Utiliser des types de données et des objets R et SQL
titleSuffix: SQL Server Machine Learning Services
description: Dans ce guide de démarrage rapide, vous allez apprendre à utiliser des types de données et des objets de données dans R et SQL Server avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0e490821194e909643e5307e833f093363cb9558
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006009"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server-machine-learning-services"></a>Démarrage rapide : Gérer les types de données et les objets à l’aide de R dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous découvrirez les problèmes courants qui se produisent lors du déplacement de données entre R et SQL Server. L’expérience que vous obtenez dans le cadre de cet exercice fournit un arrière-plan essentiel lorsque vous travaillez avec des données dans votre propre script.

Voici les problèmes courants à connaître :

- Les types de données ne correspondent pas toujours
- Des conversions implicites peuvent avoir lieu
- Des opérations de cast et de conversion sont parfois nécessaires.
- R et SQL utilisent des objets de données différents.

## <a name="prerequisites"></a>Prérequis

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage R installé.

  Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="always-return-a-data-frame"></a>Retourner toujours une trame de données

Quand votre script retourne les résultats de R vers SQL Server, il doit retourner les données sous forme de trame de données (objet **data.frame**). Tout autre type d’objet que vous générez dans votre script, qu’il s’agisse d’une liste, d’un facteur, d’un vecteur ou de données binaires, doit être converti en une trame de données si vous souhaitez le générer dans le cadre des résultats de la procédure stockée. Heureusement, vous avez plusieurs fonctions R à votre disposition pour changer des objets différents en trame de données. Vous pouvez même sérialiser un modèle binaire et le retourner dans une trame de données, ce que vous ferez ultérieurement dans ce guide de démarrage rapide.

Tout d’abord, expérimentons quelques objets r de base r (vecteurs, matrices et listes) et voyons comment la conversion en une trame de données modifie la sortie transmise à SQL Server.

Comparez ces deux scripts « Hello World » dans R. Les scripts semblent presque identiques, mais la première retourne une seule colonne de trois valeurs, tandis que la seconde retourne trois colonnes avec une seule valeur chacune.

**Exemple 1**

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
     , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
     , @input_data_1 = N' ';
```

**Exemple 2**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'
      , @input_data_1 = N'  ';
```

## <a name="identify-schema-and-data-types"></a>Identifier les types de schéma et de données

Pourquoi les résultats sont-ils si différents ?

La réponse est généralement liée à l’utilisation de la commande R `str()`. Ajoutez la fonction `str(object_name)` à n’importe quel endroit dans votre script R pour que le schéma de données de l’objet R spécifié soit retourné sous forme de message d’information. Pour afficher les messages, accédez au volet **Messages** dans Visual Studio Code ou à l’onglet **Messages** dans SSMS.

Pour comprendre pourquoi les exemples 1 et 2 ont des résultats très différents, insérez la ligne `str(OutputDataSet)` à la fin de la définition de variable _@script_ dans chaque instruction, comme ceci :

**Exemple 1 avec la fonction Str ajoutée**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Exemple 2 avec la fonction Str ajoutée**

```sql
EXECUTE sp_execute_external_script
  @language = N'R', 
  @script = N' OutputDataSet <- data.frame(c("hello"), " ", c("world"));
    str(OutputDataSet);' , 
  @input_data_1 = N'  ';
```

Examinez ensuite le texte affiché dans **Messages** pour voir ce qui diffère.

**Résultats de l’exemple 1**

```sql
STDOUT message(s) from external script:
'data.frame':   3 obs. of  1 variable:
$ mytextvariable: Factor w/ 3 levels " ","hello","world": 2 1 3
```

**Résultats de l’exemple 2**

```sql
STDOUT message(s) from external script:
'data.frame':   1 obs. of  3 variables:
$ c..hello..: Factor w/ 1 level "hello": 1
$ X...      : Factor w/ 1 level " ": 1
$ c..world..: Factor w/ 1 level "world": 1
```

Comme vous pouvez le constater, un léger changement dans la syntaxe R transforme le schéma des résultats. Nous n’allons pas expliquer pourquoi, mais les différences dans les types de données R sont expliquées en détail dans la section *structures de données* de [« avancé R » de Hadley Wickham](http://adv-r.had.co.nz).

Pour l’instant, gardez seulement à l’esprit que vous devez vérifier les résultats attendus quand vous convertissez des objets R en trames de données.

> [!TIP]
> Vous pouvez également utiliser des fonctions d’identité R, telles que `is.matrix`, `is.vector`, pour retourner des informations sur la structure de données interne.

## <a name="implicit-conversion-of-data-objects"></a>Conversion implicite des objets de données

Chaque objet de données R a ses propres règles pour le traitement des valeurs qui sont combinées avec un autre objet de données ayant le même nombre de dimensions ou avec un objet de données contenant des types de données hétérogènes.

Tout d’abord, créez une petite table de données de test.

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)

INSERT INTO RTestData
VALUES (1);

INSERT INTO RTestData
VALUES (10);

INSERT INTO RTestData
VALUES (100);
GO
```

Par exemple, supposons que vous exécutez l’instruction suivante pour effectuer une multiplication de matrice à l’aide de R. Vous multipliez une matrice à une seule colonne par les trois valeurs d’un tableau avec quatre valeurs, et vous attendez une matrice 4x3 comme résultat.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:15);
    OutputDataSet <- as.data.frame(x %*% y);'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));
```

En réalité, la colonne de trois valeurs est convertie en une matrice à une seule colonne. Étant donné qu’une matrice est simplement un tableau particulier dans R, le tableau `y` est implicitement converti en une matrice à une colonne pour rendre les deux arguments conformes.

**Résultats**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|

Toutefois, notez ce qui se produit lorsque vous modifiez la taille du tableau `y`.

```sql
execute sp_execute_external_script
   @language = N'R'
   , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:14);
   OutputDataSet <- as.data.frame(y %*% x);'
   , @input_data_1 = N' SELECT [Col1]  from RTestData;'
   WITH RESULT SETS (([Col1] int ));
```

R retourne maintenant une seule valeur comme résultat.

**Résultats**

|Col1|
|---|
|1542|

Pourquoi ? Dans ce cas, étant donné que les deux arguments peuvent être traités comme des vecteurs de la même longueur, R retourne le produit interne sous forme de matrice.  C’est le comportement attendu selon les règles de l’algèbre linéaire, mais cela peut poser problème si votre application en aval s’attend à ce que le schéma de sortie reste toujours le même !

> [!TIP]
> 
> Vous obtenez des erreurs ? Assurez-vous que vous exécutez la procédure stockée dans le contexte de la base de données qui contient la table, et non dans **Master** ou dans une autre base de données.
>
> Nous vous suggérons également d’éviter d’utiliser des tables temporaires pour ces exemples. Certains clients R mettent fin à une connexion entre les lots, en supprimant les tables temporaires.

## <a name="merge-or-multiply-columns-of-different-length"></a>Fusionner ou multiplier des colonnes de longueur différente

R offre une grande flexibilité pour travailler avec des vecteurs de différentes tailles, et pour combiner ces structures de type colonne en trames de données. Les listes de vecteurs ressemblent parfois à des tables, mais elles ne suivent pas toutes les règles qui régissent les tables de base de données.

Par exemple, le script suivant définit un tableau numérique de longueur 6 et le stocke dans la variable R `df1`. Le tableau numérique est ensuite combiné aux entiers de la table RTestData, qui contient trois (3) valeurs, pour créer une nouvelle trame de données, `df2`.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
               df1 <- as.data.frame( array(1:6) );
               df2 <- as.data.frame( c( InputDataSet , df1 ));
               OutputDataSet <- df2'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));
```

Pour remplir la trame de données, R répète les éléments récupérés de la table RTestData autant de fois que nécessaire pour obtenir le même nombre d’éléments que dans le tableau `df1`.

**Résultats**

|*Col2*|*Col3*|
|----|----|
|1|1|
|10|2|
|100|3|
|1|4|
|10|5|
|100|6\.|

N’oubliez pas qu’une trame de données est une liste de vecteurs, même si elle a l’apparence d’une table.

## <a name="cast-or-convert-sql-server-data"></a>Effectuer un cast ou une conversion des données SQL Server

R et SQL Server n’utilisent pas les mêmes types de données. Quand vous exécutez une requête dans SQL Server pour obtenir des données que vous voulez ensuite passer au runtime R, un type de conversion implicite a généralement lieu. D’autres conversions sont effectuées quand vous retournez les données de R vers SQL Server.

- SQL Server transmet les données de la requête au processus R géré par le service Launchpad et les convertit en représentation interne pour une plus grande efficacité.
- Le runtime R charge les données dans une variable data.frame et effectue ses propres opérations sur les données.
- Le moteur de base de données retourne les données à SQL Server par le biais d’une connexion sécurisée interne et présente les données en termes de types de données SQL Server.
- Vous obtenez les données en vous connectant à SQL Server à l’aide d’une bibliothèque cliente ou réseau qui peut envoyer des requêtes SQL et gérer des jeux de données tabulaires. Cette application cliente est susceptible de modifier les données d’autres manières.

Pour voir comment cela fonctionne, exécutez une requête telle que celle-ci dans l’entrepôt de données [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) . Cette requête retourne les données de ventes utilisées pour effectuer des prévisions.

```sql
USE AdventureWorksDW
GO

SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = 'M200 Europe'
           ORDER BY ReportingDate ASC
```

> [!NOTE]
>
> Vous pouvez utiliser n’importe quelle version d’AdventureWorks ou créer une requête différente à l’aide d’une base de données de votre choix. Le point est de tenter de gérer des données qui contiennent du texte, des valeurs DateTime et des valeurs numériques.

À présent, essayez de coller cette requête comme entrée de la procédure stockée.

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
      , @script = N' str(InputDataSet);
      OutputDataSet <- InputDataSet;'
      , @input_data_1 = N'
           SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = ''M200 Europe''
           ORDER BY ReportingDate ASC ;'
WITH RESULT SETS undefined;
```

Si vous obtenez une erreur, vous devez probablement modifier le texte de la requête. Par exemple, le prédicat de chaîne dans la clause WHERE doit être placé entre deux paires de guillemets simples.

Si la requête réussit, examinez les résultats de la fonction `str` pour voir de quelle manière R traite les données d’entrée.

**Résultats**

```sql
STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:
STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"
STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1
STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950
```

- La colonne date/heure a été traitée avec le type de données R **POSIXct**.
- La colonne de texte « ProductSeries » a été identifiée comme un **facteur**, ce qui signifie une variable catégorique. Par défaut, les valeurs de chaîne sont gérées comme des facteurs. Si vous passez une chaîne à R, cette chaîne est convertie en entier pour un usage interne, puis la valeur est mappée à la chaîne dans la sortie.

### <a name="summary"></a>Récapitulatif

À partir de ces exemples courts, vous pouvez voir la nécessité de vérifier les effets de la conversion de données lors du passage de requêtes SQL en entrée. Étant donné que certains types de données SQL Server ne sont pas pris en charge par R, utilisez les méthodes suivantes pour éviter les erreurs :

- Testez vos données à l’avance et vérifiez les colonnes ou les valeurs de votre schéma qui peuvent être un problème lorsqu’elles sont transmises à du code R.
- Spécifiez les colonnes dans votre source de données d’entrée individuellement, et non en utilisant `SELECT *`. Déterminez de quelle manière gérer chaque colonne.
- Effectuez les opérations de cast explicites nécessaires lors de la phase de préparation de vos données d’entrée, pour éviter tout comportement inattendu.
- Évitez de passer des colonnes de données (telles que des GUID ou des rowguid) qui provoquent des erreurs et qui ne sont pas utiles pour la modélisation.

Pour plus d’informations sur les types de données pris en charge et non pris en charge, consultez [bibliothèques et types de données R](../r/r-libraries-and-data-types.md).

Pour plus d’informations sur l’impact sur les performances de la conversion des chaînes au moment de l’exécution en facteurs numériques, consultez [SQL Server R services le réglage des performances](../r/sql-server-r-services-performance-tuning.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur l’écriture de fonctions R avancées dans SQL Server, suivez ce guide de démarrage rapide :

> [!div class="nextstepaction"]
> [Écrire des fonctions R avancées avec SQL Server Machine Learning Services](quickstart-r-functions.md)

Pour plus d’informations sur l’utilisation de R dans SQL Server Machine Learning Services, consultez les articles suivants :

- [Créer et évaluer un modèle prédictif dans R avec SQL Server Machine Learning Services](quickstart-r-train-score-model.md)
- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
