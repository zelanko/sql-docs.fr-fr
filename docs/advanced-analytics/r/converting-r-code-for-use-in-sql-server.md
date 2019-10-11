---
title: Convertir du code R pour des procédures stockées
description: Migrer du code R vers une procédure stockée SQL Server pour le déploiement de solutions et l’accès aux données relationnelles sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 713c5cc8de5daecec77ff984a22f85b220ece2a2
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251346"
---
# <a name="convert-r-code-for-execution-in-sql-server-in-database-instances"></a>Convertir le code R pour l’exécuter dans les instances SQL Server (dans la base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fournit des conseils de haut niveau sur la façon de modifier le code R pour qu’il fonctionne dans SQL Server. 

Lorsque vous déplacez du code R à partir de R Studio ou d’un autre environnement vers SQL Server, le plus souvent, le code fonctionne sans modification supplémentaire : par exemple, si le code est simple, tel qu’une fonction qui prend des entrées et retourne une valeur. Il est également plus facile de porter des solutions qui utilisent les packages **RevoScaleR** ou **MicrosoftML** , qui prennent en charge l’exécution dans différents contextes d’exécution avec des modifications minimes.

Toutefois, votre code peut nécessiter des modifications substantielles si l’une des conditions suivantes s’applique :

+ Vous utilisez les bibliothèques R qui accèdent au réseau ou qui ne peuvent pas être installées sur SQL Server.
+ Le code effectue des appels distincts à des sources de données en dehors de SQL Server, tels que des feuilles de calcul Excel, des fichiers sur des partages et d’autres bases de données. 
+ Vous souhaitez exécuter le code dans le paramètre *\@Script* de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) et paramétrer également la procédure stockée.
+ Votre solution d’origine comprend plusieurs étapes qui peuvent être plus efficaces dans un environnement de production si elles sont exécutées indépendamment, telles que la préparation des données ou l’ingénierie des caractéristiques, ainsi que la formation du modèle, le score ou la création de rapports.
+ Vous souhaitez améliorer les performances d’optimisation en modifiant les bibliothèques, en utilisant une exécution parallèle ou en déchargeant un traitement à SQL Server. 

## <a name="step-1-plan-requirements-and-resources"></a>Étape 1. Planifier les exigences et les ressources

**Packages**

+ Déterminez les packages nécessaires et assurez-vous qu’ils fonctionnent sur SQL Server.
 
+ Installer les packages à l’avance, dans la bibliothèque de packages par défaut utilisée par Machine Learning Services. Les bibliothèques utilisateur ne sont pas prises en charge.

**Sources de données** 

+ Si vous envisagez d’incorporer votre code R dans [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), identifiez les sources de données primaires et secondaires. 

    + Les sources de données **principales** sont des jeux de données volumineux, tels que des données d’apprentissage de modèle ou des données d’entrée pour les prédictions. Planifiez le mappage de votre jeu de données le plus volumineux au paramètre d’entrée de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Les sources de données **secondaires** sont généralement des jeux de données plus petits, tels que des listes de facteurs ou des variables de regroupement supplémentaires. 
    
    Actuellement, sp_execute_external_script ne prend en charge qu’un seul jeu de données comme entrée de la procédure stockée. Toutefois, vous pouvez ajouter plusieurs entrées scalaires ou binaires.

    Les appels de procédure stockée précédés par EXECUTe ne peuvent pas être utilisés en tant qu’entrée dans [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Vous pouvez utiliser des requêtes, des vues ou toute autre instruction SELECT valide.

+ Déterminez les sorties dont vous avez besoin. Si vous exécutez le code R à l’aide de sp_execute_external_script, la procédure stockée peut générer une seule trame de données en conséquence. Toutefois, vous pouvez également générer plusieurs sorties scalaires, y compris des tracés et des modèles au format binaire, ainsi que d’autres valeurs scalaires dérivées du code R ou des paramètres SQL.

**Types de données**

+ Dressez une liste des problèmes possibles liés aux types des données.

    Tous les types de données R sont pris en charge par les services SQL Server machine learning. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge un plus grand nombre de types de données que R. Par conséquent, certaines conversions de types de données implicites sont effectuées lors de l’envoi de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à R, et vice versa. Vous devrez peut-être effectuer un cast ou une conversion explicite de certaines données. 

    Les valeurs NULL sont prises en charge. Toutefois, R utilise la construction de données `na` pour représenter une valeur manquante, qui est similaire à une valeur null.

+ Envisagez d’éliminer la dépendance vis-à-vis des données qui ne peuvent pas être utilisées par R : par exemple, les types de données ROWID et GUID de SQL Server ne peuvent pas être consommés par R et génèrent des erreurs.

    Pour plus d’informations, consultez [bibliothèques et types de données R](../r/r-libraries-and-data-types.md).

## <a name="step-2-convert-or-repackage-code"></a>Étape 2. Convertir ou reconditionner du code

La modification de votre code varie selon que vous envisagez de soumettre le code R à partir d’un client distant pour qu’il s’exécute dans le contexte de calcul SQL Server, ou que vous envisagez de déployer le code dans le cadre d’une procédure stockée, ce qui peut améliorer les performances et la sécurité des données. L’encapsulation de votre code dans une procédure stockée impose des exigences supplémentaires. 

+ Définissez vos données d’entrée principales en tant que requête SQL, dans la mesure du possible, afin d’éviter le déplacement des données.

+ Lors de l’exécution de R dans une procédure stockée, vous pouvez passer par plusieurs entrées **scalaires** . Pour tous les paramètres que vous souhaitez utiliser dans la sortie, ajoutez le mot clé **Output** . 

    Par exemple, l’entrée scalaire suivante `@model_name` contient le nom du modèle, qui est également généré dans sa propre colonne dans les résultats :

    ```sql
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ Toutes les variables que vous transmettez en tant que paramètres de la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) doivent être mappées à des variables dans le code R. Par défaut, les variables sont mappées par nom.

    Toutes les colonnes du jeu de données d’entrée doivent également être mappées à des variables dans le script R.  Par exemple, supposons que votre script R contient une formule similaire à celle-ci :

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    Une erreur est générée si le jeu de données d’entrée ne contient pas de colonnes avec les noms correspondants ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour et DayOfWeek.

+ Dans certains cas, un schéma de sortie doit être défini à l’avance pour les résultats.

    Par exemple, pour insérer les données dans une table, vous devez utiliser la clause **with result Set** pour spécifier le schéma.

    Le schéma de sortie est également requis si le script R utilise l’argument `@parallel=1`. Cela s’explique par le fait que plusieurs processus peuvent être créés par SQL Server pour exécuter la requête en parallèle et collecter les résultats à la fin. Par conséquent, le schéma de sortie doit être préparé pour que les processus parallèles puissent être créés.
    
    Dans d’autres cas, vous pouvez omettre le schéma de résultat à l’aide de l’option **avec des jeux de résultats non définis**. Cette instruction retourne le DataSet à partir du script R sans nommer les colonnes ou en spécifiant les types de données SQL.

+ Envisagez de générer des données de minutage ou de suivi à l’aide de T-SQL plutôt que de R.

    Par exemple, vous pouvez transmettre l’heure système ou d’autres informations utilisées pour l’audit et le stockage en ajoutant un appel T-SQL qui est transmis aux résultats, plutôt que de générer des données similaires dans le script R. 

**Améliorez les performances et la sécurité**

+ Évitez d’écrire des prédictions ou des résultats intermédiaires dans un fichier. Écrivez plutôt des prédictions dans une table, afin d’éviter le déplacement des données.

+ Exécutez toutes les requêtes à l’avance et passez en revue les SQL Server plans de requête pour identifier les tâches qui peuvent être effectuées en parallèle.

    Si la requête d’entrée peut être parallélisée, définissez `@parallel=1` dans le cadre de vos arguments à [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). 

    Le traitement parallèle avec cet indicateur est généralement possible quand SQL Server peut utiliser des tables partitionnées ou distribuer une requête entre plusieurs processus et agréger les résultats à la fin. En revanche, il n’est généralement pas possible si vous effectuez l’apprentissage de modèles à l’aide d’algorithmes qui nécessitent la lecture de toutes les données, ou si vous avez besoin de créer des agrégats.

+ Examinez votre code R pour déterminer si certaines étapes peuvent être effectuées séparément, ou de manière plus efficace, à l’aide d’un appel de procédure stockée distinct. Par exemple, vous pouvez obtenir de meilleures performances en procédant séparément à l’ingénierie des fonctionnalités ou à l’extraction de fonctionnalités, et en enregistrant les valeurs dans une table.

+ Recherchez des moyens d’utiliser T-SQL plutôt que du code R pour les calculs basés sur un ensemble.

    Par exemple, cette solution R montre comment les fonctions T-SQL définies par l’utilisateur et R peuvent effectuer la même tâche d’ingénierie des fonctionnalités : [Procédure pas à pas de bout en bout de la science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md).

+ Si possible, remplacez les fonctions R conventionnelles par des fonctions **scaler** qui prennent en charge l’exécution distribuée. Pour plus d’informations, consultez [comparaison des fonctions r de base et](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)r.

+ Consultez un développeur de base de données pour déterminer les moyens d’améliorer les performances en utilisant des fonctionnalités de SQL Server telles que les [tables optimisées en mémoire](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)ou, si vous disposez de l’édition Enterprise, [Resource Governor](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor)).

    Pour plus d’informations, consultez [SQL Server conseils et astuces d’optimisation pour Analytics services](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

### <a name="step-3-prepare-for-deployment"></a>Étape 3. Préparer le déploiement

+ Prévenez l’administrateur afin que vous puissiez installer et tester les packages avant le déploiement de votre code. 

    Dans un environnement de développement, il peut être possible d’installer des packages dans le cadre de votre code, mais il s’agit d’une mauvaise pratique dans un environnement de production. 

    Les bibliothèques utilisateur ne sont pas prises en charge, que vous utilisiez une procédure stockée ou que vous exécutiez du code R dans le contexte de calcul SQL Server.

**Empaqueter votre code R dans une procédure stockée**

+ Si votre code est relativement simple, vous pouvez l’incorporer dans une fonction T-SQL définie par l’utilisateur sans modification, comme décrit dans les exemples suivants :

    + [Créer une fonction R qui s’exécute dans rxExec](../tutorials/deepdive-create-a-simple-simulation.md)
    + [Ingénierie des caractéristiques à l’aide de T-SQL et R](../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Si le code est plus complexe, utilisez le package R **sqlrutils** pour convertir votre code. Ce package est conçu pour aider les utilisateurs expérimentés à écrire du code de procédure stockée efficace. 

    La première étape consiste à réécrire votre code R sous la forme d’une fonction unique avec des entrées et des sorties clairement définies.

    Ensuite, utilisez le package **sqlrutils** pour générer l’entrée et les sorties dans le format correct. Le package **sqlrutils** génère le code complet de la procédure stockée et peut également inscrire la procédure stockée dans la base de données. 

    Pour plus d’informations et d’exemples, consultez [sqlrutils (SQL)](ref-r-sqlrutils.md).

**Intégrer à d’autres workflows**

+ Tirez parti des outils T-SQL et des processus ETL. Procédez à l’ingénierie des fonctionnalités, à l’extraction des fonctionnalités et au nettoyage des données à l’avance dans le cadre des flux de travail de données.

    Lorsque vous travaillez dans un environnement de développement R dédié, tel que [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] ou RStudio, vous pouvez extraire des données sur votre ordinateur, analyser les données de manière itérative, puis écrire ou afficher les résultats. 
    
    Toutefois, lorsque le code R autonome est migré vers SQL Server, une grande partie de ce processus peut être simplifiée ou déléguée à d’autres outils SQL Server. 

+ Utilisez des stratégies de visualisation asynchrones et sécurisées.

    Les utilisateurs de SQL Server souvent pas accéder aux fichiers sur le serveur, et les outils clients SQL ne prennent généralement pas en charge le périphérique graphique R. Si vous générez des tracés ou d’autres graphiques dans le cadre de la solution, envisagez d’exporter les tracés sous forme de données binaires et d’enregistrer dans une table, ou d’écrire.

+ Encapsulez les fonctions de prédiction et de score des procédures stockées pour un accès direct par les applications.

### <a name="other-resources"></a>Autres ressources

Pour obtenir des exemples de déploiement d’une solution R dans SQL Server, consultez les exemples suivants :

+ [Créez un modèle prédictif pour l’activité de location de ski à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Analytique en base de données pour le développeur SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) Montre comment vous pouvez rendre votre code R plus modulaire en l’encapsulant dans des procédures stockées

+ [Solution de science des données de bout en bout](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) Comprend une comparaison de l’ingénierie des fonctionnalités dans R et T-SQL
