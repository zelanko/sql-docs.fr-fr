---
title: fonctions d’assistance de sqlrutils - SQL Server Machine Learning Services
description: Utiliser la bibliothèque de fonctions sqlrutils dans SQL Server 2016 R Services et SQL Server 2017 Machine Learning Services avec R pour générer des procédures stockées contenant le script R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7ccc3ad494658fc7a8f9c67472aecb1c4cddb7da
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512236"
---
# <a name="sqlrutils-r-library-in-sql-server"></a>sqlrutils (bibliothèque R dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le package **sqlrutils** fournit un mécanisme permettant aux utilisateurs de R de placer leurs scripts R dans une procédure stockée T-SQL, d’inscrire cette procédure auprès d’une base de données, et d’exécuter la procédure stockée à partir d’un environnement de développement R. 

En convertissant votre code R pour qu’il s’exécute dans une seule procédure stockée, vous pouvez utiliser plus efficacement SQL Server R Services, qui exige que le script R soit incorporé en tant que paramètre dans [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Le package **sqlrutils** vous permet de créer ce script R incorporé et de définir correctement les paramètres connexes.

Le package **sqlrutils** effectue ces tâches :

- Il enregistre le script T-SQL généré sous forme de chaîne à l’intérieur d’une structure de données R.
- Si vous le souhaitez, il génère un fichier .sql pour le script T-SQL, que vous pouvez modifier ou exécuter pour créer une procédure stockée.
- Il inscrit la procédure stockée créée auprès de l’instance de SQL Server à partir de votre environnement de développement R.

Vous pouvez également exécuter la procédure stockée à partir d’un environnement R, en transmettant des paramètres bien formés et en traitant les résultats. Vous pouvez aussi utiliser la procédure stockée à partir de SQL Server pour prendre en charge des scénarios d’intégration de base de données courants comme ETL, l’apprentissage de modèle et les notations volumineuses.

  > [!NOTE]
  > Si vous envisagez d’exécuter la procédure stockée à partir d’un environnement R en appelant la fonction *executeStoredProcedure* , vous devez utiliser un fournisseur ODBC 3.8, tel que le pilote ODBC 13 pour SQL Server.  
  
## <a name="full-reference-documentation"></a>Documentation de référence complète

Le **sqlrutils** library est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même, si vous obtenez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, [documentation pour les fonctions individuelles sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est publié dans un seul emplacement sous la [référence de R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Doivent tout propres au produit comportements existent, les différences sont notées dans la page d’aide (fonction).

## <a name="functions-list"></a>Liste des fonctions

La section suivante fournit une vue d’ensemble des fonctions que vous pouvez appeler à partir de la **sqlrutils** package pour développer une procédure stockée contenant incorporé code R. Pour plus d’informations des paramètres de chaque méthode ou fonction, consultez l’aide de R pour le package : `help(package="sqlrutils")`

|Fonction | Description |
|------|-------------|
|[executeStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/executestoredprocedure)| Exécuter une procédure stockée SQL.|
|[getInputParameters](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/getinputparameters)| Obtenir la liste des paramètres d’entrée à la procédure stockée.| 
|[InputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputdata)| Définit la source de données dans SQL Server qui sera utilisée dans la trame de données R. Vous spécifiez le nom de la trame de données dans laquelle stocker les données d’entrée, et une requête pour obtenir les données ou une valeur par défaut. Seules les requêtes SELECT simples sont prises en charge. | 
|[InputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputparameter)| Définit un seul paramètre d’entrée qui est incorporé dans le script T-SQL. Vous devez fournir le nom du paramètre et son type de données R.| 
|[OutputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputdata)| Génère un objet de données intermédiaire qui est nécessaire si votre fonction R retourne une liste contenant une trame de données. L’objet *OutputData* est utilisé pour stocker le nom d’une trame de données unique obtenue à partir de la liste.| 
|[OutputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputparameter) | Génère un objet de données intermédiaire qui est nécessaire si votre fonction R retourne une liste. L’objet *OutputParameter* stocke le nom et le type de données d’un seul membre de la liste, en supposant que ce membre n’est **pas** une trame de données. |
|[registerStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/registerstoredprocedure) | Inscrire la procédure stockée avec une base de données.|
|[setInputDataQuery](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputdataquery)| Assigner une requête à un paramètre d’entrée de données de la procédure stockée.| 
|[setInputParameterValue](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputparametervalue)| Affecter une valeur à un paramètre d’entrée de la procédure stockée.| 
|[StoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/storedprocedure)| Un objet de la procédure stockée.|


## <a name="how-to-use-sqlrutils"></a>L’utilisation de sqlrutils

Le **sqlrutils** fonctions de bibliothèque doivent s’exécuter sur un ordinateur disposant de SQL Server Machine Learning avec R. Si vous travaillez sur une station de travail cliente, définir un contexte de calcul à distance à l’exécution de la touche MAJ enfoncée à SQL Server. Le flux de travail pour l’utilisation de ce package comprend les étapes suivantes :

+ Définir les paramètres de procédure stockée (entrées, sorties ou les deux) 
+ Générer et inscrire la procédure stockée    
+ Exécuter la procédure stockée  

Dans une session R, chargez **sqlrutils** à partir de la ligne de commande en tapant `library(sqlrutils)`.

> [!Note]
> Vous pouvez charger cette bibliothèque sur un ordinateur qui ne dispose pas de SQL Server (par exemple, sur une instance de R Client) si vous modifiez le contexte de calcul à SQL Server et que vous exécutez le code dans ce contexte de calcul.


### <a name="define-stored-procedure-parameters-and-inputs"></a>Définir des entrées et des paramètres de procédure stockée

`StoredProcedure` est le constructeur principal utilisé pour générer la procédure stockée. Ce constructeur génère un objet de *procédure stockée SQL Server* et crée éventuellement un fichier texte contenant une requête qui peut servir à générer la procédure stockée à l’aide d’une commande T-SQL. 

Si vous le souhaitez, la fonction *StoredProcedure* peut également inscrire la procédure stockée auprès de l’instance et de la base de données spécifiées.

+ Utilisez l’argument `func` pour spécifier une fonction R valide. Toutes les variables utilisées par la fonction doivent être définies à l’intérieur de la fonction ou être fournies en tant que paramètres d’entrée. Ces paramètres peuvent inclure au plus une trame de données.

+ La fonction R doit retourner une trame de données, une liste nommée ou la valeur NULL. Si la fonction retourne une liste, celle-ci peut contenir au plus une trame de données.

+ Utilisez l’argument `spName` pour spécifier le nom de la procédure stockée que vous souhaitez créer.

+ Vous pouvez transmettre des paramètres d’entrée et de sortie facultatifs, en utilisant les objets créés par ces fonctions d’assistance : `setInputData`, `setInputParameter`et `setOutputParameter`.

+  Vous pouvez également utiliser `filePath` pour spécifier le chemin et le nom d’un fichier .sql à créer. Vous pouvez exécuter ce fichier sur l’instance de SQL Server pour générer la procédure stockée à l’aide de T-SQL.

+ Pour définir le serveur et la base de données où sera enregistrée la procédure stockée, utilisez les arguments `dbName` et  `connectionString`.

+ Pour obtenir une liste des objets *InputData* et *InputParameter* qui ont été utilisés pour créer un objet *StoredProcedure* spécifique, appelez `getInputParameters`. 

+ Pour inscrire la procédure stockée auprès de la base de données spécifiée, utilisez `registerStoredProcedure`.

Aucune donnée ou valeur n’est généralement associé à l’objet de procédure stockée, sauf si une valeur par défaut a été spécifiée. Les données ne sont récupérées qu’une fois que la procédure stockée est exécutée. 

### <a name="specify-inputs-and-execute"></a>Spécifier les entrées et exécuter

+ Utilisez `setInputDataQuery` pour assigner une requête à un objet *InputParameter* . Par exemple, si vous avez créé un objet de procédure stockée dans R, vous pouvez utiliser `setInputDataQuery` pour passer des arguments à la fonction *StoredProcedure* afin d’exécuter la procédure stockée avec les entrées souhaitées.

+ Utilisez `setInputValue` pour assigner des valeurs spécifiques à un paramètre stocké comme objet *InputParameter* . Vous passez ensuite l’objet de paramètre et son affectation de valeur à la fonction *StoredProcedure* pour exécuter la procédure stockée avec les valeurs définies.

+ Utilisez `executeStoredProcedure` pour exécuter une procédure stockée définie comme objet *StoredProcedure* . Appelez cette fonction uniquement quand vous exécutez une procédure stockée à partir de code R. Ne l’utilisez pas quand vous exécutez la procédure stockée à partir de SQL Server à l’aide de T-SQL.

> [!NOTE]
> La fonction *executeStoredProcedure* nécessite un fournisseur ODBC 3.8, tel que le pilote ODBC 13 pour SQL Server.  

## <a name="see-also"></a>Voir aussi

[Comment créer une procédure stockée à l’aide de sqlrutils](how-to-create-a-stored-procedure-using-sqlrutils.md)

