---
title: Présentation de package Python de revoscalepy dans SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f1d4d8bbb47c34fce61bdb95a3184a1d2b10f4d1
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889475"
---
# <a name="introducing-revoscalepy-in-sql-server-machine-learning"></a>Présentation de revoscalepy dans SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** une nouvelle bibliothèque Python n’est fourni par Microsoft pour prendre en charge l’informatique distribuée, à distance contextes de calcul et les algorithmes de hautes performances pour les développeurs Python.

Il est basé sur le **RevoScaleR** package pour R, qui a été fourni dans Microsoft R Server et SQL Server R Services et vise à fournir les mêmes fonctionnalités :

+ Prend en charge plusieurs contextes de calcul locaux et distants
+ Fournit des fonctions équivalentes à celles de RevoScaleR pour la visualisation et de transformation des données
+ Fournit des versions de Python de RevoScaleR algorithmes d’apprentissage automatique pour le traitement distribué ou en parallèle
+ Amélioration des performances, notamment l’utilisation des bibliothèques de mathématiques Intel

MicrosoftML packages sont également fournis pour R et Python. Pour plus d’informations, consultez [à l’aide de MicrosoftML dans SQL Server](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>Versions et plateformes prises en charge

Le **revoscalepy** module est disponible uniquement lorsque vous installez un des produits Microsoft suivants :

+ Machine Learning Services, dans SQL Server 2017
+ Microsoft Machine Learning Server 9.2.0 ou version ultérieure

Pour obtenir la dernière version de revoscalepy, installer la mise à jour Cumulative 1 pour SQL Server 2017. Il inclut de nombreuses améliorations dans Python, y compris :

+ Une nouvelle fonction Python, `rx_create_col_info`, qui obtient des informations de schéma à partir d’une source de données SQL Server, tels que [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) pour 
+ Améliorations apportées aux [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) pour prendre en charge les scénarios parallèles à l’aide de la `RxLocalParallel` contexte de calcul. 

## <a name="supported-functions-and-data-types"></a>Types de données et fonctions pris en charge

Cette section fournit une vue d’ensemble des types de données de Python et des nouvelles fonctions de Python prise en charge dans les **revoscalepy** module, en commençant par la version de SQL Server 2017 CTP 2.0. 

Pour obtenir la liste des fonctions dans les bibliothèques Python mis à la date, consultez ces liens :

+ [revoscalepy pour Python](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [microsoftml pour Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>Types de données, les sources de données et les contextes de calcul

SQL Server et Python utilisent différents types de données dans certains cas. Pour obtenir la liste de mappages entre les types de données SQL et Python, consultez [extension Python](../concepts/extension-python.md).

Sources de données prises en charge pour l’apprentissage de Python dans SQL Server inclut les sources de données ODBC, base de données SQL Server et les fichiers locaux, y compris les fichiers XDF.

Vous créez l’objet de source de données à l’aide des fonctions répertoriées dans le tableau suivant. Après avoir défini la source de données, vous chargez ou transformer les données à l’aide appropriée [(fonction) ETL](#bkmk_etl).

> [!IMPORTANT]
> Nombre de noms de fonction ont changé depuis la version initiale de Python dans CTP 2.0.

**Données de SQL Server**

+ Utilisez [RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata) pour définir une source de données à partir d’une requête ou une table
+ Utilisez [RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) pour créer un contexte de calcul de SQL Server
+ Utilisez [RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) pour créer une source de données à partir d’une connexion ODBC

**revoscalepy** prend également en charge la [source de données XDF](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata), utilisé pour le déplacement des données entre la mémoire et d’autres sources de données.

> [!TIP]
> Si vous ne connaissez pas l’idée de sources de données ou les contextes de calcul, nous vous recommandons de commencer par lire sur le fonctionnement du calcul distribué pour l’apprentissage dans [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction).


### <a name="bkmk_algorithms"></a>Machine learning et les fonctions de synthèse

Les algorithmes d’apprentissage automatique suivants et des fonctions de synthèse à partir de RevoScaleR sont incluses dans SQL Server 2017, à partir de CTP 2.0.

| Fonction| Description|Remarques|
| ------ | ------ |------ |
|`rx_btrees` | Ajuster les arbres de décision augmentés de gradient stochastique|`rx_btrees_ex` dans CTP 2.0|
|`rx_dforest` | Ajuster les forêts de décision de classification et de régression|`rx_dforest_ex` dans CTP 2.0|
|`rx_dtree` | Ajuster des arbres de classification et de régression |`rx_dtree_ex` dans CTP 2.0|
|`rx_lin_mod` | Créer un modèle linéaire|`rx_lin_mod_ex` dans CTP 2.0|
|`rx_logit` | Créer un modèle de régression logistique|`rx_logit_ex` dans CTP 2.0|
|`rx_predict` | Générer des prédictions à partir d’un modèle formé|`rx_predict_ex` dans CTP 2.0|
|`rx_summary` | Générer un résumé du modèle||

Nouveaux algorithmes machine learning sont également fournies par la version de Python de [MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| Fonction| Description|
| ------ | ------ |
|`rx_fast_forest` |Créez un modèle de forêt de décision|
|`rx_fast_linear` | Régression linéaire avec SGD ascent coordonnée double|
|`rx_fast_trees` | Créer un modèle d’arbre de décision optimisé |
|`rx_logistic_regression` | Créer un modèle de régression logistique|
|`rx_neural_network` | Créer un modèle de réseau neuronal personnalisable |
|`rx_oneclass_svm` | Crée un modèle SVM sur un jeu de données déséquilibré, pour la détection d’anomalie|

> [!TIP]
> La plupart de ces algorithmes sont déjà fournis sous forme de modules dans Azure Machine Learning.

MicrosoftML pour Python inclut également une variété de transformations et les fonctions d’assistance, telles que :

+ `rx_predict` génère des prédictions à partir d’un modèle formé et peut être utilisé pour calculer les scores en temps réel
+ fonctions de personnalisation d’image
+ fonctions d’extraction de traitement et le sentiment de texte

Pour plus d’informations, consultez [présentation de MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> La Communauté Python utilise les conventions de codage peuvent être différentes de ce que vous êtes habitué, y compris toutes les lettres minuscules et des traits de soulignement plutôt que de la casse mixte pour les noms de paramètre. En outre, peut-être que vous avez remarqué que la **revoscalepy** bibliothèque est toujours en minuscule. C'est juste ! Une autre convention de Python.
> 
> Consultez les conseils sur la documentation de référence de Python pour Microsoft R: [aide de la fonction Python][Python fonction help](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>Exemples

Vous pouvez exécuter le code qui inclut **revoscalepy** fonctions localement ou dans un contexte de calcul à distance. Vous pouvez également exécuter Python dans SQL Server en incorporant le code Python dans une procédure stockée.

Lorsque vous exécutez localement, vous généralement exécuter un script Python à partir de la ligne de commande, ou à partir d’un environnement de développement Python et spécifier un contexte de calcul de SQL Server à l’aide d’une de la **revoscalepy** fonctions. Vous pouvez utiliser le contexte de calcul à distance pour l’ensemble du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur d’utiliser des données les plus récentes et éviter le déplacement des données.

Si vous souhaitez placer un script Python complet à l’intérieur de la procédure stockée, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), nous vous recommandons de réécrire le code comme une fonction unique qui a défini clairement les entrées et sorties. Entrées et sorties doivent être **pandas** des trames de données. Dans ce cas, vous pouvez appeler la procédure stockée à partir de n’importe quel client qui prend en charge T-SQL, facilement transmettre les requêtes SQL en tant qu’entrées et enregistrer les résultats dans des tables SQL. Pour obtenir un exemple, consultez [Analytique de Python dans base de données pour les développeurs SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-remote-compute-contexts"></a>À l’aide des contextes de calcul à distance

+ [Créer un modèle à l’aide de revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)

  Cet exemple montre comment exécuter Python à l’aide d’une instance de SQL Server comme contexte de calcul.

### <a name="using-a-stored-procedure"></a>À l’aide d’une procédure stockée

+ [Exécuter Python avec T-SQL](../tutorials/run-python-using-t-sql.md)

  Cet exemple montre le mécanisme de base de l’appel de script Python qui est incorporé dans une procédure stockée.

### <a name="using-revoscalepy-with-microsoftml"></a>À l’aide de revoscalepy avec MicrosoftML

Les fonctions de Python pour MicrosoftML sont intégrées avec les contextes de calcul et les sources de données qui sont fournies dans revoscalepy. Par conséquent, vous pouvez utiliser un algorithme de MicrosoftML pour définir et de former un modèle dans Python et utiliser les fonctions de revoscalepy pour exécuter le code Python, localement ou dans un contexte de calcul de SQl Server.

Importer uniquement les modules dans votre code Python et puis faire référence aux fonctions individuelles que vous avez besoin.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>Spécifications

Pour exécuter le code Python dans SQL Server, vous devez avoir installé SQL Server 2017 avec la fonctionnalité **Machine Learning Services**et activé le langage Python. Les versions antérieures de SQL Server ne prennent pas en charge intégration de Python.

> [!NOTE]
> Distributions Open source de Python ne gèrent pas les contextes de calcul de SQL Server. Toutefois, si vous avez besoin publier et consommer des applications Python à partir de Windows, vous pouvez installer Microsoft Machine Learning Server sans installation de SQL Server. Pour plus d’informations, consultez [installer SQL Server 2017 Machine Learning Server (autonome)](../install/sql-machine-learning-standalone-windows-install.md).

## <a name="get-more-help"></a>Obtenir une assistance supplémentaire

Une documentation complète de ces API seront disponible lorsque le produit est lancé. En attendant, nous recommandons que vous référencez la fonction correspondante dans les bibliothèques RevoScaleR ou MicrosoftML.

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

Vous pouvez obtenir de l’aide sur n’importe quelle fonction Python par l’importation du module, puis en appelant `help()`. Par exemple, en cours d’exécution `help(revoscalepy)` à partir de votre IDE Python retourne une liste de toutes les fonctions dans le module revoscalepy, avec leurs signatures.

Si vous utilisez Python Tools pour Visual Studio, vous pouvez utiliser IntelliSense pour obtenir de l’aide de syntaxe et de l’argument. Pour plus d’informations, consultez [prennent en charge de Python dans Visual Studio](http://docs.microsoft.com/visualstudio/python/installation)et télécharger l’extension qui correspond à votre version de Visual Studio. Vous pouvez utiliser Python avec Visual Studio 2015 et 2017, ou des versions antérieures.

## <a name="see-also"></a>Voir aussi

[Didacticiels Python](../tutorials/sql-server-python-tutorials.md)
