---
title: sp_rxPredict | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f46403afef0e2f6cf967561a8fd24ec6409fe93
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434859"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Génère une valeur prédite pour une entrée donnée selon un modèle stocké dans un format binaire dans une base de données SQL Server machine learning.

Fournit des modèles R et Python machine learning dans quasiment en temps réel de notation. `sp_rxPredict` est une procédure stockée fournie comme un wrapper pour le `rxPredict` fonction R au [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) et [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)et le [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) fonction Python dans [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Il est écrit en C++ et est spécialement optimisée pour les opérations de calcul de score.

**Cet article s’applique à**:  
- SQL Server 2017  
- SQL Server 2016 R Services avec [mis à niveau les composants R](https://docs.microsoft.com/sql/advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server)

## <a name="syntax"></a>Syntaxe

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Arguments

**model**

Un modèle préformé dans un format pris en charge. 

**input**

Une requête SQL valide

### <a name="return-values"></a>Valeurs retournées

Une colonne de score est renvoyée, ainsi que les colonnes SQL directes à partir de la source de données d’entrée.
Autres colonnes, telles que de l’intervalle de confiance de score, peut être retourné si l’algorithme prend en charge la génération de ces valeurs.

## <a name="remarks"></a>Notes

Pour activer l’utilisation de la procédure stockée, SQLCLR doit être activé sur l’instance.

> [!NOTE]
> Prendre en compte les implications de sécurité avant d’activer cette option.

L’utilisateur doit avoir `EXECUTE` autorisation sur la base de données.

### <a name="supported-platforms"></a>Plateformes prises en charge
 
- SQL Server 2017 Machine Learning Services (inclut R Server 9.2)  
- SQL Server 2017 Machine Learning Server (autonome) 
- SQL Server R Services 2016, avec une mise à niveau de l’instance de R Services à R Server 9.1.0). ou version ultérieure  

### <a name="supported-algorithms"></a>Algorithmes pris en charge

Pour une liste des algorithmes pris en charge, consultez [de score en temps réel](../../advanced-analytics/real-time-scoring.md).

Les types de modèle suivants sont **pas** pris en charge :  
- Modèles contenant d’autres types de transformations de R non pris en charge  
- Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes dans RevoScaleR  
- Modèles PMML  
- Modèles créés à l’aide d’autres bibliothèques R à partir de CRAN ou d’autres référentiels  
- Modèles contenant n’importe quel autre type de transformation R autres que ceux répertoriés ici  

## <a name="examples"></a>Exemples

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

En plus de constituer une requête SQL valide, les données d’entrée dans *@inputData* doit inclure des colonnes compatibles avec les colonnes dans le modèle stocké.

`sp_rxPredict` prend en charge uniquement les types de colonne de .NET suivants : double, float, short, ushort, long, ulong et chaîne. Vous devrez peut-être filtrer les types non pris en charge dans vos données d’entrée avant de l’utiliser pour calculer les scores en temps réel. 

  Pour plus d’informations sur les types SQL correspondants, consultez [le mappage de Type SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) ou [mappage des données de paramètre CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

