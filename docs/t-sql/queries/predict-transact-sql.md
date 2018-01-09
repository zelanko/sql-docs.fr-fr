---
title: "PRÉDIRE (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PREDICT
- PREDICT_TSQL
dev_langs: TSQL
helpviewer_keywords: PREDICT clause
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 5f2ed3582341ff2824943a432e5877602b0b9ee7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="predict-transact-sql"></a>PRÉDIRE (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Génère une valeur prédite ou les scores en fonction d’un modèle stocké.  

## <a name="syntax"></a>Syntaxe

```
PREDICT  
(  
  MODEL = @model | model_literal,  
  DATA = object AS <table_alias>  
)  
WITH ( <result_set_definition> )  

<result_set_definition> ::=  
  {  
    { column_name  
      data_type  
      [ COLLATE collation_name ]  
      [ NULL | NOT NULL ]  
    }  
      [,...n ]  
  }  

MODEL = @model | model_literal  
```

### <a name="arguments"></a>Arguments

**model**

Le `MODEL` paramètre est utilisé pour spécifier le modèle utilisé pour calculer les scores ou la prédiction. Le modèle est spécifié comme une variable ou un littéral ou une expression scalaire.

L’objet de modèle peut être créé à l’aide de R ou Python ou un autre outil.

**data**

Le paramètre de données est utilisé pour spécifier les données utilisées pour calculer les scores ou la prédiction. Données sont spécifiées sous la forme d’une source de table dans la requête. Source de table peut être une table, un alias de table, un alias de l’expression de table commune, une vue ou un fonction table.

**paramètres**

Le paramètre de paramètres est utilisé pour spécifier des paramètres facultatifs définis par l’utilisateur utilisés pour calculer les scores ou la prédiction.

Le nom de chaque paramètre est spécifique au type de modèle. Par exemple, la fonction rxPredict dans RevoScaleR prend en charge le paramètre  _@computeResiduals bits_ pour prendre en charge de calcul des résiduels lors de l’évaluation d’un modèle de régression logistique. Vous pourriez passer que nom du paramètre et valeur pour le `PREDICT` (fonction).

> [REMARQUE] Cette option n’est pas pris en charge dans la version préliminaire de SQL Server 2017 et est incluse uniquement à des fins de compatibilité avant.

**AVEC ( \<result_set_definition >)**

La clause WITH est utilisée pour spécifier le schéma de la sortie retournée par le `PREDICT` (fonction).

En plus des colonnes retournées par la `PREDICT` fonction proprement dite, toutes les colonnes qui font partie des données d’entrée sont disponibles pour une utilisation dans la requête.

### <a name="return-values"></a>Valeurs retournées

Aucun schéma prédéfini n’est disponible ; SQL Server ne valide pas le contenu du modèle et ne valide pas les valeurs de colonne retourné.  
- Le `PREDICT` fonction traverse les colonnes en tant qu’entrée  
- Le `PREDICT` fonction génère également de nouvelles colonnes, mais le nombre de colonnes et leurs types de données varie selon le type de modèle qui a été utilisé pour la prédiction.  

Les messages d’erreur liés aux données, le modèle ou le format de colonne sont retournés par la fonction de prédiction sous-jacente associée au modèle.  
- Pour RevoScaleR, la fonction équivalente est [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)  
- Pour MicrosoftML, la fonction équivalente est [rxPredict.mlModel](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxpredict)  

Il n’est pas possible d’afficher la structure de modèle interne à l’aide de `PREDICT`. Si vous souhaitez comprendre le contenu du modèle lui-même, vous devez charger le modèle objet, désérialiser et utiliser code R approprié pour analyser le modèle.

## <a name="remarks"></a>Notes 

Le `PREDICT` fonction est prise en charge dans toutes les éditions de SQL Server, notamment Linux.

Il n’est pas nécessaire que R, Python ou une autre machine learning langage être installé sur le serveur à utiliser le `PREDICT` (fonction). Vous pouvez l’apprentissage du modèle dans un autre environnement et l’enregistrer dans une table SQL Server pour une utilisation avec `PREDICT`, ou appelez le modèle à partir d’une autre instance de SQL Server qui contient le modèle enregistré.

### <a name="supported-algorithms"></a>Algorithmes pris en charge

Le modèle que vous utilisez doit avoir été créé à l’aide d’un des algorithmes pris en charge à partir du package RevoScaleR. Pour obtenir la liste de modèles actuellement pris en charge, consultez [en temps réel de calcul de score](../../advanced-analytics/real-time-scoring.md).

### <a name="permissions"></a>Autorisations

Aucune autorisation n’est requise pour `PREDICT`; Cependant, l’utilisateur doit avoir `EXECUTE` autorisation sur la base de données et pour interroger des données qui sont utilisées en tant qu’entrées. L’utilisateur doit également être en mesure de lire le modèle à partir d’une table, si le modèle a été stocké dans une table.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent la syntaxe pour appeler `PREDICT`.

### <a name="call-a-stored-model-and-use-it-for-prediction"></a>Appeler un modèle stocké et l’utiliser pour la prédiction

Cet exemple appelle un modèle de régression logistique existant stocké dans la table [models_table]. Obtient le dernier modèle formé, à l’aide d’une instruction SELECT, elle transmet ensuite le modèle binaire à la fonction de prédiction. Les valeurs d’entrée représentent les fonctionnalités ; la sortie représente la classification affectée par le modèle.

```sql
DECLARE @logit_model varbinary(max) = "SELECT TOP 1 @model from [models_table]";
DECLARE @input_qry = "SELECT ID, [Gender], [Income] from NewCustomers";

SELECT PREDICT [class]
FROM PREDICT( MODEL = @logit_model,  DATA = @input_qry
WITH (class string);
```

### <a name="using-predict-in-a-from-clause"></a>À l’aide de la prédiction dans une clause FROM

Cet exemple fait référence à la `PREDICT` de fonction dans le `FROM` clause d’un `SELECT` instruction :

```sql
SELECT d.*, p.Score
FROM PREDICT(MODEL = @logit_model, 
  DATA = dbo.mytable AS d) WITH (Score float) AS p;
```

L’alias **d** spécifié pour la source de table dans le _données_ paramètre est utilisé pour référencer les colonnes appartenant à dbo.mytable. L’alias **p** spécifié pour le **PREDICT** fonction est utilisée pour référencer les colonnes retournées par la fonction de prédiction.

### <a name="combining-predict-with-an-insert-statement"></a>Combinaison de prédire avec une instruction INSERT

Un des cas d’utilisation courants pour la prédiction consiste à générer un score pour les données d’entrée, puis insérez les valeurs prédites dans une table. L’exemple suivant suppose que l’application appelante utilise une procédure stockée pour insérer une ligne contenant la valeur prédite dans une table :

```sql
CREATE PROCEDURE InsertLoanApplication
(@p1 varchar(100), @p2 varchar(200), @p3 money, @p4 int)
AS
BEGIN
  DECLARE @model varbinary(max) = (select model
  FROM scoring_model
  WHERE model_name = 'ScoringModelV1');
  WITH d as ( SELECT * FROM (values(@p1, @p2, @p3, @p4)) as t(c1, c2, c3, c4) )

  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = d) WITH(score float) as p;
END;
```

Si la procédure accepte plusieurs lignes via un paramètre table, il peut être écrit comme suit :

```sql
CREATE PROCEDURE InsertLoanApplications (@new_applications dbo.loan_application_type)
AS
BEGIN
  DECLARE @model varbinary(max) = (SELECT model_bin FROM scoring_models WHERE model_name = 'ScoringModelV1');
  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = @new_applications as d)
  WITH (score float) as p;
END;
```

### <a name="creating-an-r-model-and-generating-scores-using-optional-model-parameters"></a>Création d’un modèle R et générer des scores à l’aide des paramètres de modèle facultatif

> [!NOTE]
> Utilisation de l’argument de paramètres n’est pas pris en charge dans la version Release Candidate 1.

Cet exemple suppose que vous avez créé un modèle de régression logistique avec une matrice de covariance, à l’aide d’un appel à RevoScaleR comme celui-ci :

```R
logitObj <- rxLogit(Kyphosis ~ Age + Start + Number, data = kyphosis, covCoef = TRUE)
```

Si vous stockez le modèle dans SQL Server au format binaire, vous pouvez utiliser la fonction PREDICT à générer non seulement les prédictions, mais également des informations supplémentaires pris en charge par le type de modèle, tels que des erreurs ou des intervalles de confiance.

Le code suivant montre l’appel équivalent à partir de R à rxPredict :

```R
rxPredict(logitObj, data = new_kyphosis_data, computeStdErr = TRUE, interval = "confidence")
```

L’appel équivalent à l’aide du `PREDICT` fonction fournit également le score (a prédit la valeur), erreur et les intervalles de confiance :

```sql
SELECT d.Age, d.Start, d.Number, p.pred AS Kyphosis_Pred, p.stdErr, p.pred_lower, p.pred_higher
FROM PREDICT( MODEL = @logitObj,  DATA = new_kyphosis_data AS d,
  PARAMETERS = N'computeStdErr bit, interval varchar(30)',
  computeStdErr = 1, interval = 'confidence')
WITH (pred float, stdErr float, pred_lower float, pred_higher float) AS p;
```


