---
title: Qu’est-ce que SQL Server R services 2016?
titleSuffix: ''
description: R services est une fonctionnalité de SQL Server 2016 qui donne la possibilité d’exécuter des scripts R avec des données relationnelles. Vous pouvez utiliser des infrastructures et des packages Open source, ainsi que les packages Microsoft R pour l’analyse prédictive et les Machine Learning. Les scripts sont exécutés dans la base de données sans déplacer de données en dehors de SQL Server ou sur le réseau. Cet article explique les notions de base de SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/12/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 973c09be9cff6e66043b056e1a772ab8974cebb4
ms.sourcegitcommit: 12b7e3447ca2154ec2782fddcf207b903f82c2c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957492"
---
# <a name="what-is-sql-server-2016-r-services"></a>Qu’est-ce que SQL Server R services 2016?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

R services est une fonctionnalité de SQL Server 2016 qui donne la possibilité d’exécuter des scripts R avec des données relationnelles. Vous pouvez utiliser des infrastructures et des packages Open source, ainsi que les [packages Microsoft R](#packages) pour l’analyse prédictive et les machine learning. Les scripts sont exécutés dans la base de données sans déplacer de données en dehors de SQL Server ou sur le réseau. Cet article explique les notions de base de SQL Server R Services.

> [!Note]
> R services a été renommé en [machine learning services](../what-is-sql-server-machine-learning.md) dans SQL Server 2017 et versions ultérieures, et prend en charge Python et R.

## <a name="what-is-r-services"></a>Qu’est-ce que R Services ?

SQL Server R Services vous permet d’exécuter des scripts R dans la base de données. Vous pouvez l’utiliser pour préparer et nettoyer des données, procéder à l’ingénierie des fonctionnalités et former, évaluer et déployer des Machine Learning des modèles dans une base de données. La fonctionnalité exécute vos scripts où résident les données et élimine le transfert des données sur le réseau vers un autre serveur.

Les distributions de base de R sont incluses dans R services. Vous pouvez utiliser des infrastructures et des packages Open source en plus des packages Microsoft [RevoScaleR](../r/ref-r-revoscaler.md), [MicrosoftML](../r/ref-r-microsoftml.md), [olapr]. /r/Ref-r-olapr.MD) et [sqlrutils](../r/ref-r-sqlrutils.md) pour r.

R Services utilise une infrastructure d’extensibilité pour exécuter des scripts R dans SQL Server. En savoir plus sur ce fonctionnement:

+ [Infrastructure d’extensibilité](../concepts/extensibility-framework.md)
+ [Extension R](../concepts/extension-r.md)

## <a name="what-can-i-do-with-r-services"></a>Que puis-je faire avec R services?

Vous pouvez utiliser R services pour générer et former des Machine Learning et des modèles d’apprentissage profond au sein de SQL Server. Vous pouvez également déployer des modèles existants sur R services et utiliser des données relationnelles pour les prédictions.

Voici des exemples de types de prédictions que vous pouvez utiliser SQL Server R Services pour, notamment:

|||
|-|-|
|Classification/catégorisation|Diviser automatiquement les commentaires client en catégories positives et négatives|
|Régression/prédire les valeurs continues|Prédire le prix des maisons en fonction de la taille et de l’emplacement|
|Détection d’anomalie|Détecter les transactions bancaires frauduleuses |
|Recommandations|Suggérer des produits que les acheteurs en ligne peuvent souhaiter acheter, en fonction de leurs achats précédents|

### <a name="how-to-execute-r-scripts"></a>Comment exécuter des scripts R

Il existe deux façons d’exécuter des scripts R dans R services:

+ La méthode la plus courante consiste à utiliser la procédure stockée T-SQL [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Vous pouvez également utiliser votre client R préféré et écrire des scripts qui poussent l’exécution (désignée sous le terme de *contexte de calcul distant*) à une SQL Server distante. Pour plus d’informations, consultez Guide pratique pour [configurer un développement R client](../r/set-up-a-data-science-client.md) pour la science des données.

<a name="packages"></a>

## <a name="r-packages"></a>Packages R

Vous pouvez utiliser des infrastructures et des packages Open source, en plus des packages d’entreprise Microsoft. Les packages R Open source les plus courants sont pré-installés dans R services. Les packages R suivants de Microsoft sont également inclus :

| Package | Description |
|-|-|
| [RevoScaleR](../r/ref-r-revoscaler.md) | Package principal pour les transformations et manipulations R. Data extensibles, synthèse statistique, visualisation et nombreuses formes de modélisation. En outre, les fonctions de ce package distribuent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle. |
| [MicrosoftML (R)](../r/ref-r-microsoftml.md) | Ajoute des algorithmes de Machine Learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments. |
| [olapR](../r/ref-r-olapr.md) | Fonctions R utilisées pour les requêtes MDX sur un cube SQL Server Analysis Services OLAP. |
| [sqlrutils](../r/ref-r-sqlrutils.md) | Mécanisme permettant d’utiliser des scripts R dans une procédure stockée T-SQL, d’enregistrer cette procédure stockée avec une base de données et d’exécuter la procédure stockée à partir d’un [environnement de développement R](../r/set-up-a-data-science-client.md). |
| [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) est la distribution améliorée de R de Microsoft. Il s’agit d’une plateforme open source complète pour l’analyse statistique et la science des données. Il est basé sur R et totalement compatible avec ce langage, et il inclut des capacités supplémentaires pour améliorer les performances et la reproductibilité. |

## <a name="how-do-i-get-started-with-rservices"></a>Comment faire prise en main de RServices?

1. [Installer SQL Server 2016 R services](../install/sql-r-services-windows-install.md)

1. Configurez vos outils de développement. Vous pouvez utiliser les éléments suivants:

    + [Azure Data Studio](../../azure-data-studio/what-is.md) ou [SQL Server Management Studio (SSMS)](../../ssms/sql-server-management-studio-ssms.md) pour utiliser T-SQL et la procédure stockée [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour exécuter votre script R.
    + R sur votre propre ordinateur portable ou station de travail de développement pour exécuter des scripts. Vous pouvez extraire des données localement ou envoyer l’exécution à distance pour SQL Server avec [RevoScaleR](../r/ref-r-revoscaler.md). Pour plus d’informations, consultez Guide pratique pour [configurer un développement R client](../r/set-up-a-data-science-client.md) pour la science des données.

1. Écrire votre premier script R

    + Démarrage rapide : [Exécuter un script «Hello World» dans R](../tutorials/quickstart-r-run-using-tsql.md)
    + Démarrage rapide : [Créer un modèle prédictif dans R](../tutorials/quickstart-r-create-predictive-model.md)
    + Tutoriel : [Utilisez R dans T-SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md): Explorez les données, effectuez l’ingénierie des caractéristiques, formez et déployez des modèles, puis faites des prédictions (série de cinq parties)
    + Tutoriel : [Utiliser r services dans les outils r](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md): Explorez les données, créez des graphiques et des tracés, effectuez l’ingénierie des caractéristiques, formez et déployez des modèles, puis Élaborez des prédictions (série en six parties)

## <a name="next-steps"></a>Étapes suivantes

+ [Installer SQL Server 2016 R services](../install/sql-r-services-windows-install.md)
+ [Configurer un client de science des données pour le développement R](../r/set-up-a-data-science-client.md)