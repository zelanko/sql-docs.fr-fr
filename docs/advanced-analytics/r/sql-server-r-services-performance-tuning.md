---
title: Performances de SQL Server R Services paramétrage - Machine Learning Services SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e547e2cd3c50e020d1164dc2b8aaffb31f4e3cb8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641654"
---
# <a name="performance-tuning-for-r-in-sql-server"></a>Optimisation des performances pour R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article est le premier d’une série de quatre articles qui décrivent l’optimisation des performances pour R Services, en fonction de deux études de cas :

- Tests de performances effectués par l’équipe de développement de produit pour valider le profil de performance des solutions R

- Optimisation des performances par l’équipe de science des données Microsoft pour un scénario d’apprentissage spécifique souvent demandé par les clients.

L’objectif de cette série est de fournir des conseils sur les types de techniques qui sont particulièrement utiles pour l’exécution des travaux R dans SQL Server d’optimisation des performances.

+ Cette rubrique (première) fournit une vue d’ensemble de l’architecture et de certains problèmes courants lors de l’optimisation pour les tâches de science des données.
+ Le deuxième article couvre le matériel et les optimisations de SQL Server.
+ Le troisième article traite des optimisations dans le code R et des ressources pour l’Opérationnalisation.
+ Le quatrième article décrit les méthodes de test en détail et les résultats en matière de rapports et les conclusions.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

## <a name="performance-goals-and-targeted-scenarios"></a>Objectifs de performances et des scénarios ciblés

La fonctionnalité R Services a été introduite dans SQL Server 2016 pour prendre en charge l’exécution de scripts R par SQL Server. Lorsque vous utilisez cette fonctionnalité, le runtime R fonctionne dans un processus séparé à partir du moteur de base de données, mais il échange des données en toute sécurité avec le moteur de base de données, à l’aide des ressources du serveur et des services qui interagissent avec SQL Server, telles que le Launchpad approuvé.

Dans SQL Server 2017, la prise en charge a été annoncée pour exécuter des scripts Python à l’aide de la même architecture, avec des langues supplémentaires à suivre dans les futures.

Comme le nombre de versions prises en charge et la langue augmente, il est important que l’administrateur de base de données et l’architecte de base de données connaissent les risques de contention des ressources en raison de travaux de machine learning, et qu’ils sont en mesure de configurer le serveur pour prendre en charge les nouvelles charges de travail. Bien que la conservation d’analytique proche des données élimine les mouvements de données non sécurisé, il déplace également des charges de travail analytiques hors tension de l’ordinateur portable du chercheur de données et sur le serveur qui héberge les données.

Optimisation des performances pour l’apprentissage n’est pas une solution globale. Les tâches courantes suivantes peuvent avoir des profils de performances très différentes :

- Tâches d’apprentissage : création et l’apprentissage d’un modèle de régression et l’apprentissage d’un réseau neuronal
- Ingénierie des fonctionnalités à l’aide de R et l’extraction des caractéristiques à l’aide de T-SQL
- Notation sur les lignes uniques ou les petits lots et en bloc de la notation à l’aide des entrées sous forme de tableau
- Notation dans R et déploiement de modèles en production sur SQL Server dans les procédures stockées en cours d’exécution
- Modification du code R pour réduire le transfert de données ou de supprimer des transformations de données coûteux
- Permettre les tests automatisés et le recyclage de modèles

Étant donné que le choix des techniques d’optimisation dépend de la tâche qui est essentielle pour votre application ou d’un cas d’usage, les études de cas couvre les conseils de performances générales et obtenir des conseils sur l’optimisation pour un scénario spécifique, l’optimisation de la notation par lot.

+ **Options d’optimisation individuels dans SQL Server**

    Dans la première étude de cas de performances, plusieurs tests ont été exécutées sur un jeu de données unique à l’aide d’un seul type de modèle. L’algorithme de rxLinMod dans RevoscaleR a été utilisé pour générer un modèle et créer des scores à partir de celui-ci, mais le code, ainsi que les tables de données sous-jacentes ont été systématiquement modifiées pour tester l’impact de chaque modification.

    Par exemple, dans une série de tests, le code R a été modifié afin qu’une comparaison a pu être établie entre l’ingénierie des fonctionnalités à l’aide d’une fonction de transformation et préalable informatique les fonctionnalités et fonctions puis de chargement à partir d’une table. Dans une autre série de tests, les performances de formation de modèle a été comparée entre l’utilisation d’une table indexée standard et les données dans une table avec différents types de compression ou de nouveaux types d’index.

+ **Optimisation pour un scénario de calcul de score de haut volume spécifique**

    Les tâches d’apprentissage automatique dans l’étude de cas de deuxième implique le traitement reprend nombreux soumise à plusieurs postes et recherche le meilleur candidat pour chaque poste de travail. Le modèle d’apprentissage lui-même est formulé comme un problème de classification binaire : il prend une description de reprise et de travail en tant qu’entrée et génère la probabilité pour chaque paire resume-job. Étant donné que l’objectif est de trouver la meilleure correspondance, un seuil de probabilité défini par l’utilisateur est utilisé pour filtrer et obtenir uniquement les correspondances de bonne.

    Pour cette solution, l’objectif principal était pour atteindre une faible latence lors de la notation. Toutefois, cette tâche est gourmande en ressources même pendant le processus de calcul de score, étant donné que chaque nouveau travail doit être mise en correspondance par rapport à des millions de curriculum vitae dans un laps de temps raisonnable. En outre, l’étape d’ingénierie des fonctionnalités produit des fonctionnalités de 2000 par reprise ou de travail et est un goulot d’étranglement de performances de manière significative.

Nous vous suggérons de consulter tous les résultats de la première étude de cas pour déterminer les techniques sont applicables à votre solution et d’évaluer leur impact potentiel.

Ensuite, passez en revue les résultats de l’étude de cas d’optimisation notation pour savoir comment l’auteur appliquer différentes techniques et optimisé le serveur pour prendre en charge une charge de travail particulier.

## <a name="performance-optimization-process"></a>Processus d’optimisation des performances

Configuration et optimisation des performances nécessite la création d’une base solide, sur lequel les optimisations de couche conçues pour les charges de travail spécifiques :

- Choisir un serveur approprié pour l’analytique de l’hôte. En règle générale, un rapport secondaire, entrepôt de données ou un autre serveur est déjà utilisé pour d’autres rapports ou l’analytique est préféré. Toutefois, dans une solution de traitement transactionnel analytique (HTAP) hybride, données opérationnelles peuvent être utilisées comme entrée à R pour calculer les scores rapide.

- Configurer l’instance de SQL Server pour équilibrer les opérations de moteur de base de données et de R ou d’exécution aux niveaux appropriés de script Python. Cela peut inclure la modification des valeurs par défaut de SQL Server pour la mémoire et l’utilisation du processeur, NUMA et paramètres d’affinité de processeur et la création de groupes de ressources.

- Optimiser l’ordinateur du serveur pour prendre en charge une utilisation efficace de scripts externes. Cela peut inclure l’augmentation du nombre de comptes utilisés pour l’exécution du script externe, l’activation de gestion des packages, et affectation d’utilisateurs à associées des rôles de sécurité.

- Application des optimisations spécifiques au stockage de données et de transfert dans SQL Server, y compris l’indexation de stratégies de statistiques, création de requête et l’optimisation des requêtes et la conception de tables qui sont utilisés pour l’apprentissage. Vous pouvez également analyser les sources de données et données modes de transport, ou modifier les processus ETL pour optimiser l’extraction des caractéristiques.

- Paramétrer le modèle analytique pour éviter le manque d’efficacité. La portée des optimisations qui sont possibles dépendent de la complexité de votre code R et les packages et les données que vous utilisez. Tâches clés incluent les éliminer des transformations de données coûteux ou de déchargement de préparation ou fonctionnalité ingénieries tâches de données à partir de R ou Python pour les processus ETL ou SQL. Vous pourrez également refactoriser les scripts, éliminer les installations de package d’en ligne, diviser le code R dans des procédures distinctes pour la formation, notation et d’évaluation ou simplifier le code pour travailler plus efficacement en tant qu’une procédure stockée.

## <a name="articles-in-this-series"></a>Articles de cette série

+ [Optimisation des performances pour R dans SQL Server - matériel](../r/sql-server-configuration-r-services.md)

    Fournit des instructions pour configurer le matériel qui [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est installé et pour la configuration de l’instance de SQL Server pour mieux prendre en charge de scripts externes. Il est particulièrement utile pour **les administrateurs de base de données**.

+ [Optimisation des performances pour R dans SQL Server - code et les données de l’optimisation](../r/r-and-data-optimization-r-services.md)

    Fournit des conseils spécifiques sur la façon d’optimiser le script externe pour éviter les problèmes connus. Il est plus utile de **scientifiques des données**.

    > [!NOTE]
    > Alors que la plupart des informations dans cette section s’applique à R en général, certaines informations sont spécifiques aux fonctions analytiques RevoScaleR. Guide des performances détaillé ne sont pas disponible pour **revoscalepy** et autres prises en charge les bibliothèques Python.
    >

+ [Optimisation des performances pour R dans SQL Server - méthodes et les résultats](../r/performance-case-study-r-services.md)

    Résume les données qui a été utilisé les deux études de cas, comment les performances ont été testées et comment les optimisations affecté les résultats.
