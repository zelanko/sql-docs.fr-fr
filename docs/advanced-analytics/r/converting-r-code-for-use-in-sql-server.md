---
title: Conversion de code R pour une utilisation dans R Services | Microsoft Doc
ms.custom: SQL2016_New_Updated
ms.date: 06/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d403b716d6be6c571f4de76a25ba3f6f7f5c4e8d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="converting-r-code-for-use-in-r-services"></a>Conversion de code R pour une utilisation dans R Services

Lorsque vous déplacez le code R à partir de R Studio ou un autre environnement pour SQL Server, souvent le code fonctionne sans modification supplémentaire lors de l’ajout à la  *@script*  paramètre de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Cela est particulièrement vrai si vous avez développé votre solution à l’aide de la **RevoScaleR** fonctions, rendant relativement simple modifier les contextes d’exécution.

Toutefois, vous modifiez généralement votre code R à exécuter dans SQL Server, à la fois pour profiter des avantages de l’intégration plus étroite avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour éviter les coûteux transferts de données.

Pour voir des exemples d’exécution de code R dans SQL Server, consultez ces procédures pas à pas :

+ [Analytique dans base de données pour le développeur SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) montre comment vous pouvez effectuer votre code R plus modulaire en l’encapsulant dans les procédures stockées

+ [Solution de science des données de bout en bout](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) inclut une comparaison d’ingénierie de fonctionnalité dans R et T-SQL

## <a name="how-the-data-science-process-changes-in-sql-server"></a>Comment le processus de science des données changent dans SQL Server

Lorsque vous travaillez dans un environnement de développement R dédié comme [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] ou RStudio, le processus habituel consiste à extraire des données sur votre ordinateur, analyser les données de manière itérative, puis écrire ou afficher les résultats. Toutefois, lorsque le code de R autonome est migré vers SQL Server, une grande partie de ce processus peut être simplifiée ou déléguée à d’autres outils de SQL Server. En outre, cela peut améliorer les performances dans de nombreux cas.

| Code externe | R dans SQL Server |
|-------|-------|
| Réception des données| Définir les données d’entrée comme une requête SQL. Éviter le déplacement des données. |
| Résumé et visualisation des données| Graphiques peuvent être exportées en tant qu’images ou envoyées à une station de travail distante.|
|Ingénierie des caractéristiques| Utiliser R dans la base de données si vous ne souhaitez pas modifier votre code, mais consultez Optimisation de vos requêtes. Examiner si elle peut être plus efficace d’appeler des fonctions T-SQL ou UDF personnalisés.|
|Nettoyage des données (étape du processus d’analyse)| Effectuer une ingénierie de fonctionnalité, d’extraction de fonctionnalité et de nettoyage des données à l’avance en tant que partie du flux de travail de données.|
|Sortie des prédictions dans un fichier| Prédictions de sortie à une table afin d’éviter le déplacement des données. Retour à la ligne des fonctions dans les procédures stockées pour l’accès direct de prédiction par les applications.|

## <a name="best-practices"></a>Meilleures pratiques

+ Notez à l’avance les dépendances telles que les packages dont vous aurez besoin. Dans un environnement de développement et de test, vous pouvez éventuellement installer les packages dans votre code, mais ce n’est pas une bonne pratique dans un environnement de production. Prévenez l’administrateur afin que vous puissiez installer et tester les packages avant le déploiement de votre code.

+ Dressez une liste des problèmes possibles liés aux types des données. Le schéma des résultats attendus de chaque section du code de document.

+ Distinguez les sources de données principales, telles que les données d’apprentissage du modèle ou les données d’entrée utilisées pour les prédictions, des sources de données secondaires, telles que les facteurs, les variables de regroupement supplémentaires, etc. Mappez votre plus grand jeu de données au paramètre d’entrée de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Modifiez vos instructions de données d’entrée pour qu’elles s’exécutent directement dans la base de données. Plutôt que le déplacement des données vers un fichier de volume partagé de cluster local, soit en effectuant répété appels ODBC, vous pouvez obtenir de meilleures performances à l’aide de requêtes SQL ou les vues qui peuvent être exécutées directement sur la base de données, en évitant le déplacement de données.

+ Utilisez des plans de requête SQL Server pour identifier les tâches qui peuvent être effectuées en parallèle. Si la requête d’entrée peut être parallélisée, définissez `@parallel=1` dans le cadre de vos arguments à [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Le traitement parallèle avec cet indicateur est généralement possible quand SQL Server peut utiliser des tables partitionnées ou distribuer une requête entre plusieurs processus et agréger les résultats à la fin.

  En revanche, il n’est généralement pas possible si vous effectuez l’apprentissage de modèles à l’aide d’algorithmes qui nécessitent la lecture de toutes les données, ou si vous avez besoin de créer des agrégats.

+ Quand vous le pouvez, remplacez les fonctions R standard par des fonctions **ScaleR** qui prennent en charge l’exécution distribuée. Pour plus d’informations, consultez [comparaison de Base de R et des fonctions R échelle](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler-compared-to-base-r).

+ Examinez votre code R pour déterminer si certaines étapes peuvent être effectuées séparément, ou de manière plus efficace, à l’aide d’un appel de procédure stockée distinct. Par exemple, vous pouvez choisir d’effectuer l’ingénierie ou l’extraction des caractéristiques séparément et d’ajouter les valeurs dans une nouvelle colonne. 

  Utilisez T-SQL au lieu du code R pour effectuer des calculs reposant sur des ensembles. Pour obtenir un exemple d’une solution R qui compare des UDF et R pour des tâches ingénierie de fonctionnalité, consultez [procédure pas à pas au bout de science des données](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md).

+ Utilisez le package R **sqlrutils** pour convertir votre code en une seule fonction avec clairement entrées et sorties, ce qui peuvent être facilement mappées à des paramètres de procédure stockée. Pour plus d’informations et d’exemples, consultez [SqlRUtils](../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).


## <a name="restrictions"></a>Restrictions

 Quand vous convertissez du code R, tenez compte des restrictions suivantes :

### <a name="data-types"></a>Types de données

-   Tous les types de données R sont pris en charge. Du fait que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge davantage de types de données que R, des conversions de types de données sont parfois effectuées de façon implicite quand vous transférez des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et R. Vous devrez peut-être convertir explicitement ou de convertir certaines données.

- Les valeurs NULL sont prises en charge. R utilise le `na` construction de données pour représenter une valeur manquante, qui est similaire à une valeur null.

Pour plus d’informations, consultez [les Types de données et les bibliothèques R](../r/r-libraries-and-data-types.md).

### <a name="inputs-and-outputs"></a>Entrées et sorties

+ Vous pouvez définir un seul jeu de données d’entrée dans les paramètres d’une procédure stockée. Cette requête d’entrée de la procédure stockée doit être une instruction SELECT unique valide. Nous vous recommandons d’utiliser cette entrée pour le plus grand jeu de données et d’obtenir des jeux de données plus petits en fonction des besoins à l’aide d’appels à RODBC.

+ Précédé d’exécuter des appels de procédure stockée ne peut pas être utilisés en tant qu’entrée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Toutes les colonnes dans le jeu de données d’entrée doivent être mappées à des variables dans le script R. Les variables sont automatiquement mappées par nom. Par exemple, supposons que votre script R contient une formule comme celle-ci :
    
    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
     Une erreur est générée si le jeu de données d’entrée ne contient pas de colonnes avec la correspondance des noms ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour et DayOfWeek.

+ Vous pouvez également fournir plusieurs paramètres scalaires comme entrée. Toutefois, toutes les variables que vous passez comme paramètres de la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) doivent être mappées à des variables dans le code R. Par défaut, les variables sont mappées par nom.

+ Pour inclure des variables d’entrée scalaires dans la sortie du code R, ajoutez simplement le mot clé **OUTPUT** à la variable que vous définissez.

+ Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], votre code R peut générer un seul jeu de données sous la forme d’un objet data.frame. Toutefois, vous pouvez également générer plusieurs sorties scalaires, y compris des tracés au format binaire et des modèles au format varbinary.

+ Vous pouvez généralement générer le jeu de données retourné par le script R sans avoir à spécifier les noms des colonnes de sortie, à l’aide de l’option WITH RESULT SETS UNDEFINED. Toutefois, toutes les variables du script R que vous souhaitez générer doivent être mappées à des paramètres de sortie SQL.

+ Si votre script R utilise l’argument `@parallel=1`, vous devez définir le schéma de sortie. Cela s’explique par le fait que plusieurs processus peuvent être créés par SQL Server pour exécuter la requête en parallèle et collecter les résultats à la fin. Par conséquent, le schéma de sortie doit être défini avant de pouvoir créer les processus parallèles.

### <a name="dependencies"></a>Dépendances

 + N’installez pas de packages à partir du code R. Sur le serveur SQL Server, les packages doivent être installés à l’avance.
 
  Veillez à installer des packages dans la bibliothèque de package par défaut utilisée par les Services de Machine Learning. Pour plus d’informations, consultez [gestion des packages R pour SQL Server](../r/r-package-management-for-sql-server-r-services.md)
