---
title: sp_execute_external_script (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs: TSQL
helpviewer_keywords: sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d437e6e8d86aa648d9c6ef11a8ca04297cafbaf3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Exécute le script fourni en tant qu’argument à un emplacement externe. Le script doit être écrite dans un langage pris en charge et inscrit. L’arborescence de la requête est contrôlé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les utilisateurs ne peuvent pas effectuer des opérations arbitraires sur la requête. Pour exécuter **sp_execute_external_script**, vous devez tout d’abord activer les scripts externes à l’aide de la `sp_configure 'external scripts enabled', 1;` instruction.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_execute_external_script   
    @language = N'language,   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]   
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```  
  
## <a name="arguments"></a>Arguments  
 @language= N'*langage*'  
 Indique le langage de script. *langage* est **sysname**.  

 Les valeurs valides sont `Python` ou `R`. 
  
 @script= N'*script*'  
 Script de langage externe spécifié comme une entrée de littéral ou une variable. *script* est **nvarchar (max)**.  
  
 [ @input_data_1_name = N'*input_data_1_name*']  
 Spécifie le nom de la variable utilisée pour représenter la requête définie par @input_data_1. Le type de données de la variable de script externe dépend de la langue. En cas de R, la variable d’entrée est une trame de données. Dans le cas de Python, l’entrée doit être sous forme de tableau. *input_data_1_name* est **sysname**.  
  
 Valeur par défaut est « InputDataSet ».  
  
 [ @input_data_1 = N'*input_data_1*']  
 Spécifie les données d’entrée utilisées par le script externe sous la forme d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] requête. *input_data_1* est **nvarchar (max)**.  
  
 [ @output_data_1_name = N'*output_data_1_name*']  
 Spécifie le nom de la variable dans le script externe qui contient les données à retourner à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la fin de l’appel de procédure stockée. Le type de données de la variable de script externe dépend de la langue. Dans le cas de R, la sortie doit être une trame de données. Dans le cas de Python, la sortie doit être une trame de données pandas. *output_data_1_name* est **sysname**.  
  
 Valeur par défaut est « OutputDataSet ».  
  
 [ @parallel = 0 | 1 ]  
 Activer l’exécution parallèle de scripts R en définissant le `@parallel` paramètre 1. La valeur par défaut pour ce paramètre est 0 (Aucun parallélisme).  
  
 Pour les scripts R qui n’utilisent pas les fonctions RevoScaleR, à l’aide de le `@parallel` paramètre peut être utile pour le traitement des jeux de données volumineux, en supposant que le script peut être parallélisé simplement. Par exemple, lors de l’utilisation de R `predict` fonction avec un modèle pour générer de nouvelles prédictions, définissez `@parallel = 1` comme une indication au moteur de requête. Si la requête peut être parallélisée, les lignes sont distribuées en fonction de la **MAXDOP** paramètre.  
  
 Si `@parallel = 1` et la sortie est en cours de diffusion directement à l’ordinateur client, puis le `WITH RESULTS SETS` clause est requise et un schéma de sortie doit être spécifié.  
  
 Pour les scripts R qui utilisent les fonctions RevoScaleR, le traitement parallèle est géré automatiquement et vous ne devez pas spécifier `@parallel = 1` à la **sp_execute_external_script** appeler.  
  
 [ @params = N' *@parameter_name data_type* [OUT | SORTIE] [,.. .n]']  
 Une liste de déclarations de paramètre d’entrée qui sont utilisées dans le script externe.  
  
 [ @parameter1 = '*value1*' [OUT | SORTIE] [,.. .n]]  
 Une liste de valeurs pour les paramètres d’entrée utilisés par le script externe.  


## <a name="remarks"></a>Notes  
 Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge, tels que R. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comprend un composant de serveur installé avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi qu’un ensemble d’outils de station de travail et de bibliothèques de connectivité qui connectent les données scientifiques à l’environnement hautes performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Installer R Services (de-de base de données) au cours de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation pour permettre l’exécution de scripts R. Pour plus d’informations, consultez [configurer SQL Server R Services &#40; dans la base de données &#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
 Vous pouvez contrôler les ressources utilisées par un script externe en configurant un pool de ressources externes. Pour plus d’informations, consultez [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Plus d’informations sur la charge de travail peuvent être obtenues à partir des affichages de catalogue du gouverneur de ressources, la DMV et des compteurs. Pour plus d’informations, consultez [affichages catalogue du gouverneur de ressources &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Du gouverneur de ressources liées de vues de gestion dynamique &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), et [objet de Scripts SQL Server, externe](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

L’exécution du script d’analyse à l’aide [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) et [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

 Par défaut, les jeux de résultats retournés par cette procédure stockée s’affichent avec des colonnes sans nom. Noms de colonnes utilisés dans un script locaux de l’environnement de script et ne sont pas répercutées dans le jeu de résultats obtenus. Pour nommer des colonnes du jeu de résultats, utilisez le `WITH RESULTS SET` clause de [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md).
  
 En plus de retourner un jeu de résultats, vous pouvez retourner des valeurs scalaires à partir du script R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des paramètres de sortie. L’exemple suivant illustre l’utilisation du paramètre de sortie :  
  
```  
DECLARE @model varbinary(max);  
EXEC sp_execute_external_script  
        @language = N'R'  
        , @script = N'  
    # build classification model to predict tipped or not  
    logitObj <- glm(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource, family = binomial(link=logit));  
  
    # First, serialize a model and put it into a database table  
    modelbin <- serialize(logitObj, NULL);  
    '  
        , @input_data_1 = N'  
SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance  
  FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)  
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d  
'  
        , @input_data_1_name = N'featureDataSource'  
        , @params = N'@modelbin varbinary(max) OUTPUT'  
        , @modelbin = @model OUTPUT;  
```  


## <a name="streaming-execution-for-r-script"></a>Diffusion en continu de l’exécution pour le script R  
 Diffusion en continu de l’exécution du script R est pris en charge en spécifiant `@r_rowsPerRead int parameter` dans `@params` collection.  Diffusion en continu permet de scripts R fonctionnent avec des données qui ne tient pas dans la mémoire. Par exemple, s’il existe des milliards de lignes score à l’aide de prédire fonction nouvelle `@r_rowsPerRead` paramètre peut être utilisé pour fractionner l’exécution dans un flux à la fois. Étant donné que ce paramètre contrôle le nombre de lignes qui sont envoyés aux processus R, il peut être également utilisé pour limiter le nombre de lignes en cours de lecture à la fois. Cela peut être utile pour atténuer les problèmes de performances de serveur si, par exemple, un grand modèle apprentissage. Notez que ce paramètre peut uniquement être utilisé dans les cas où la sortie du script R ne dépend pas la lecture ou en examinant l’ensemble de lignes.  
  
 Les deux le `@r_rowsPerRead` paramètre de diffusion en continu et la `@parallel` argument doit être considérée comme indicateurs. Pour l’indicateur à appliquer, il doit être possible de générer un plan de requête SQL qui inclut un traitement parallèle. Si ce n’est pas possible, le traitement parallèle ne peut pas être activé.  
  
> [!NOTE]  
>  Traitement parallèle et diffusion en continu sont pris en charge uniquement dans Enterprise Edition. Vous pouvez inclure les paramètres dans vos requêtes dans l’Édition Standard sans déclencher d’erreur, mais les paramètres n’ont aucun effet et les scripts R exécutés dans un processus unique.  
  
## <a name="restrictions"></a>Restrictions  
 **Types de données :** les types de données suivants ne sont pas pris en charge lorsqu’il est utilisé dans la requête d’entrée ou des paramètres de `sp_execute_external_script` procédure et retour d’une erreur de type non pris en charge.  
  
 Pour résoudre ce problème, **CAST** la colonne ou la valeur à un type pris en charge dans [!INCLUDE[tsql](../../includes/tsql-md.md)] et l’envoyer à R.  
  
-   **cursor**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **heure**  
  
-   **sql_variant**  
  
-   **texte**, **image**  
  
-   **xml**  
  
-   **hierarchyid**, **geometry**, **geography**  
  
-   Types CLR définis par l’utilisateur  
  
 **DateTime** valeurs d’entrée sont converties en NA sur le côté de R pour les valeurs qui ne répondent pas la plage autorisée des valeurs dans R. cela est nécessaire car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet une plus grande plage de valeurs qu’est pris en charge dans le langage R.  
  
 Les valeurs float (par exemple, + Inf, -Inf, NaN) ne sont pas pris en charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] même si les deux langages utilisent la norme IEEE 754. Comportement actuel envoie uniquement les valeurs à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] directement comme un résultat sqlclient dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] lève l’erreur. Ces valeurs sont converties en **NULL**.  
  
 N’importe quel jeu de résultats de R ne peut pas être mappé à un [!INCLUDE[tsql](../../includes/tsql-md.md)] type de données, est sortie comme NULL.  
  
## <a name="permissions"></a>Permissions  
 Requiert **EXECUTE ANY EXTERNAL SCRIPT** autorisation de base de données.  
  
## <a name="examples"></a>Exemples  
 Cette section contient des exemples d’utilisation de la procédure stockée à exécuter des scripts R à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
### <a name="a-return-a-data-set-from-r-to-sql-server"></a>A. Retourne un jeu de données à partir de R vers SQL Server  
 L’exemple suivant crée une procédure stockée qui utilise **sp_execute_external_script** pour retourner un jeu de données iris de R vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
DROP PROC IF EXISTS get_iris_dataset;  
go  
CREATE PROC get_iris_dataset  
AS  
BEGIN  
 EXEC   sp_execute_external_script  
       @language = N'R'  
     , @script = N'iris_data <- iris;'  
     , @input_data_1 = N''  
     , @output_data_1_name = N'iris_data'  
     WITH RESULT SETS (("Sepal.Length" float not null,   
           "Sepal.Width" float not null,  
        "Petal.Length" float not null,   
        "Petal.Width" float not null, "Species" varchar(100)));  
END;  
go  
```  
  
### <a name="b-generate-a-model-based-on-data-from-sql-server"></a>B. Générer un modèle basé sur les données de SQL Server  
 L’exemple suivant crée une procédure stockée qui utilise **sp_execute_external_script** pour générer un modèle iris et de retourner le modèle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Cet exemple requiert l’installation du package e1071. Pour plus d’informations, consultez [installer des Packages R supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).  
  
```  
DROP PROC IF EXISTS generate_iris_model;  
go  
  
CREATE PROC generate_iris_model  
AS  
BEGIN  
 EXEC sp_execute_external_script  
      @language = N'R'  
     , @script = N'  
          library(e1071);  
          irismodel <-naiveBayes(iris_data[,1:4], iris_data[,5]);  
          trained_model <- data.frame(payload = as.raw(serialize(irismodel, connection=NULL)));  
'  
     , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from iris_data'  
     , @input_data_1_name = N'iris_data'  
     , @output_data_1_name = N'trained_model'  
    WITH RESULT SETS ((model varbinary(max)));  
END;  
go  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Les Types de données et les bibliothèques de Python](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [Bibliothèques R et les Types de données R](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Problèmes connus pour SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CRÉER une bibliothèque externe &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Option de Configuration de serveur scripts externes activés](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server, objet External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
  
