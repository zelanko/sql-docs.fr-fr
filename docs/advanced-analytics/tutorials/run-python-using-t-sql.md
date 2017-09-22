---
title: "Exécuter à l’aide de T-SQL de Python | Documents Microsoft"
ms.custom: 
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- Python
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: f2eba50d5c5e57025462c46b38fc0ddbfc947ea0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="run-python-using-t-sql"></a>Exécutez Python à l’aide de T-SQL

Cet exemple montre comment vous pouvez exécuter un script Python simple dans SQL Server, à l’aide de la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

## <a name="step-1-create-the-test-data-table"></a>Étape 1. Créer la table de données de test

Tout d’abord, vous allez créer des données supplémentaires, à utiliser lorsque vous mappez les noms des jours de la semaine pour la source de données. Exécutez l’instruction T-SQL suivante pour créer la table.

```SQL
CREATE TABLE PythonTest (
    [DayOfWeek] varchar(10) NOT NULL,
    [Amount] float NOT NULL
    )
GO

INSERT INTO PythonTest VALUES
('Sunday', 10.0),
('Monday', 11.1),
('Tuesday', 12.2),
('Wednesday', 13.3),
('Thursday', 14.4),
('Friday', 15.5),
('Saturday', 16.6),
('Friday', 17.7),
('Monday', 18.8),
('Sunday', 19.9)
GO
```

## <a name="step-2-run-the-hello-world-script"></a>Étape 2. Exécutez le script « Hello World »

Le code suivant charge l’exécutable de Python, transmet les données d’entrée et pour chaque ligne de données d’entrée, met à jour le nom du jour de la table avec un nombre qui représente l’index du jour de la semaine.

Notez le paramètre * @RowsPerRead *. Ce paramètre spécifie le nombre de lignes qui sont passés à l’exécution de Python à partir de SQL Server.

La bibliothèque d’analyse données Python, appelé **pandas**, est requis pour passer des données vers SQL Server et est inclus par défaut avec les Services de Machine Learning.

```sql
DECLARE @ParamINT INT = 1234567
DECLARE @ParamCharN VARCHAR(6) = 'INPUT '

print '------------------------------------------------------------------------'
print 'Output parameters (before):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)

print 'Dataset (before):'
SELECT * FROM PythonTest

print '------------------------------------------------------------------------'
print 'Dataset (after):'
DECLARE @RowsPerRead INT = 5

execute sp_execute_external_script 
@language = N'Python',
@script = N'
import sys
import os
print("*******************************")
print(sys.version)
print("Hello World")
print(os.getcwd())
print("*******************************")
if ParamINT == 1234567:
       ParamINT = 1
else:
       ParamINT += 1

ParamCharN="OUTPUT"
OutputDataSet = InputDataSet

global daysMap

daysMap = {
       "Monday" : 1,
       "Tuesday" : 2,
       "Wednesday" : 3,
       "Thursday" : 4,
       "Friday" : 5,
       "Saturday" : 6,
       "Sunday" : 7
       }

OutputDataSet["DayOfWeek"] = pandas.Series([daysMap[i] for i in OutputDataSet["DayOfWeek"]], index = OutputDataSet.index, dtype = "int32")
', 
@input_data_1 = N'SELECT * FROM PythonTest', 
@params = N'@r_rowsPerRead INT, @ParamINT INT OUTPUT, @ParamCharN CHAR(6) OUTPUT',
@r_rowsPerRead = @RowsPerRead,
@paramINT = @ParamINT OUTPUT,
@paramCharN = @ParamCharN OUTPUT
with result sets (("DayOfWeek" int null, "Amount" float null))

print 'Output parameters (after):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)
GO
```

> [!TIP]
> Les paramètres pour cette procédure stockée sont décrits plus en détail dans ce démarrage rapide : [du code à l’aide de R dans T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md).

## <a name="step-3-view-the-results"></a>Étape 3. Afficher les résultats

La procédure stockée Obtient les données d’origine, s’applique le script Python, puis retourne les données modifiées dans le **résultats** volet de Management Studio ou autre outil de requête SQL.


|DayOfWeek (avant)| Montant|DayOfWeek (après) |
|-----|-----|-----|
|Dimanche|10|7|
|Lundi|11.1|1|
|Mardi|12.2|2|
|Mercredi|13.3|3|
|Jeudi|14.4|4|
|Vendredi|15.5|5|
|Samedi|16.6|6|
|Vendredi|17.7|5|
|Lundi|18.8|1|
|Dimanche|19.9|7|

Messages d’état ou les erreurs renvoyées à la console de Python sont retournées sous forme de messages dans la **requête** fenêtre. Voici un extrait de la sortie que peut s’afficher :

*Exemples de résultats*

```
Output parameters (before):
ParamINT=1234567
ParamCharN=INPUT 
Dataset (before):

(10 rows affected)

Dataset (after):
STDOUT message(s) from external script: 
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

(10 rows affected)
Output parameters (after):
ParamINT=2
ParamCharN=OUTPUT
```

+ Le **Message** sortie inclut le répertoire de travail utilisé pour l’exécution du script. Dans cet exemple, MSSQLSERVER01 fait référence au compte de processus de travail alloué par SQL Server pour gérer la tâche. 

    Le GUID est le nom d’un dossier temporaire est créé pendant l’exécution du script pour stocker les artefacts de données et de script. Ces dossiers temporaires sont sécurisés par SQL Server et sont nettoyés par l’objet de traitement Windows une fois que le script s’est arrêté.

+ La section qui contient le message « Hello World » imprime deux fois. Cela se produit car la valeur de * @RowsPerRead * a été défini sur 5 et il y a 10 lignes de la table ; par conséquent, les deux appels à Python sont requis pour traiter toutes les lignes de la table.

    Dans vos séries de production, nous recommandons que vous fassiez des essais avec différentes valeurs pour déterminer le nombre maximal de lignes qui doivent être passés dans chaque lot. Le nombre optimal de lignes est dépendant des données et est affecté par le nombre de colonnes dans le jeu de données et le type de données que vous passez.

## <a name="resources"></a>Ressources

Consultez ces exemples de Python supplémentaires et des didacticiels de conseils avancés et des démonstrations de bout en bout.

+ [Utiliser Python revoscalepy pour créer un modèle](use-python-revoscalepy-to-create-model.md)
+ [Python dans base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

## <a name="troubleshooting"></a>Dépannage

Si vous ne trouvez pas la procédure stockée, `sp_execute_external_script`, cela signifie que vous n’avez pas probablement terminé la configuration de l’instance pour prendre en charge l’exécution du script externe. Une fois le programme d’installation de SQL Server 2017 en cours d’exécution et en sélectionnant les Python en tant que langue d’apprentissage, vous devez explicitement activer la fonctionnalité à l’aide de `sp_configure`, puis redémarrez l’instance. Pour plus d’informations, consultez [le programme d’installation Machine Learning Services avec Python](../python/setup-python-machine-learning-services.md).
