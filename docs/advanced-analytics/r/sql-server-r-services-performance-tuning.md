---
title: Réglage des performances de R
description: Cet article décrit l’optimisation des performances pour R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4d7b6b91ac3aeaa45c5e6c3e05c12176f5f60b28
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727362"
---
# <a name="performance-tuning-for-r-in-sql-server"></a>Optimisation des performances pour R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article est le premier d’une série de quatre articles qui décrivent l’optimisation des performances pour R Services sur la base de deux études de cas :

- Tests de performances effectués par l’équipe de développement de produit pour valider le profil de performances des solutions R

- Optimisation des performances par l’équipe de science des données Microsoft pour un scénario de Machine Learning spécifique souvent demandé par les clients.

L’objectif de cette série est de fournir des conseils sur les types de techniques de réglage des performances qui sont les plus utiles pour l’exécution de travaux R dans SQL Server.

+ Cette (première) rubrique fournit une vue d’ensemble de l’architecture et de certains problèmes courants lors de l’optimisation des tâches de science des données.
+ Le deuxième article traite des optimisations matérielles et SQL Server spécifiques.
+ Le troisième article traite des optimisations dans le code R et des ressources pour l’opérationalisation.
+ Le quatrième article décrit les méthodes de test en détail et mentionne les résultats et les conclusions.

**S’applique à :** SQL Server 2016 R Services, SQL Server Machine Learning Services

## <a name="performance-goals-and-targeted-scenarios"></a>Objectifs de performances et scénarios ciblés

La fonctionnalité R Services a été introduite dans SQL Server 2016 pour prendre en charge l’exécution de scripts R par SQL Server. Lorsque vous utilisez cette fonctionnalité, le runtime R fonctionne dans un processus distinct du moteur de base de données, mais échange des données en toute sécurité avec le moteur de base de données, à l’aide des ressources serveur et des services qui interagissent avec SQL Server, tel que le Launchpad approuvé.

Dans SQL Server 2017, la prise en charge a été annoncée pour l’exécution de scripts Python via la même architecture, dont des langues supplémentaires à venir.

À mesure que le nombre de versions et de langues prises en charge augmente, il est important que l’administrateur de base de données et l’architecte de base de données soient conscients du potentiel de contention des ressources en raison des tâches de Machine Learning et qu’ils sont en mesure de configurer le serveur pour prendre en charge les nouvelles charges de travail. Bien que la conservation des analyses à proximité des données élimine les mouvements de données non sécurisés, elle déplace également les charges de travail analytiques de l’ordinateur portable du scientifique de données vers le serveur qui héberge les données.

L’optimisation des performances pour Machine Learning n’est clairement pas une proposition unique. Les tâches courantes suivantes peuvent avoir des profils de performances très différents :

- Tâches de formation : création et entraînement d’un modèle de régression et apprentissage d’un réseau neuronal
- Ingénierie de fonctionnalités utilisant R et extraction de fonctionnalités à l’aide de T-SQL
- Scoring sur des lignes simples ou des lots de petite taille et scoring en bloc à l’aide d’entrées tabulaires
- Exécution du scoring dans R et déploiement de modèles en production sur SQL Server dans des procédures stockées
- Modification du code R pour réduire le transfert de données ou supprimer les transformations de données coûteuses
- Activer les tests automatisés et la reformation des modèles

Étant donné que le choix des techniques d’optimisation dépend de la tâche qui est essentielle à votre application ou cas d’usage, les études de cas couvrent des conseils généraux en matière de performances et des conseils sur l’optimisation pour un scénario spécifique, l’optimisation du scoring par lot.

+ **Options d’optimisation individuelles dans SQL Server**

    Dans la première étude de cas sur les performances, plusieurs tests ont été exécutés sur un seul jeu de données à l’aide d’un seul type de modèle. L’algorithme rxLinMod dans RevoscaleR a été utilisé pour générer un modèle et créer des scores à partir de celui-ci, mais le code, ainsi que les tables de données sous-jacentes ont été modifiés systématiquement pour tester l’impact de chaque modification.

    Par exemple, dans une série de tests, le code R a été modifié afin d’établir une comparaison entre l’ingénierie des fonctionnalités à l’aide d’une fonction de transformation et le précalcul des fonctionnalités, puis le chargement des fonctionnalités à partir d’une table. Dans une autre série de tests, les performances d’apprentissage du modèle ont été comparées, entre l’utilisation d’une table indexée standard et les données d’une table avec différents types de compression ou de nouveaux types d’index.

+ **Optimisation pour un scénario de scoring à volume élevé spécifique**

    La tâche Machine Learning dans la deuxième étude de cas implique le traitement de plusieurs CV pour plusieurs postes et la recherche du meilleur candidat pour chaque poste de travail. Le modèle de Machine Learning lui-même est formulé comme un problème de classification binaire : il accepte un CV et une description de l’emploi comme entrée, et génère la probabilité pour chaque paire CV-emploi. Étant donné que l’objectif est de trouver la meilleure correspondance, un seuil de probabilité défini par l’utilisateur est utilisé pour filtrer davantage et obtenir uniquement les bonnes correspondances.

    Pour cette solution, l’objectif principal consistait à atteindre une faible latence pendant le scoring. Toutefois, cette tâche est coûteuse en termes de calcul, même pendant le processus de scoring, car chaque nouvel emploi doit être mis en correspondance avec des millions de CV dans un délai raisonnable. En outre, l’étape d’ingénierie des fonctionnalités génère plus de 2 000 fonctionnalités par CV ou emploi, et représente un goulot d’étranglement significatif pour les performances.

Nous vous suggérons de passer en revue tous les résultats de la première étude de cas pour déterminer quelles techniques sont applicables à votre solution et peser leur impact potentiel.

Passez ensuite en revue les résultats de l’étude de cas d’optimisation du score pour voir comment l’auteur a appliqué différentes techniques et a optimisé le serveur afin qu’il prenne en charge une charge de travail particulière.

## <a name="performance-optimization-process"></a>Processus d’optimisation des performances

La configuration et l’optimisation des performances requièrent la création d’une base solide, sur laquelle on applique des couches d’optimisations conçues pour des charges de travail spécifiques :

- Choisissez un serveur approprié pour héberger l’analyse. En règle générale, il est préférable d’utiliser un entrepôt de données secondaire ou un autre serveur de rapports qui est déjà utilisé pour d’autres rapports ou analytiques. Toutefois, dans une solution de traitement analytique transactionnel hybride (HTAP), les données opérationnelles peuvent être utilisées comme entrée pour R pour un scoring rapide.

- Configurez l’instance SQL Server pour équilibrer les opérations du moteur de base de données et l’exécution des scripts R ouPython aux niveaux appropriés. Cela peut inclure la modification des paramètres SQL Server par défaut pour la mémoire et l’utilisation du processeur, les paramètres NUMA et l’affinité du processeur, ainsi que la création de groupes de ressources.

- Optimisez l’ordinateur serveur pour qu’il prenne en charge l’utilisation efficace des scripts externes. Cela peut inclure l’ajout du nombre de comptes utilisés pour l’exécution de scripts externes, l’activation de la gestion des packages et l’attribution d’utilisateurs aux rôles de sécurité associés.

- Application d’optimisations spécifiques au stockage et au transfert de données dans SQL Server, y compris les stratégies d’indexation et de statistiques, la conception de requêtes et l’optimisation des requêtes, ainsi que la conception de tables utilisées pour la Machine Learning. Vous pouvez également analyser les sources de données et les méthodes de transport des données, ou modifier les processus ETL pour optimiser l’extraction des fonctionnalités.

- Paramétrez le modèle analytique pour éviter les inefficacités. La portée des optimisations possibles dépend de la complexité de votre code R et des packages et des données que vous utilisez. Les tâches principales incluent l’élimination des transformations de données coûteuses ou le déchargement des tâches de préparation des données ou d’ingénierie des fonctionnalités de R ou Python vers des processus ETL ou SQL. Vous pouvez également refactoriser des scripts, éliminer des installations de packages en ligne, diviser du code R en procédures distinctes d’apprentissage, de scoring et d’évaluation, ou simplifier le code pour qu’il soit plus efficace en tant que procédure stockée.

## <a name="articles-in-this-series"></a>Articles de cette série

+ [Optimisation des performances pour R dans SQL Server - matériel](../r/sql-server-configuration-r-services.md)

    Fournit des instructions pour configurer le matériel sur lequel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est installé et pour configurer l’instance SQL Server afin de mieux prendre en charge les scripts externes. C’est particulièrement utile pour les **administrateurs de base de données**.

+ [Optimisation des performances pour R dans SQL Server- Code et optimisation des données](../r/r-and-data-optimization-r-services.md)

    Fournit des conseils spécifiques sur l’optimisation du script externe afin d’éviter les problèmes connus. Il s’adresse essentiellement aux **scientifiques des données**.

    > [!NOTE]
    > Bien que la majeure partie de cette section s’applique à R en général, elle contient aussi des informations plus spécifiques sur les fonctions analytiques RevoScaleR. Les conseils détaillés sur les performances ne sont pas disponibles pour **revoscalepy** et d’autres bibliothèques Python prises en charge.
    >

+ [Optimisation des performances pour R dans SQL Server - méthodes et résultats](../r/performance-case-study-r-services.md)

    Fait un résumé des données utilisées par les deux études de cas, comment les performances ont été testées et comment les optimisations ont affecté les résultats.
