---
title: sp_execute_external_script (Transact-SQL) Microsoft Docs
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
ms.openlocfilehash: 8800df26e505f1fffe25e6f65218481e7a8158f0
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80663016"
---
# <a name="sp_execute_external_script-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
La procédure **stockée sp_execute_external_script** exécute un script fourni comme argument d’entrée à la procédure, et est utilisée avec les [services d’apprentissage automatique](../../machine-learning/index.yml) et les [extensions de langue](../../language-extensions/language-extensions-overview.md). 

Pour les services d’apprentissage automatique, [Python](../../machine-learning/concepts/extension-python.md) et [R](../../machine-learning/concepts/extension-r.md) sont des langues prises en charge. Pour les extensions linguistiques, Java est pris en charge mais doit être défini avec [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md).

Pour exécuter **sp_execute_external_script,** vous devez d’abord installer des services d’apprentissage automatique ou des extensions de langue. Pour plus d’informations, voir [installer SQL Server Machine Learning Services (Python and R) sur Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md) et [Linux](../../linux/sql-server-linux-setup-machine-learning.md), ou [installez SQL Server Language Extensions sur Windows](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md) et [Linux](../../linux/sql-server-linux-setup-language-extensions.md).
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
La **procédure stockée sp_execute_external_script** exécute un script fourni comme argument d’entrée à la procédure, et est utilisée avec Les Services [d’apprentissage automatique](../../machine-learning/index.yml) sur SQL Server 2017. 

Pour les services d’apprentissage automatique, [Python](../../machine-learning/concepts/extension-python.md) et [R](../../machine-learning/concepts/extension-r.md) sont des langues prises en charge. 

Pour exécuter **sp_execute_external_script,** vous devez d’abord installer des services d’apprentissage automatique. Pour plus d’informations, voir [Installer SQL Server Machine Learning Services (Python et R) sur Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md).
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
La **procédure sp_execute_external_script** stockée exécute un script fourni comme argument d’entrée à la procédure, et est utilisé avec R [Services](../../machine-learning/r/sql-server-r-services.md) sur SQL Server 2016.

Pour R Services, [R](../../machine-learning/concepts/extension-r.md) est la langue soutenue.

Pour exécuter **sp_execute_external_script,** vous devez d’abord installer R Services. Pour plus d’informations, voir [Installer SQL Server Machine Learning Services (Python et R) sur Windows](../../machine-learning/install/sql-r-services-windows-install.md).
::: moniker-end

 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

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
## <a name="syntax-for-2017-and-earlier"></a>Syntaxe pour 2017 et plus tôt

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
 langue n '*langue*' ** \@**  
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
 Indique le langage du script. *la langue* est **sysname**. Les valeurs valides sont **R**, **Python**, et toute langue définie avec [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) (par exemple, Java).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
 Indique le langage du script. *la langue* est **sysname**. Dans SQL Server 2017, les valeurs valides sont **R** et **Python**.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
 Indique le langage du script. *la langue* est **sysname**. Dans SQL Server 2016, la seule valeur valable est **R**.
::: moniker-end

 script n'*script*' Script de langage externe spécifié comme une entrée littérale ou variable. ** \@** *script* est **nvarchar(max)**.  

`[ @input_data_1 =  N'input_data_1' ]`Spécifie les données d’entrée utilisées [!INCLUDE[tsql](../../includes/tsql-md.md)] par le script externe sous la forme d’une requête. Le type de données de *input_data_1* est **nvarchar(max)**.

`[ @input_data_1_name = N'input_data_1_name' ]`Spécifie le nom de la variable @input_data_1utilisée pour représenter la requête définie par . Le type de données de la variable dans le script externe dépend de la langue. En cas de R, la variable d’entrée est un cadre de données. Dans le cas de Python, l’entrée doit être tabulaire. *input_data_1_name* est **sysname**.  La valeur par défaut est *InputDataSet*.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]`Utilisé pour construire des modèles par partition. Spécifie le nom de la colonne utilisée pour commander l’ensemble de résultats, par exemple par nom de produit. Le type de données de la variable dans le script externe dépend de la langue. En cas de R, la variable d’entrée est un cadre de données. Dans le cas de Python, l’entrée doit être tabulaire.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]`Utilisé pour construire des modèles par partition. Spécifie le nom de la colonne utilisée pour segmenter les données, telles que la région géographique ou la date. Le type de données de la variable dans le script externe dépend de la langue. En cas de R, la variable d’entrée est un cadre de données. Dans le cas de Python, l’entrée doit être tabulaire. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]`Spécifie le nom de la variable dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script externe qui contient les données à retourner à la fin de l’appel de procédure stocké. Le type de données de la variable dans le script externe dépend de la langue. Pour R, la sortie doit être un cadre de données. Pour Python, la sortie doit être un cadre de données pandas. *output_data_1_name* est **sysname**.  La valeur par défaut est *OutputDataSet*.  

`[ @parallel = 0 | 1 ]`Activez l’exécution parallèle des `@parallel` scripts R en définissant le paramètre à 1. La valeur par défaut de ce paramètre est de 0 (pas de parallélisme). Si `@parallel = 1` et la sortie est diffusée directement à `WITH RESULT SETS` la machine cliente, alors la clause est nécessaire et un schéma de sortie doit être spécifié.  

 + Pour les scripts R qui n’utilisent pas `@parallel` les fonctions RevoScaleR, l’utilisation du paramètre peut être bénéfique pour le traitement de grands jeux de données, en supposant que le script peut être banalement parallélisé. Par exemple, lors `predict` de l’utilisation de la `@parallel = 1` fonction R avec un modèle pour générer de nouvelles prédictions, définissez comme un indice pour le moteur de requête. Si la requête peut être parallélisée, les lignes sont distribuées selon le paramètre **MAXDOP.**  
  
 + Pour les scripts R qui utilisent les fonctions RevoScaleR, `@parallel = 1` le traitement parallèle est géré automatiquement et vous ne devez pas spécifier à **l’sp_execute_external_script** appel.  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]`Une liste des déclarations de paramètres d’entrée qui sont utilisées dans le script externe.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]`Une liste de valeurs pour les paramètres d’entrée utilisés par le script externe.  

## <a name="remarks"></a>Notes

> [!IMPORTANT]
> L’arbre de requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est contrôlé par et les utilisateurs ne peuvent pas effectuer des opérations arbitraires sur la requête. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans une langue prise en charge. Les langues prises en charge sont **Python** et **R** utilisées avec les services d’apprentissage automatique, et toute langue définie avec [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) (par exemple, Java) utilisée avec les extensions linguistiques.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans une langue prise en charge. Les langues prises en charge sont **Python** et **R** dans SQL Server 2017 Machine Learning Services.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans une langue prise en charge. La seule langue prise en charge est **R** dans SQL Server 2016 R Services.
::: moniker-end

Par défaut, les ensembles de résultats retournés par cette procédure stockée sont des sorties avec des colonnes anonymes. Les noms de colonnes utilisés dans un script sont locaux à l’environnement de script et ne sont pas reflétés dans l’ensemble de résultats de sortie. Pour nommer les colonnes `WITH RESULT SET` de [`EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)jeu de résultat, utilisez la clause de .

En plus de retourner un ensemble de résultats, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous pouvez retourner les valeurs scalaires en utilisant des paramètres OUTPUT. 
  
Vous pouvez contrôler les ressources utilisées par les scripts externes en configurant un pool de ressources externes. Pour plus d’informations, voir [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Les renseignements sur la charge de travail peuvent être obtenus à partir des vues du catalogue des gouverneurs des ressources, des DMV et des compteurs. Pour plus d’informations, voir [Resource Governor Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), Resource Governor Related Dynamic Management Views &#40;[Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), et [SQL Server, External Scripts Object](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

### <a name="monitor-script-execution"></a>Surveiller l’exécution du script

Surveiller l’exécution du script à [l’aide de sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) et [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>Paramètres pour la modélisation de partition

Vous pouvez définir deux paramètres supplémentaires qui permettent la modélisation sur les données partitionnées, où les partitions sont basées sur une ou plusieurs colonnes que vous fournissez qui segmentent naturellement un ensemble de données en partitions logiques créées et utilisées uniquement lors de l’exécution du script. Les colonnes contenant des valeurs répétitives pour l’âge, le sexe, la région géographique, la date ou l’heure, sont quelques exemples qui se prêtent à des ensembles de données partitionnés.
 
Les deux paramètres sont **input_data_1_partition_by_columns** et **input_data_1_order_by_columns**, où le deuxième paramètre est utilisé pour commander l’ensemble de résultats. Les paramètres sont passés sous `sp_execute_external_script` forme d’entrées avec le script externe exécutant une fois pour chaque partition. Pour plus d’informations et d’exemples, voir [Tutorial: Create partition-based models](https://docs.microsoft.com/sql/machine-learning/tutorials/r-tutorial-create-models-per-partition).

Vous pouvez exécuter le script `@parallel=1`en parallèle en spécifiant . Si la requête d’entrée peut être `@parallel=1` parallélisée, `sp_execute_external_script`vous devez définir dans le cadre de vos arguments à . Par défaut, l’optimiseur `@parallel=1` de requête fonctionne sous les tables ayant plus de 256 lignes, mais si vous voulez gérer cela explicitement, ce script inclut le paramètre comme une démonstration.

> [!Tip]
> Pour les charges de travail d’entraînement, vous pouvez utiliser `@parallel` avec n’importe quel script d’entraînement arbitraire, même ceux qui utilisent des algorithmes non-Microsoft-rx. En règle générale, seuls les algorithmes RevoScaleR (avec le préfixe rx) offrent un parallélisme dans les scénarios d’entraînement dans SQL Server. Mais avec les nouveaux paramètres dans SQL Server vNext, vous pouvez faire le parallèle avec un script qui appelle des fonctions non spécifiquement conçues avec cette capacité.
::: moniker-end

### <a name="streaming-execution-for-python-and-r-scripts"></a>Exécution en continu pour les scripts Python et R  

Le streaming permet au script Python ou R de fonctionner avec plus de données que ce qui peut tenir dans la mémoire. Pour contrôler le nombre de lignes passées pendant le streaming, `@r_rowsPerRead` spécifiez une valeur integer pour le paramètre, dans la `@params` collection.  Par exemple, si vous formez un modèle qui utilise des données très larges, vous pouvez ajuster la valeur pour lire moins de lignes, pour vous assurer que toutes les lignes peuvent être envoyées dans un morceau de données. Vous pouvez également utiliser ce paramètre pour gérer le nombre de lignes lues et traitées en même temps, afin d’atténuer les problèmes de performances du serveur. 
  
Le `@r_rowsPerRead` paramètre pour `@parallel` le streaming et l’argument doivent être considérés comme des indices. Pour que l’indice soit appliqué, il doit être possible de générer un plan de requête SQL qui comprend le traitement parallèle. Si cela n’est pas possible, le traitement parallèle ne peut pas être activé.  
  
> [!NOTE]  
> Le streaming et le traitement parallèle ne sont pris en charge que dans Enterprise Edition. Vous pouvez inclure les paramètres dans vos requêtes dans l’édition standard sans soulever une erreur, mais les paramètres n’ont aucun effet et les scripts R s’exécutent en un seul processus.  
  
## <a name="restrictions"></a>Restrictions  

### <a name="data-types"></a>Types de données

Les types de données suivants ne sont pas pris en charge lorsqu’ils sont utilisés dans la requête d’entrée ou les paramètres de la procédure **sp_execute_external_script,** et renvoient une erreur de type non étayée.  

En tant que **CAST** solution de contournement, CAST [!INCLUDE[tsql](../../includes/tsql-md.md)] la colonne ou la valeur à un type pris en charge avant de l’envoyer au script externe.  
  
-   **Curseur**  
  
-   **Timestamp**  
  
-   **datetime2**, **datetimeoffset**, **heure**  
  
-   **sql_variant**  
  
-   **texte**, **image**  
  
-   **xml**  
  
-   **hiérarchie,** **géométrie**, **géographie**  
  
-   types CLR définis par l'utilisateur

En général, tout ensemble de résultat [!INCLUDE[tsql](../../includes/tsql-md.md)] qui ne peut pas être cartographié à un type de données, est la sortie comme NULL.  

### <a name="restrictions-specific-to-r"></a>Restrictions spécifiques à R

Si l’entrée comprend des valeurs **de date** qui ne correspondent pas à la gamme de valeurs autorisées en R, les valeurs sont converties en **NA**. Cela est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessaire parce que permet un plus large éventail de valeurs que ce qui est pris en charge dans la langue R.

Les valeurs de `+Inf`flotteurs (par exemple, , `-Inf`, `NaN`) ne sont pas prises en charge même [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si les deux langues utilisent IEEE 754. Le comportement actuel envoie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] simplement les valeurs directement; par conséquent, le client [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] SQL jette une erreur. Par conséquent, ces valeurs sont converties en **NULL**.

## <a name="permissions"></a>Autorisations

Nécessite **EXECUTE N’IMPORTE QUELLE** autorisation de base de données SCRIPT EXTERNE.  

## <a name="examples"></a>Exemples

Cette section contient des exemples de la façon dont cette [!INCLUDE[tsql](../../includes/tsql-md.md)]procédure stockée peut être utilisée pour exécuter des scripts R ou Python à l’aide de .

### <a name="a-return-an-r-data-set-to-sql-server"></a>R. Retourner un ensemble de données R sur SQL Server  

L’exemple suivant crée une procédure stockée qui utilise **sp_execute_external_script** pour retourner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]le jeu de données Iris inclus avec R à .  

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

L’exemple suivant crée une procédure stockée qui utilise **sp_execute_external_script** pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]générer un modèle d’iris et de retourner le modèle à .  

> [!NOTE]
>  Cet exemple nécessite l’installation préalable du paquet e1071. Pour plus d’informations, voir [Installer des forfaits R supplémentaires sur SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md).

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

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>C. Créer un modèle Python et générer des scores à partir de ce modèle

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

Les rubriques de colonne utilisées dans le code Python ne sont pas la sortie de SQL Server ; par conséquent, utilisez la déclaration WITH RESULT pour spécifier les noms de colonnes et les types de données que SQL peut utiliser.

Pour calculer les scores, vous pouvez également utiliser la fonction [PREDICT](../../t-sql/queries/predict-transact-sql.md) native, qui est généralement plus rapide car elle évite d’appeler le runtime Python ou R.

## <a name="see-also"></a>Voir aussi

+ [Services d’apprentissage automatique de serveur SQL](../../machine-learning/index.yml)
+ [Extensions linguistiques du serveur SQL](../../language-extensions/language-extensions-overview.md). 
+ [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
+ [Bibliothèques python et types de données](../../machine-learning/python/python-libraries-and-data-types.md)  
+ [R Bibliothèques et types de données R](../../machine-learning/r/r-libraries-and-data-types.md)  
+ [SQL Server R Services](../../machine-learning/r/sql-server-r-services.md)   
+ [Problèmes connus pour SQL Server Machine Learning Services](../../machine-learning/known-issues-for-sql-server-machine-learning-services.md)   
+ [CREATE BIBLIOTHÈQUE EXTERNE &#40;&#41;Transact-SQL](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
+ [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
+ [external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
+ [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
+ [SQL Server, objet External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
+ [Sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
