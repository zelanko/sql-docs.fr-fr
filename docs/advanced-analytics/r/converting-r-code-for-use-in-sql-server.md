---
title: Convertir le code R pour les procédures stockées - SQL Server Machine Learning Services
description: Migrer le code R à une procédure stockée SQL Server pour la solution déploiement et accès aux données à des données relationnelles sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a3348058b03ff1441256cc8298ddc1b5b2216b0d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642791"
---
# <a name="convert-r-code-for-execution-in-sql-server-in-database-instances"></a>Convertir le code R pour l’exécution dans les instances SQL Server (en base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit des instructions détaillées sur la façon de modifier le code R fonctionne dans SQL Server. 

Lorsque vous déplacez le code R à partir de R Studio ou un autre environnement vers SQL Server, plus souvent le code fonctionne sans modification supplémentaire : par exemple, si le code est simple, comme une fonction qui accepte certaines entrées et retourne une valeur. Il est également plus facile pour les solutions de port qui utilisent le **RevoScaleR** ou **MicrosoftML** packages, qui prennent en charge l’exécution dans différents contextes d’exécution avec un minimum de modifications.

Toutefois, votre code peut nécessiter des modifications substantielles si une des situations suivantes se présente :

+ Vous utilisez les bibliothèques R qui accèdent au réseau ou qui ne peut pas être installé sur SQL Server.
+ Le code effectue des appels distincts à des sources de données en dehors de SQL Server, tels que des feuilles de calcul Excel, des fichiers sur des partages et des autres bases de données. 
+ Vous souhaitez exécuter le code le *@script* paramètre de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) et également paramétrer la procédure stockée.
+ Votre solution d’origine comprend plusieurs étapes qui peuvent être plus efficaces dans un environnement de production si exécutée indépendamment, telles que la préparation des données ou de l’ingénierie et le modèle de formation, notation ou signaler.
+ Vous souhaitez améliorer optimiser les performances en ajustant les bibliothèques, à l’aide de l’exécution en parallèle ou déchargement d’un traitement à SQL Server. 

## <a name="step-1-plan-requirements-and-resources"></a>Étape 1. Planifier la configuration requise et ressources

**Packages**

+ Déterminer quels packages sont nécessaires et vous assurer qu’elles fonctionnent sur SQL Server.
 
+ Installer des packages à l’avance, dans la bibliothèque de package par défaut utilisée par les Services Machine Learning. Bibliothèques utilisateur ne sont pas pris en charge.

**Sources de données** 

+ Si vous souhaitez incorporer votre code R dans [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), identifier les sources de données primaire et secondaire. 

    + **Principal** sources de données sont des jeux de données volumineux, tels que les données d’apprentissage de modèle, ou des données d’entrée pour les prédictions. Envisagez de mapper votre plus grand jeu de données vers le paramètre d’entrée de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + **Secondaire** sources de données sont généralement petits jeux de données, telles que les listes des facteurs ou des variables de regroupement supplémentaires. 
    
    Actuellement, sp_execute_external_script prend en charge uniquement un seul jeu de données en tant qu’entrée à la procédure stockée. Toutefois, vous pouvez ajouter plusieurs entrées de scalaires ou binaire.

    Précédé d’exécuter des appels de procédure stockée ne peut pas être utilisés en tant qu’entrée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Vous pouvez utiliser des requêtes, des vues ou toute autre instruction SELECT valide.

+ Déterminer les sorties que vous avez besoin. Si vous exécutez le code R à l’aide de sp_execute_external_script, la procédure stockée peut sortie ainsi qu’une trame de données. Toutefois, vous pouvez également générer plusieurs sorties scalaires, y compris des tracés et des modèles dans un format binaire, ainsi que d’autres valeurs scalaires dérivé des paramètres de code R ou SQL.

**Types de données**

+ Dressez une liste des problèmes possibles liés aux types des données.

    Tous les types de données R sont pris en charge par SQL Server machine Learning Services. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge une plus grande variété de types de données de R. Par conséquent, certaines conversions de types de données implicites sont effectuées lors de l’envoi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données R et vice versa. Vous devrez peut-être effectuer un cast ou de convertir certaines données explicitement. 

    Les valeurs NULL sont prises en charge. Toutefois, R utilise la `na` construction de données pour représenter une valeur manquante, qui est similaire à une valeur null.

+ Supprimez la dépendance sur les données qui ne peut pas être utilisées par r : par exemple, les ID de ligne et les types de données GUID à partir de SQL Server ne peut pas être consommés par R et génèrent des erreurs.

    Pour plus d’informations, consultez [les Types de données et les bibliothèques R](../r/r-libraries-and-data-types.md).

## <a name="step-2-convert-or-repackage-code"></a>Étape 2. Convertir ou recréez le package code

Combien vous modifiez votre code varie selon que vous avez l’intention de soumettre le code R à partir d’un client distant à exécuter dans le contexte de calcul SQL Server ou prévoyez de déployer le code dans le cadre d’une procédure stockée, ce qui peut fournir de meilleures performances et sécurité des données. Encapsulant votre code dans une procédure stockée impose certaines exigences supplémentaires. 

+ Définir vos données d’entrée principales en tant qu’une requête SQL dans la mesure du possible, afin d’éviter le déplacement des données.

+ Lors de l’exécution de R dans une procédure stockée, vous pouvez passer à travers plusieurs **scalaire** entrées. Pour tous les paramètres que vous souhaitez utiliser dans la sortie, ajoutez le **sortie** mot clé. 

    Par exemple, l’entrée scalaire suivante `@model_name` contient le nom du modèle, qui est également générée sous sa propre colonne dans les résultats :

    ```sql
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ Toutes les variables que vous passez comme paramètres de la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) doivent être mappés à des variables dans le code R. Par défaut, les variables sont mappées par nom.

    Toutes les colonnes dans le jeu de données d’entrée doivent également être mappées à des variables dans le script R.  Par exemple, supposons que votre script R contient une formule semblable à celle-ci :

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    Une erreur est générée si le jeu de données d’entrée ne contient pas de colonnes avec les noms correspondants ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour et DayOfWeek.

+ Dans certains cas, un schéma de sortie doit être défini à l’avance pour les résultats.

    Par exemple, pour insérer les données dans une table, vous devez utiliser le **avec jeu de résultats** clause pour spécifier le schéma.

    Le schéma de sortie est également requis si le script R utilise l’argument `@parallel=1`. Cela s’explique par le fait que plusieurs processus peuvent être créés par SQL Server pour exécuter la requête en parallèle et collecter les résultats à la fin. Par conséquent, le schéma de sortie doit être préparé avant que les processus parallèles peuvent être créés.
    
    Dans d’autres cas, vous pouvez omettre le schéma de résultats à l’aide de l’option **WITH RESULT SETS UNDEFINED**. Cette instruction retourne le jeu de données à partir du script R sans les colonnes d’affectation de noms ou en spécifiant les types de données SQL.

+ Envisagez de générer des données de minutage ou suivies à l’aide de T-SQL plutôt que R.

    Par exemple, vous pouvez passer l’heure système ou autres informations utilisées pour l’audit et le stockage en ajoutant un appel de T-SQL qui est transmis aux résultats, plutôt que de générer des données similaires dans le script R. 

**Améliorer les performances et sécurité**

+ Évitez d’écrire des prédictions ou des résultats intermédiaires dans le fichier. Écrire des prédictions dans une table à la place, afin d’éviter le déplacement des données.

+ Exécutez toutes les requêtes à l’avance et passez en revue les plans de requête SQL Server pour identifier les tâches qui peuvent être effectuées en parallèle.

    Si la requête d’entrée peut être parallélisée, définissez `@parallel=1` dans le cadre de vos arguments à [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). 

    Le traitement parallèle avec cet indicateur est généralement possible quand SQL Server peut utiliser des tables partitionnées ou distribuer une requête entre plusieurs processus et agréger les résultats à la fin. En revanche, il n’est généralement pas possible si vous effectuez l’apprentissage de modèles à l’aide d’algorithmes qui nécessitent la lecture de toutes les données, ou si vous avez besoin de créer des agrégats.

+ Examinez votre code R pour déterminer si certaines étapes peuvent être effectuées séparément, ou de manière plus efficace, à l’aide d’un appel de procédure stockée distinct. Par exemple, vous pouvez obtenir les meilleures performances en effectuant l’ingénierie des fonctionnalités d’extraction de fonctionnalités séparément et enregistrer les valeurs dans une table.

+ Recherchez des façons d’utiliser T-SQL plutôt que du code R pour effectuer des calculs en fonction de jeu.

    Par exemple, cette solution R montre comment défini par l’utilisateur des fonctions T-SQL et R peut effectuer la même tâche d’ingénierie de fonctionnalité : [Procédure pas à pas de données Science End-to-End](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md).

+ Si possible, remplacez les fonctions R standard avec **ScaleR** fonctions qui prennent en charge l’exécution distribuée. Pour plus d’informations, consultez [comparaison de Base R et de mise à l’échelle des fonctions R](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r).

+ Consulter un développeur de base de données pour déterminer les moyens d’améliorer les performances en utilisant les fonctionnalités de SQL Server comme [tables optimisées en mémoire](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables), ou, si vous avez Enterprise Edition, [du gouverneur de ressources](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor)).

    Pour plus d’informations, consultez [conseils d’optimisation de SQL Server et des astuces pour les Services d’Analytique](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

### <a name="step-3-prepare-for-deployment"></a>Étape 3. Préparer le déploiement

+ Prévenez l’administrateur afin que vous puissiez installer et tester les packages avant le déploiement de votre code. 

    Dans un environnement de développement, il peut être OK installer des packages dans le cadre de votre code, mais il s’agit d’une mauvaise pratique dans un environnement de production. 

    Bibliothèques utilisateur ne sont pas pris en charge, sont à l’aide d’une procédure stockée ou en exécutant le code R dans le contexte de calcul de SQL Server.

**Empaquetez votre code R dans une procédure stockée**

+ Si votre code est relativement simple, vous pouvez l’incorporer dans une fonction définie par l’utilisateur de T-SQL sans modification, comme décrit dans ces exemples :

    + [Créer une fonction R qui s’exécute dans rxExec](../tutorials/deepdive-create-a-simple-simulation.md)
    + [Ingénierie des fonctionnalités à l’aide de T-SQL et R](../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Si le code est plus complexe, utilisez le package R **sqlrutils** pour convertir votre code. Ce package est conçu pour aider les utilisateurs expérimentés de R à écrire du code de bon de procédure stockée. 

    La première étape consiste à réécrire votre code R en tant qu’une seule fonction avec clairement définie des entrées et sorties.

    Ensuite, utilisez le **sqlrutils** package pour générer l’entrée et les sorties dans le format correct. Le **sqlrutils** package génère le code de procédure stockée complète pour vous et peuvent également inscrire la procédure stockée dans la base de données. 

    Pour plus d’informations et des exemples, consultez [sqlrutils (SQL)](ref-r-sqlrutils.md).

**Intégrer avec d’autres workflows**

+ Tirez parti des outils de T-SQL et les processus ETL. Effectuer l’ingénierie, l’extraction de la fonctionnalité et nettoyage des données à l’avance en tant que partie du flux de travail de données.

    Lorsque vous travaillez dans un environnement de développement R dédié tel que [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] ou RStudio, vous pouvez extraire des données sur votre ordinateur, analyser les données de manière itérative, puis écrire ou afficher les résultats. 
    
    Toutefois, lorsque le code R autonome est migré vers SQL Server, une grande partie de ce processus peut être simplifiée ou déléguée à d’autres outils de SQL Server. 

+ Utiliser des stratégies de visualisation sécurisé et asynchrone.

    Fréquence à laquelle les utilisateurs de SQL Server ne peut pas accéder aux fichiers sur le serveur et outils clients SQL ne gèrent généralement pas le périphérique graphique R. Si vous générez des tracés ou des graphiques dans le cadre de la solution, envisagez d’exporter les tracés en tant que données binaires et de l’enregistrement dans une table ou d’écrire.

+ Retour à la ligne de prévision et les fonctions de scoring dans les procédures stockées pour un accès direct par les applications.

### <a name="other-resources"></a>Autres ressources

Pour afficher des exemples de la façon dont une solution de R peut être déployée dans SQL Server, consultez les exemples suivants :

+ [Créer un modèle prédictif pour entreprise de location de skis à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Analytique en base de données pour les développeurs SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) montre comment vous pouvez effectuer votre code R plus modulaire en l’encapsulant dans les procédures stockées

+ [Solution de science des données de bout en bout](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) inclut une comparaison de l’ingénierie dans R et T-SQL
