---
title: sp_execute_external_script (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: ab3bf4f98abaf5f164a3b38f4e09b10acf28b2f4
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532834"
---
# <a name="sp_execute_external_script-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
La procédure stockée **sp_execute_external_script** exécute un script fourni en tant qu’argument d’entrée pour la procédure et est utilisé avec les [Extensions](../../language-extensions/language-extensions-overview.md)de [machine learning services](../../advanced-analytics/index.yml) et de langage. 

Pour Machine Learning Services, [python](../../advanced-analytics/concepts/extension-python.md) et [R](../../advanced-analytics/concepts/extension-r.md) sont des langages pris en charge. Pour les extensions de langage, Java est pris en charge, mais doit être défini avec [Create External Language](../../t-sql/statements/create-external-language-transact-sql.md).

Pour exécuter **sp_execute_external_script**, vous devez d’abord installer les Extensions de machine learning services ou de langage. Pour plus d’informations, consultez [installer SQL Server machine learning services (Python et R) sur Windows](../../advanced-analytics/install/sql-machine-learning-services-windows-install.md) et [Linux](../../linux/sql-server-linux-setup-machine-learning.md), ou [installer les extensions de langage SQL Server sur Windows](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md) et [Linux](../../linux/sql-server-linux-setup-language-extensions.md).
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
La procédure stockée **sp_execute_external_script** exécute un script fourni en tant qu’argument d’entrée pour la procédure et est utilisé avec [Machine Learning Services](../../advanced-analytics/index.yml) sur SQL Server 2017. 

Pour Machine Learning Services, [python](../../advanced-analytics/concepts/extension-python.md) et [R](../../advanced-analytics/concepts/extension-r.md) sont des langages pris en charge. 

Pour exécuter **sp_execute_external_script**, vous devez d’abord installer machine learning services. Pour plus d’informations, consultez [installer SQL Server machine learning services (Python et R) sur Windows](../../advanced-analytics/install/sql-machine-learning-services-windows-install.md).
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
La procédure stockée **sp_execute_external_script** exécute un script fourni en tant qu’argument d’entrée pour la procédure et est utilisé avec [R Services](../../advanced-analytics/r/sql-server-r-services.md) sur SQL Server 2016.

Pour R services, [r](../../advanced-analytics/concepts/extension-r.md) est le langage pris en charge.

Pour exécuter **sp_execute_external_script**, vous devez d’abord installer R services. Pour plus d’informations, consultez [installer SQL Server machine learning services (Python et R) sur Windows](../../advanced-analytics/install/sql-r-services-windows-install.md).
::: moniker-end

 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax"></a>Syntaxe

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]    
    [ , @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
## <a name="syntax-for-2017-and-earlier"></a>Syntaxe pour 2017 et versions antérieures

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end

## <a name="arguments"></a>Arguments
 **\@Language** = N'*Language*'  
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
 Indique le langage de script. *Language* est de **type sysname**. Les valeurs valides sont **R**, **python**et n’importe quel langage défini avec [Create External Language](../../t-sql/statements/create-external-language-transact-sql.md) (par exemple, Java).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
 Indique le langage de script. *Language* est de **type sysname**. Dans SQL Server 2017, les valeurs valides sont **R** et **python**.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
 Indique le langage de script. *Language* est de **type sysname**. Dans SQL Server 2016, la seule valeur valide est **R**.
::: moniker-end

 **\@** script du langage externe*script =* N est spécifié en tant qu’entrée littérale ou variable. le *script* est **de type nvarchar (max)** .  

`[ @input_data_1 =  N'input_data_1' ]` spécifie les données d’entrée utilisées par le script externe sous la forme d’une requête [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le type de données de *input_data_1* est **nvarchar (max)** .

`[ @input_data_1_name = N'input_data_1_name' ]` spécifie le nom de la variable utilisée pour représenter la requête définie par @input_data_1. Le type de données de la variable dans le script externe dépend de la langue. Dans le cas de R, la variable d’entrée est une trame de données. Dans le cas de Python, l’entrée doit être tabulaire. *input_data_1_name* est de **type sysname**.  La valeur par défaut est *InputDataSet*.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]` utilisé pour générer des modèles par partition. Spécifie le nom de la colonne utilisée pour trier le jeu de résultats, par exemple par nom de produit. Le type de données de la variable dans le script externe dépend de la langue. Dans le cas de R, la variable d’entrée est une trame de données. Dans le cas de Python, l’entrée doit être tabulaire.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]` utilisé pour générer des modèles par partition. Spécifie le nom de la colonne utilisée pour segmenter les données, telles que la région géographique ou la date. Le type de données de la variable dans le script externe dépend de la langue. Dans le cas de R, la variable d’entrée est une trame de données. Dans le cas de Python, l’entrée doit être tabulaire. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]` spécifie le nom de la variable dans le script externe qui contient les données à retourner à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la fin de l’appel de la procédure stockée. Le type de données de la variable dans le script externe dépend de la langue. Pour R, la sortie doit être une trame de données. Pour Python, la sortie doit être une trame de données pandas. *output_data_1_name* est de **type sysname**.  La valeur par défaut est *OutputDataSet*.  

`[ @parallel = 0 | 1 ]` permet l’exécution parallèle de scripts R en affectant la valeur 1 au paramètre `@parallel`. La valeur par défaut de ce paramètre est 0 (aucun parallélisme). Si `@parallel = 1` et que la sortie est diffusée directement sur l’ordinateur client, la clause `WITH RESULT SETS` est requise et un schéma de sortie doit être spécifié.  

 + Pour les scripts R qui n’utilisent pas de fonctions RevoScaleR, l’utilisation du paramètre `@parallel` peut être bénéfique pour le traitement de jeux de données volumineux, en supposant que le script peut être parallélisée de façon triviale. Par exemple, lors de l’utilisation de la fonction R `predict` avec un modèle pour générer de nouvelles prédictions, définissez `@parallel = 1` comme indicateur pour le moteur de requête. Si la requête peut être parallélisée, les lignes sont distribuées selon le paramètre **MAXDOP** .  
  
 + Pour les scripts R qui utilisent des fonctions RevoScaleR, le traitement parallèle est géré automatiquement et vous ne devez pas spécifier `@parallel = 1` à l’appel **sp_execute_external_script** .  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]` liste des déclarations de paramètres d’entrée utilisées dans le script externe.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]` liste de valeurs pour les paramètres d’entrée utilisés par le script externe.  

## <a name="remarks"></a>Notes

> [!IMPORTANT]
> L’arborescence de requêtes est contrôlée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les utilisateurs ne peuvent pas effectuer d’opérations arbitraires sur la requête. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge. Les langues prises en charge sont **python** et **R** utilisées avec machine learning services, ainsi que tous les langages définis avec [Create External Language](../../t-sql/statements/create-external-language-transact-sql.md) (par exemple, Java) utilisés avec les extensions de langage.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge. Les langues prises en charge sont **python** et **R** dans SQL Server 2017 machine learning services.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge. La seule langue prise en charge est **r** dans SQL Server les Services r 2016.
::: moniker-end

Par défaut, les jeux de résultats retournés par cette procédure stockée sont générés avec des colonnes sans nom. Les noms de colonne utilisés dans un script sont locaux dans l’environnement de script et ne sont pas reflétés dans le jeu de résultats sorti. Pour nommer les colonnes du jeu de résultats, utilisez la clause `WITH RESULT SET` de [`EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md).

En plus de retourner un jeu de résultats, vous pouvez retourner des valeurs scalaires à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des paramètres de sortie. 
  
Vous pouvez contrôler les ressources utilisées par les scripts externes en configurant un pool de ressources externes. Pour plus d’informations, consultez [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Les informations sur la charge de travail peuvent être obtenues à partir des affichages catalogue du gouverneur de ressources, des DMV et des compteurs. Pour plus d’informations, consultez [Resource Governor les &#40;affichages catalogue&#41;Transact-SQL](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Resource Governor les &#40;vues de gestion&#41;dynamique associées à Transact-SQL](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)et [SQL Server, objet scripts externes](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

### <a name="monitor-script-execution"></a>Surveiller l’exécution du script

Surveiller l’exécution du script à l’aide de [sys. DM _external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) et [sys. DM _external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>Paramètres pour la modélisation de partition

Vous pouvez définir deux paramètres supplémentaires qui activent la modélisation sur des données partitionnées, où les partitions sont basées sur une ou plusieurs colonnes que vous fournissez, qui segmentent naturellement un jeu de données en partitions logiques créées et utilisées uniquement pendant l’exécution du script. Les colonnes contenant des valeurs répétitives pour l’âge, le sexe, la région géographique, la date ou l’heure, sont quelques exemples qui se prêtent à des jeux de données partitionnés.
 
Les deux paramètres sont **input_data_1_partition_by_columns** et **input_data_1_order_by_columns**, où le deuxième paramètre est utilisé pour trier le jeu de résultats. Les paramètres sont passés comme entrées à `sp_execute_external_script` avec le script externe qui s’exécute une fois pour chaque partition. Pour plus d’informations et d’exemples, consultez [Didacticiel : créer des modèles basés sur une partition](https://docs.microsoft.com/sql/advanced-analytics/tutorials/r-tutorial-create-models-per-partition).

Vous pouvez exécuter le script en parallèle en spécifiant `@parallel=1`. Si la requête d’entrée peut être parallélisée, vous devez définir `@parallel=1` dans le cadre de vos arguments pour `sp_execute_external_script`. Par défaut, l’optimiseur de requête fonctionne sous `@parallel=1` sur les tables contenant plus de 256 lignes, mais si vous souhaitez gérer cela explicitement, ce script comprend le paramètre comme une démonstration.

> [!Tip]
> Pour la formation workoads, vous pouvez utiliser `@parallel` avec n’importe quel script d’apprentissage arbitraire, même ceux qui utilisent des algorithmes non-Microsoft-RX. En règle générale, seuls les algorithmes RevoScaleR (avec le préfixe RX) offrent un parallélisme dans les scénarios d’apprentissage dans SQL Server. Mais avec les nouveaux paramètres dans SQL Server vNext, vous pouvez paralléliser un script qui appelle des fonctions qui ne sont pas spécifiquement conçues avec cette fonctionnalité.
::: moniker-end

### <a name="streaming-execution-for-python-and-r-scripts"></a>Exécution de la diffusion en continu pour les scripts Python et R  

La diffusion en continu permet au script Python ou R de travailler avec plus de données que la mémoire ne peut en contenir. Pour contrôler le nombre de lignes transmises pendant la diffusion en continu, spécifiez une valeur entière pour le paramètre, `@r_rowsPerRead` dans la collection `@params`.  Par exemple, si vous effectuez l’apprentissage d’un modèle qui utilise des données très larges, vous pouvez ajuster la valeur pour lire moins de lignes, afin de vous assurer que toutes les lignes peuvent être envoyées dans un segment de données. Vous pouvez également utiliser ce paramètre pour gérer le nombre de lignes lues et traitées en même temps, afin d’atténuer les problèmes de performances du serveur. 
  
Le paramètre `@r_rowsPerRead` pour la diffusion en continu et l’argument `@parallel` doivent être considérés comme des indicateurs. Pour que l’indicateur soit appliqué, il doit être possible de générer un plan de requête SQL qui comprend un traitement parallèle. Si ce n’est pas possible, le traitement parallèle ne peut pas être activé.  
  
> [!NOTE]  
> La diffusion en continu et le traitement parallèle sont pris en charge uniquement dans Enterprise Edition. Vous pouvez inclure les paramètres dans vos requêtes dans l’édition standard sans générer d’erreur, mais les paramètres n’ont aucun effet et les scripts R s’exécutent dans un processus unique.  
  
## <a name="restrictions"></a>Restrictions  

### <a name="data-types"></a>Types de données

Les types de données suivants ne sont pas pris en charge lorsqu’ils sont utilisés dans la requête ou les paramètres d’entrée de la procédure **sp_execute_external_script** , et renvoient une erreur de type non pris en charge.  

En guise de solution de contournement, **effectuez un cast** de la colonne ou de la valeur en un type pris en charge dans [!INCLUDE[tsql](../../includes/tsql-md.md)] avant de l’envoyer au script externe.  
  
-   **cursor**  
  
-   **timestamp**  
  
-   **datetime2**, **DateTimeOffset**, **Time**  
  
-   **sql_variant**  
  
-   **texte**, **image**  
  
-   **xml**  
  
-   **hierarchyid**, **Geometry**, **Geography**  
  
-   Types CLR définis par l’utilisateur

En général, tout jeu de résultats qui ne peut pas être mappé à un type de données [!INCLUDE[tsql](../../includes/tsql-md.md)] est généré en tant que valeur NULL.  

### <a name="restrictions-specific-to-r"></a>Restrictions spécifiques à R

Si l’entrée comprend des valeurs **DateTime** qui ne correspondent pas à la plage de valeurs autorisée dans R, les valeurs sont converties en **na**. Cela est nécessaire, car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise une plus grande plage de valeurs que ce qui est pris en charge dans le langage R.

Les valeurs float (par exemple, `+Inf`, `-Inf`, `NaN`) ne sont pas prises en charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], même si les deux langages utilisent IEEE 754. Le comportement actuel envoie simplement les valeurs à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] directement ; par conséquent, le client SQL de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] génère une erreur. Par conséquent, ces valeurs sont converties en valeurs **null**.

## <a name="permissions"></a>Autorisations

Requiert **l’autorisation exécuter une** base de données de script externe.  

## <a name="examples"></a>Exemples

Cette section contient des exemples de la façon dont cette procédure stockée peut être utilisée pour exécuter des scripts R ou python à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Retourne un jeu de données R SQL Server  

L’exemple suivant crée une procédure stockée qui utilise **sp_execute_external_script** pour retourner le jeu de données Iris inclus avec R à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

```sql
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
GO
```

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>B. Générer un modèle R basé sur les données de SQL Server  

L’exemple suivant crée une procédure stockée qui utilise **sp_execute_external_script** pour générer un modèle d’IRIS et retourner le modèle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

> [!NOTE]
>  Cet exemple nécessite une installation avancée du package e1071. Pour plus d’informations, consultez [installer des packages R supplémentaires sur SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md).

```sql
DROP PROC IF EXISTS generate_iris_model;
GO
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
GO
```

Pour générer un modèle semblable à l’aide de Python, vous devez remplacer l’identificateur de langage `@language=N'R'` par `@language = N'Python'` et apporter les modifications nécessaires à l’argument `@script`. Autrement, tous les paramètres fonctionnent de la même manière que pour R.

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>C. Créer un modèle Python et générer des scores à partir de celui-ci

Cet exemple illustre l’utilisation de sp\_execute\_external\_script pour générer des scores sur un modèle Python simple. 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

-- Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders'

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

# Get data from input query
customer_data = my_input_data

# Define the model
n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Les en-têtes de colonne utilisés dans le code python ne sont pas générés dans SQL Server ; par conséquent, utilisez l’instruction WITH RESULT pour spécifier les noms de colonnes et les types de données que SQL doit utiliser.

Pour calculer les scores, vous pouvez également utiliser la fonction [PREDICT](../../t-sql/queries/predict-transact-sql.md) native, qui est généralement plus rapide car elle évite d’appeler le runtime Python ou R.

## <a name="see-also"></a>Voir aussi

+ [SQL Server Machine Learning Services](../../advanced-analytics/index.yml)
+ [Extensions de langage SQL Server](../../language-extensions/language-extensions-overview.md). 
+ [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
+ [Bibliothèques Python et types de données](../../advanced-analytics/python/python-libraries-and-data-types.md)  
+ [Bibliothèques r et types de données R](../../advanced-analytics/r/r-libraries-and-data-types.md)  
+ [SQL Server R Services](../../advanced-analytics/r/sql-server-r-services.md)   
+ [Problèmes connus pour SQL Server Machine Learning Services](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
+ [CRÉER une bibliothèque &#40;externe Transact-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
+ [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
+ [external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
+ [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
+ [SQL Server, objet External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
