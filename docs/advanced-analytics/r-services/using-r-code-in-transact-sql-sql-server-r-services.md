---
title: "Utilisation de code R dans Transact-SQL (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4e6fe30d-a105-4d5b-bc05-5e5204753847
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 28
---
# Utilisation de code R dans Transact-SQL (SQL Server R Services)
Ce didacticiel fournit des exemples très courts de syntaxe à utiliser avec R dans SQL Server R Services.    
    
    
Il s’agit d’un bon point de départ pour débuter avec SQL Server R Services et découvrir les principes de base de la définition de script R dans une procédure stockée T-SQL. Il explique également l'utilisation des données comme entrée et la définition des sorties.    
    
**Conditions préalables** : Pour exécuter du code R dans SQL Server R Services, vous devez être connecté à une instance de SQL Server où R Services est déjà installé.     
    
## Partie 1 : Opérations de base  

Dans les sections suivantes, vous allez découvrir comment étendre la procédure stockée en ajoutant des paramètres et comment configurer les entrées et sorties.   
  
### 1.1 Vérifier si R fonctionne dans SQL Server  

Cette requête utilise la procédure stockée système [sp_execute_external_script](https://msdn.microsoft.com/library/mt604368.aspx), qui permet d’appeler R dans le contexte de SQL Server. Cet exemple transmet une requête SQL comme entrée à R, et R retourne cette trame de données à SQL Server.     
    
1. Dans le menu Démarrer de Windows, recherchez Microsoft SQL Server Management Studio.     
2. Si vous ne le trouvez pas, vous devrez peut-être l’installer : [Télécharger SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).    
3. Dans la boîte de dialogue **Se connecter au serveur**, tapez le nom d’un serveur ou d’une instance où SQL Server R Services est activé. Pour ces exemples, veillez à vous connecter en utilisant un compte capable de créer une base de données, d’exécuter des instructions SELECT et d’afficher des tables.  Ouvrez une nouvelle fenêtre **Requête** et collez cette instruction, juste pour vérifier que tout fonctionne correctement :    
    
    ```sql   
    exec sp_execute_external_script  
      @language =N'R',    
      @script=N'OutputDataSet<-InputDataSet',      
      @input_data_1 =N'select 1 as hello'    
      with result sets (([hello] int not null));    
    go    
    ```   
       
       
  
### <a name="bkmk_SSMSBasics"></a>1.2. Créer des données de test simples  
    
Avant de développer une solution de science des données complexe, il est important de comprendre les différences entre SQL Server et R.    
  
1. Créez une table de données temporaire en exécutant l’instruction T-SQL suivante.     
   
    ```sql    
    CREATE TABLE #MyData ([Col1] int not null) ON [PRIMARY]    
    INSERT INTO #MyData   VALUES (1);    
    INSERT INTO #MyData   Values (10);    
    INSERT INTO #MyData   Values (100) ;    
    GO    
    ```    
5. Une fois la table créée, utilisez l’instruction suivante pour interroger la table :  
    ```sql  
    SELECT * from #MyData  
    ```  

**Résultats**  
  
|Col1 |   
|----|   
| 1|   
|10|   
|100|   
  
    
### 1.3. Obtenir les données de test à l’aide de script R    
  
Une fois la table créée, exécutez l’instruction suivante :  
  
  ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' OutputDataSet <- InputDataSet;'    
    , @input_data_1 = N' SELECT *  FROM #MyData;'    
    WITH RESULT SETS (([NewColName] int NOT NULL));
  ```    
    
Elle doit retourner les mêmes valeurs, mais avec un nouveau nom de colonne.  
  
**Remarques**    
- Le paramètre *@language* définit l’extension de langage à appeler, dans le cas présent, R.    
- Dans le paramètre *@script*, vous définissez les commandes à passer au runtime R comme texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar**, puis appeler la variable.    
- La ligne `N'OutputDataSet <- InputDataSet;'` transmet à R les données d’entrée contenues dans le nom de variable par défaut **InputDataSet**, puis revient aux résultats sans autre opération. Notez que R respecte la casse. Veillez donc à respecter la casse des noms de variables d’entrée et de sortie, sinon une erreur sera déclenchée.    
   
    
Pour spécifier une autre variable d’entrée ou de sortie, utilisez le paramètre *@input_data_1_name* et tapez un identificateur SQL valide. Dans l’exemple suivant, les noms des variables de sortie et d'entrée ont été remplacés respectivement par *SQLOut* et *SQLIn* :    
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' SQLOut <- SQLIn;'    
    , @input_data_1 = N' SELECT 12 as Col;'    
    , @input_data_1_name  = N'SQLIn'    
    , @output_data_1_name =  N'SQLOut'    
    WITH RESULT SETS (([NewColName] int NOT NULL));    
```    
    
**Remarques**    
- Les paramètres obligatoires *@input_data_1* et *@output_data_1* doivent être spécifiés en premier, pour pouvoir utiliser les paramètres facultatifs *@input_data_1_name* et *@output_data_1_name*.    
- SQL et R ne prennent pas en charge les mêmes types de données. Ainsi, des conversions de types ont très souvent lieu lors de l’envoi de données de SQL Server vers R, et vice versa. Pour plus d’informations, consultez [Utilisation des types de données R](../../advanced-analytics/r-services/working-with-r-data-types.md).    
- Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres datasets à partir de votre code R et retourner des sorties d’autres types en plus du dataset. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats.      
- Le schéma du dataset retourné (R data.frame) est défini par l’instruction `WITH RESULT SETS`. Essayez de l’omettre et observez ce qui se produit.    
- Les résultats sous forme de tableau sont retournés dans le volet **Valeurs**. Les messages retournés par le runtime R sont fournis dans le volet **Messages**.     
  
### 1.4 Générer des résultats à l’aide de R    
    
Vous pouvez également générer des valeurs en utilisant le script R et en laissant vide la chaîne de requête d’entrée dans _@input_data_1_. Vous pouvez également utiliser une instruction SQL SELECT valide comme espace réservé, mais vous ne pouvez pas utiliser les résultats SQL dans le script R.    
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' mytextvariable <- c("hello", " ", "world");    
                         OutputDataSet <- as.data.frame(mytextvariable);'    
    , @input_data_1 = N' SELECT 1 as Temp1'    
    WITH RESULT SETS (([col] char(20) NOT NULL));    
```    
    
**Résultats**    
    
    
 |*col* |    
 |-----|    
 |*hello*|    
 |     |    
 |*world*|    
    

Maintenant, essayez une autre version de l’exemple Hello World fourni ci-dessus.     
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'    
    , @input_data_1 = N'  '    
    WITH RESULT SETS (([col1] varchar(20) , [col2] char(1), [col3] varchar(20) ));    
```    
    
    
**Résultats**    
    
    
 |*col1* | *col2* | *col3*|    
 |-------|-------|-------    
 |*hello*|  |*world*|    
    
Notez que les deux instructions créent un vecteur à trois valeurs, mais que le deuxième exemple retourne trois colonnes avec une seule ligne, tandis que la première renvoie une seule colonne avec trois lignes. Pourquoi ?
    
Parce que R offre plusieurs manières d’utiliser des colonnes de valeurs : des vecteurs, des matrices, des tableaux et des listes. Ces opérations, même si elles sont puissantes et flexibles, ne sont pas toujours conformes aux attentes des développeurs SQL.  Certaines fonctions R effectuent des conversions implicites d’objets de données dans des listes et des matrices.

> [!TIP] 
> 
> Vérifiez toujours vos résultats et déterminez le nombre de colonnes de données que retournera votre code R, et quels seront les types de données.    
>     
> Le résultat du script R qui apparaît dans la procédure stockée doit être un **data.frame**, quelles que soient les structures de données qu'utilise votre code R (matrices, vecteurs, etc.).      
  
  
## Partie 2 : Conversion de données et autres problèmes  
  
Cette section présente certains problèmes qui peuvent se produire pendant l’exécution de votre code R dans SQL Server.  
  
+ Types de données : comprendre les options de transtypage et de conversion, ainsi que les conversions implicites.  
+ Jeux de résultats tabulaires : anticiper la méthode appliquée par R pour modifier les colonnes et les lignes de données.    
  
### 2.1 Forçage de type de données implicite  
    
R et SQL Server n’utilisent pas les mêmes types de données. Vous devez donc connaître les restrictions qui existent quand vous déplacez des données entre R et la base de données. Les exemples suivants illustrent certains de ces problèmes courants.   
    
    
1. Exécutez l’instruction suivante pour effectuer une multiplication de matrice à l’aide de R. Dans ce script, la colonne contenant trois valeurs est convertie en une matrice à colonne unique.  Ensuite, R convertit implicitement la deuxième variable, `y`, en matrice à une seule colonne pour que les deux arguments soient conformes.  
    
    ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
      , @script = N'    
        x <- as.matrix(InputDataSet);    
        y <- array(12:15);    
      OutputDataSet <- as.data.frame(x %*% y);'    
     , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
      WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));    
    ```    
**Résultats**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|
 
  
      
2. Maintenant, exécutez le script suivant qui est similaire au précédent, et observez ce qui se passe quand vous modifiez la longueur du tableau. 
   
    ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
      , @script = N'    
        x <- as.matrix(InputDataSet);    
        y <- array(12:14);    
      OutputDataSet <- as.data.frame(y %*% x);'    
      , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
      WITH RESULT SETS (([Col1] int ));    
    ```    

**Résultats**    
    
|Col1|
|---|    
|1542|    
  
  Cette fois-ci, R retourne une seule valeur comme résultat. Ce résultat est valide, car les deux arguments sont des vecteurs de la même longueur. Ainsi, R retourne le produit interne sous forme de matrice.    
    
   
  
### 2.2 Fusionner ou multiplier des colonnes de longueur différente    
    
  
Le script suivant illustre certains comportements de R, qui peuvent ne pas répondre aux attentes du développeur de bases de données.   
  
Le script définit un nouveau tableau numérique de longueur 6 et le stocke dans la variable R `df1`. Le tableau numérique est ensuite combiné aux entiers de la table #MyData, qui contient trois valeurs, pour créer une trame de données, `df2`.   
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N'    
               df1 <- as.data.frame( array(1:6) );    
               df2 <- as.data.frame( c( InputDataSet , df1 ));    
               OutputDataSet <- df2'    
    , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));    
```    
    
**Résultats**    
    
|*Col2*|*Col3*|    
|----|----|    
| 1| 1|    
|10|2|    
|100|3|    
| 1|4|    
|10|5|    
|100|6|    
    
Il existe de nombreuses fonctions en R qui créent une sortie sous forme de tableau, mais qui effectuent des opérations très différentes sur les valeurs en fonction de l’objet de données R. Étant donné que cette procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] exige que les entrées et sorties soient passées en tant que data.frame, vous utiliserez fréquemment des fonctions pour convertir des colonnes et des lignes vers et à partir de trames de données.    
    
Si vous avez un doute concernant l’objet de données R utilisé, ajoutez la fonction `str()` R ou l’une des fonctions d’identification (`is.matrix`, `is.vector`, etc.) pour examiner les résultats et obtenir le schéma et les types de valeurs réels.    
  
  
Pour plus d’informations, consultez cet article de Hadley Wickham sur les [structures de données R](http://adv-r.had.co.nz/Data-structures.html).    
    
### 2.3 Identifier les types de données et vérifier les schémas   
Vous constatez qu’il est important de savoir exactement combien de colonnes seront retournées à partir de votre code R, et ce que sera le type de données de chaque colonne.     
    
  
Vous pouvez utiliser la fonction `str()` dans votre script R pour que le schéma de données de l’objet R soit retourné sous forme de message d’information dans . 

Par exemple, l’instruction suivante retourne le schéma de la table #MyData.    
        
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' str(InputDataSet);'    
    , @input_data_1 = N' SELECT *  FROM #MyData;'    
      WITH RESULT SETS undefined;    
```    
    
    
**Résultats**    
    
*Message(s) STDOUT provenant du script externe :*    
*'data.frame': 3 obs. of 1 variable:*    
*Message(s) STDOUT provenant du script externe :*    
*$ Col1: int 1   10   100*    
    
  
  
### 2.4 Effectuer un transtypage ou une conversion de colonnes   
  
Quand vous envoyez des données de SQL Server vers R, vous devez fréquemment effectuer des transtypages ou des conversions de données pour être sûr qu’elles peuvent être gérées correctement.    
  
Quand vous utilisez une requête SQL comme entrée de code R, plusieurs transformations de données ont lieu :    
- SQL Server transfère les données de la requête au processus R géré par le service Launchpad, et les convertit en représentation interne.    
- Le runtime R charge les données dans une variable data.frame et effectue ses propres opérations sur les données.    
- Le moteur de base de données retourne les données à Management Studio ou à un autre client à l’aide des types de données SQL Server.  
    
1. Exécutez la requête suivante sur l’entrepôt de données AdventureWorksDW. La requête de données d’entrée définit une table de données de ventes à utiliser pour créer une prévision.   
  
    ```sql    
    execute sp_execute_external_script    
       @language = N'R'    
      , @script = N' str(InputDataSet);'    
      , @input_data_1 = N'
           SELECT ReportingDate    
         , CAST(ModelRegion as varchar(50)) as ProductSeries    
         , Amount    
           FROM [AdventureworksDW2016CTP3].[dbo].[vTimeSeries]     
           WHERE [ModelRegion] = ''M200 Europe''    
           ORDER BY ReportingDate ASC ;'    
        WITH RESULT SETS undefined;    
    ```    
  
2. Examinez maintenant les résultats de la fonction `str` pour voir comment R a géré les données d’entrée.
      
**Résultats**    
    
  *Message(s) STDOUT provenant du script externe : 'data.frame':    37 obs. of  3 variables:*    
  *Message(s) STDOUT provenant du script externe : $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"*    
  *Message(s) STDOUT provenant du script externe : $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1 ...*    
  *Message(s) STDOUT provenant du script externe : $ Amount       : num  3400 16925 20350 16950 16950*    
    
    
**Remarques**    
    
- Certains types de données SQL Server ne sont pas pris en charge par R. Ainsi, vous devez spécifier les colonnes individuellement, puis effectuer un transtypage de certaines colonnes pour éviter les erreurs.    
- Le prédicat de chaîne dans la clause WHERE doit être placé entre deux ensembles de guillemets simples.    
- La colonne datetime a été retournée comme type de données R **POSIXct**.    
- La colonne [ProductSeries] a été identifiée (correctement) comme un **factor**.    
     
  
### 2.5 Utiliser plusieurs entrées   
Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre. En revanche, vous pouvez appeler d’autres datasets à partir de votre code R, à l’aide de RODBC.     
  
Par exemple, l’exemple suivant effectue un appel au package RODBC, en spécifiant les données dans une instruction SELECT.    
    
```sql    
    @script = N' 
       <other R code here>;    
       library(RODBC);    
       connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");        dbhandle <- odbcDriverConnect(connStr)    
       OutputDataSet <- sqlQuery(dbhandle, "SELECT * from <table_name>");    
       <more R code combining the data>'    
```

Nous recommandons d’utiliser RODBC pour obtenir des jeux de données non volumineux, tels que des recherches ou des listes de facteurs, et d’utiliser le paramètre @input_data pour obtenir des jeux de données volumineux, tels que ceux utilisés pour l’apprentissage d’un modèle dans SQL Server. 


### 2.6 Générer plusieurs sorties

Dans SQL Server 2016, la sortie de R à partir de la procédure stockée sp_execute_external_script est limitée à un dataset ou un data.frame unique. (Cette limitation sera peut-être supprimée ultérieurement.)   
Toutefois, vous pouvez retourner des sorties d’autres types en plus du dataset. Par exemple, vous pouvez former un modèle en utilisant un dataset unique comme entrée, mais retourner un tableau de statistiques comme sortie, plus le modèle formé en tant qu’objet.    
    
Vous pouvez aussi ajouter le mot clé `OUTPUT` à n’importe quel paramètre d’entrée pour qu’il soit retourné avec les résultats.   
    
### 2.7 Traitement parallèle    
    
Si vous travaillez avec un grand jeu de données et que la requête SQL qui obtient vos données peut générer un plan de requête parallèle, vous pouvez exécuter un script R en parallèle en affectant la valeur 1 au paramètre *@parallel*. Ceci est généralement utile quand vous calculez le score d’un grand jeu de résultats. Si vous utilisez cette option, vous devez spécifier le schéma des résultats de sortie à l’avance à l’aide de WITH RESULT SETS.    
    
Toutefois, ce paramètre n’aura aucun effet si vous avez besoin de former un modèle qui utilise toutes les lignes. Dans ce cas, nous vous recommandons d’utiliser les packages **ScaleR**. Ces packages peuvent distribuer le traitement automatiquement sans que vous ayez à spécifier *@parallel =1* dans l’appel à sp_execute_external_script.    
    
      
  
## Partie 3. Encapsulation des fonctions R dans les procédures stockées  
  
R fournit de nombreuses fonctions statistiques avancées qui peuvent nécessiter du code compliqué à reproduire à l’aide de T-SQL.  Toutefois, avec R Services, vous pouvez également exécuter des scripts utilitaires R dans une procédure stockée pour prendre en charge les tâches suivantes :   
    
- Appliquer les fonctions mathématiques et statistiques de R à des données SQL Server    
    
- Créer des fonctions table ou des fonctions scalaires qui utilisent du code R    
     

 En règle générale, vous devez encapsuler les appels à ces fonctions R dans des procédures stockées pour faciliter la transmission des paramètres. Pour illustrer ce processus, la même fonction est fournie dans le code R, dans un appel de procédure stockée ad hoc à sp_execute_external_script et dans une procédure stockée que vous pouvez utiliser pour paramétrer la fonction R.
 
      
### 3.1 Générer des nombres aléatoires  
  
L’instruction suivante utilise l’une des fonctions R du package `stats`, qui est chargé par défaut quand R Services est installé. La fonction `rnorm` illustrée ici génère 20 nombres aléatoires avec une distribution normale, avec une moyenne égale à 100.    

Voici le code R qui effectue le travail.

```r
as.data.frame(rnorm(20, mean = 100));
```

Cette instruction appelle la fonction depuis T-SQL et renvoie les résultats vers SQL Server.  
   
```sql    
EXEC sp_execute_external_script    
      @language = N'R'    
    , @script = N' 
         OutputDataSet <- as.data.frame(rnorm(20, mean = 100));'    
    , @input_data_1 = N'   ;'    
      WITH RESULT SETS (([Density] float NOT NULL));    
```    

Ensuite, vous encapsulez la procédure stockée dans une autre procédure stockée pour faciliter la transmission des paramètres. Vous devez définir chacun des paramètres d’entrée dans l’argument _@params_ et mapper chaque paramètre vers le paramètre R correspondant à son nom.

```sql
CREATE PROCEDURE MyRNorm (@mynorm int, @mymean int)
AS
    EXEC sp_execute_external_script    
      @language = N'R'    
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynorm, mymean));'    
    , @input_data_1 = N'   ;' 
    , @params = N' @mynorm int, @mymean int'  
    , @mynorm = @mynorm
    , @mymean = @mymean
    WITH RESULT SETS (([Density] float NOT NULL));    
```

Appelez la nouvelle procédure stockée, puis passez les valeurs.

```sql
exec MyRNorm @mynorm = 20,@mymean = 100
```  
    
### 3.2 Autres utilisations des fonctions utilitaires R  
  
Cet exemple appelle l’un des packages d’utilitaire R et utilise sa fonction `memory.limit()` pour obtenir la mémoire de l’environnement actuel. Le package `utils` est installé mais pas chargé par défaut.    
    
```sql    
execute sp_execute_external_script    
      @language = N'R'    
    , @script = N'    
        library(utils);    
        mymemory <- memory.limit();    
        OutputDataSet <- as.data.frame(mymemory);'    
    , @input_data_1 = N' ;'    
     WITH RESULT SETS (([Col1] int not null));    
```    

L’exemple suivant obtient la longueur maximale d’entiers pris en charge sur l’ordinateur actuel à l’aide de la fonction R .Machine, puis affiche le résultat dans la console.

```R
localmax <- .Machine$integer.max;
localmax;
```

```sql
execute sp_execute_external_script
  @language = N'R'
  , @script = N'
      localmax <- .Machine$integer.max;
      OutputDataSet <- as.data.frame(localmax);'
  , @input_data_1 = N'select [Col1]  from #MyData;'
  WITH RESULT SETS (([MaxIntValue] int not null));
```     
    
Toutefois, R n’est pas toujours plus efficace. Dans SQL Server, les opérations basées sur des jeux peuvent être beaucoup plus efficaces pour certaines tâches que les spécialistes des données effectuent traditionnellement dans R. Pour obtenir un exemple de comparaison de fonctions R et T-SQL personnalisées, consultez [Procédure pas à pas pour une solution complète de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md). 

Pour chaque cas, évaluez s’il est plus judicieux d’effectuer une opération donnée à l’aide de R, de T-SQL ou d’un autre outil.    
    
    
    
### Ressources supplémentaires    
    
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md) : cette procédure pas à pas illustre des tâches courantes de science des données.    
[Solution complète de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md) : cette procédure pas à pas illustre un processus de développement et de déploiement qui compare les approches SQL et R.       
[Analytique avancée pour les développeurs SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md) : illustre l’opérationnalisation de modèle complète.     
    
    
    
    
