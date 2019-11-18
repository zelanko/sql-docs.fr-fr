---
title: 'Démarrage rapide : Types de données R'
titleSuffix: SQL Server Machine Learning Services
description: Dans ce démarrage rapide, vous allez apprendre à utiliser des types de données et des objets de données dans R et SQL Server avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4dab7cca8edcc01052ced81ec33a1f411da7ba9a
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73726977"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server-machine-learning-services"></a>Démarrage rapide : Gérer les objets et types de données en utilisant R dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez découvrir les problèmes courants susceptibles de se produire quand vous transférez des données entre R et SQL Server. L’expérience que vous obtenez dans le cadre de cet exercice fournit une base essentielle lorsque vous travaillez avec des données dans votre propre script.

Voici les problèmes courants à connaître :

- Les types de données ne correspondent pas toujours
- Des conversions implicites peuvent avoir lieu
- Des opérations de cast et de conversion sont parfois nécessaires.
- R et SQL utilisent des objets de données différents.

## <a name="prerequisites"></a>Conditions préalables requises

- Ce guide de démarrage rapide nécessite un accès à une instance de SQL Server sur laquelle est installée [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) avec le langage R.

  Votre instance SQL Server peut se trouver sur une machine virtuelle Azure ou être locale. Sachez simplement que la fonctionnalité de script externe est désactivée par défaut. De ce fait, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que le **service SQL Server Launchpad** est en cours d’exécution avant de commencer.

- Vous aurez aussi besoin d’un outil pour exécuter les requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à partir de n’importe quel outil de requête ou de gestion de base de données, pourvu qu’il puisse se connecter à une instance SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="always-return-a-data-frame"></a>Toujours retourner une trame de données

Quand votre script retourne les résultats de R vers SQL Server, il doit retourner les données sous forme de trame de données (objet **data.frame**). Tout autre type d’objet que vous générez dans votre script (liste, facteur, vecteur ou données binaires) doit être converti en trame de données si vous souhaitez retourner la sortie de l’objet dans les résultats de la procédure stockée. Heureusement, vous avez plusieurs fonctions R à votre disposition pour changer des objets différents en trame de données. Vous pouvez même sérialiser un modèle binaire et le retourner dans une trame de données, ce que vous ferez plus tard dans ce guide de démarrage rapide.

Tout d’abord, vous allez expérimenter certains objets R de base, notamment les vecteurs, matrices et listes, pour voir de quelle manière leur conversion en trame de données change la sortie passée à SQL Server.

Comparez ces deux scripts « Hello World » dans R. Les scripts semblent presque identiques, mais le premier retourne une seule colonne de trois valeurs, tandis que le second retourne trois colonnes avec une seule valeur chacune.

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

**Exemple 1 avec la fonction str ajoutée**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Exemple 2 avec la fonction str ajoutée**

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

Comme vous pouvez le constater, un léger changement dans la syntaxe R transforme le schéma des résultats. Nous n’allons pas en expliquer la raison ici, mais les différences entre les types de données R sont décrites en détail dans la section *Data Structures* dans [Advanced R](http://adv-r.had.co.nz), par Hadley Wickham.

Pour l’instant, gardez seulement à l’esprit que vous devez vérifier les résultats attendus quand vous convertissez des objets R en trames de données.

> [!TIP]
> Vous pouvez également utiliser des fonctions d’identité R, telles que `is.matrix`, `is.vector`, pour retourner des informations sur la structure de données interne.

## <a name="implicit-conversion-of-data-objects"></a>Conversion implicite des objets de données

Chaque objet de données R a ses propres règles pour le traitement des valeurs qui sont combinées avec un autre objet de données ayant le même nombre de dimensions ou avec un objet de données contenant des types de données hétérogènes.

Créez une petite table de données de test.

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

Par exemple, supposez que vous exécutez l’instruction suivante pour effectuer une multiplication de matrice à l’aide de R. Vous multipliez une matrice à une seule colonne de trois valeurs par un tableau de quatre valeurs, et attendez comme résultat une matrice contenant quatre colonnes de trois valeurs.

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

Toutefois, observez ce qui se passe quand vous modifiez la taille du tableau `y`.

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

Pourquoi ? Dans ce cas, les deux arguments peuvent être traités comme des vecteurs de même longueur, ce qui permet à R de retourner le produit interne sous forme de matrice.  C’est le comportement attendu selon les règles de l’algèbre linéaire, mais cela peut poser problème si votre application en aval s’attend à ce que le schéma de sortie reste toujours le même !

> [!TIP]
> 
> Vous obtenez des erreurs ? Vérifiez que vous exécutez la procédure stockée dans le contexte de la base de données qui contient la table, et non dans **maître** ou une autre base de données.
>
> Nous vous suggérons également d’éviter d’utiliser des tables temporaires pour ces exemples. Certains clients R mettent fin à une connexion entre les lots, ce qui supprime les tables temporaires.

## <a name="merge-or-multiply-columns-of-different-length"></a>Fusionner ou multiplier des colonnes de longueur différente

R offre une grande flexibilité dans l’utilisation de vecteurs de tailles différentes et la combinaison des structures en colonnes en trames de données. Les listes de vecteurs ressemblent parfois à des tables, mais elles ne suivent pas toutes les règles qui régissent les tables de base de données.

Par exemple, le script suivant définit un tableau numérique de longueur 6 et le stocke dans la variable R `df1`. Le tableau numérique est ensuite combiné aux entiers de la table RTestData, qui contient trois valeurs, pour créer la trame de données `df2`.

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
|100|6|

N’oubliez pas qu’une trame de données est une liste de vecteurs, même si elle a l’apparence d’une table.

## <a name="cast-or-convert-sql-server-data"></a>Effectuer un cast ou une conversion des données SQL Server

R et SQL Server n’utilisent pas les mêmes types de données. Quand vous exécutez une requête dans SQL Server pour obtenir des données que vous voulez ensuite passer au runtime R, un type de conversion implicite a généralement lieu. D’autres conversions sont effectuées quand vous retournez les données de R vers SQL Server.

- SQL Server transfère les données de la requête au processus R géré par le service Launchpad, et les convertit en représentation interne pour une plus grande efficacité.
- Le runtime R charge les données dans une variable data.frame et effectue ses propres opérations sur les données.
- Le moteur de base de données retourne les données à SQL Server par le biais d’une connexion sécurisée interne et présente les données en termes de types de données SQL Server.
- Vous obtenez les données en vous connectant à SQL Server à l’aide d’une bibliothèque cliente ou réseau qui peut envoyer des requêtes SQL et gérer des jeux de données tabulaires. Cette application cliente est susceptible de modifier les données d’autres manières.

Pour voir comment cela fonctionne, exécutez une requête telle que celle-ci sur l’entrepôt de données [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Cette requête retourne les données de ventes utilisées pour effectuer des prévisions.

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
> Vous pouvez utiliser n’importe quelle version d’AdventureWorks ou créer une requête différente à l’aide d’une de vos bases de données. Le but est de manipuler des données contenant du texte, des valeurs date/heure et des nombres.

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
- La colonne texte « ProductSeries » a été identifiée comme **facteur**, autrement dit une variable de catégorie. Par défaut, les valeurs de chaîne sont gérées comme des facteurs. Si vous passez une chaîne à R, cette chaîne est convertie en entier pour un usage interne, puis la valeur est mappée à la chaîne dans la sortie.

### <a name="summary"></a>Résumé

À partir de ces exemples courts, vous pouvez voir la nécessité de vérifier les effets de la conversion de données lors du passage de requêtes SQL en tant qu’entrée. Certains types de données SQL Server ne sont pas pris en charge dans R. Pour éviter les erreurs d’exécution, suivez ces conseils :

- Testez vos données au préalable. Vérifiez les colonnes ou valeurs dans votre schéma qui peuvent poser problème quand elles sont passées au code R.
- Spécifiez les colonnes dans votre source de données d’entrée individuellement, et non en utilisant `SELECT *`. Déterminez de quelle manière gérer chaque colonne.
- Effectuez les opérations de cast explicites nécessaires lors de la phase de préparation de vos données d’entrée, pour éviter tout comportement inattendu.
- Évitez de passer des colonnes de données (telles que des GUID ou des rowguid) qui provoquent des erreurs et qui ne sont pas utiles pour la modélisation.

Pour plus d’informations sur les types de données pris en charge et non pris en charge, consultez [Types de données et bibliothèques R](../r/r-libraries-and-data-types.md).

Pour plus d’informations sur l’impact sur les performances de la conversion de chaînes en facteurs numériques au moment de l’exécution, consultez [Réglage des performances de SQL Server R Services](../r/sql-server-r-services-performance-tuning.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur l’écriture de fonctions R avancées dans SQL Server, suivez ce démarrage rapide :

> [!div class="nextstepaction"]
> [Écrire des fonctions R avancées avec SQL Server Machine Learning Services](quickstart-r-functions.md)

Pour plus d’informations sur l’utilisation de R dans SQL Server Machine Learning Services, consultez les articles suivants :

- [Créer un modèle prédictif doté d’un score en R avec SQL Server Machine Learning Services](quickstart-r-train-score-model.md)
- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
