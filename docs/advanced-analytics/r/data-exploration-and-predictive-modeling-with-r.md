---
title: Exploration de données et modélisation prédictive avec R
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7cdd1e6dbb0438c1eb3d7404bc0aed672d088206
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470198"
---
# <a name="data-exploration-and-predictive-modeling-with-r-in-sql-server"></a>Exploration de données et modélisation prédictive avec R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les améliorations apportées au processus de science des données possibles grâce à l’intégration avec SQL Server.

S'applique à : SQL Server 2016 R services, SQL Server 2017 machine supervisée services

## <a name="the-data-science-process"></a>Processus de science des données

Les spécialistes de données adoptent le langage R pour explorer les données et créer des modèles prédictifs. C’est généralement un processus itératif d’essais et d’erreurs qui s’exécute jusqu’à obtenir un bon modèle prédictif. En tant que spécialiste des données, vous pouvez vous connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et extraire les données vers votre poste de travail local à l’aide du package RODBC, explorer vos données et créer un modèle prédictif à l’aide des packages R standard.

Toutefois, cette approche présente de nombreux inconvénients, car HAE a entravé l’adoption plus étendue de R dans l’entreprise. 

+ Le déplacement des données peut être lent, inefficace ou non sécurisé
+ R lui-même présente des limitations de performances et de mise à l’échelle

Ces inconvénients deviennent plus évidents lorsque vous avez besoin de déplacer et d’analyser de grandes quantités de données, ou d’utiliser des jeux de données qui ne tiennent pas dans la mémoire disponible sur votre ordinateur.

Les nouveaux packages évolutifs et les fonctions R incluses [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] dans vous aident à surmonter un grand nombre de ces défis. 

## <a name="whats-different-about-revoscaler"></a>Quelle est la différence avec RevoScaleR?

Le package **RevoScaleR** contient des implémentations de certaines fonctions R plus populaires, qui ont été repensées pour fournir les fonctionnalités de parallélisme et mise à l’échelle. Pour plus d’informations, consultez la page relative [à l’informatique distribuée à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).

Le package RevoScaleR prend également en charge la modification du *contexte d’exécution*. Cela signifie que, pour une solution entière ou simplement une fonction, vous pouvez indiquer que les calculs doivent être effectués à l’aide des ressources de l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et non pas celles de votre poste de travail local. Cela présente plusieurs avantages : vous n’avez pas à déplacer des données inutiles et vous pouvez tirer parti des ressources de calcul supérieures sur l’ordinateur serveur.

## <a name="r-environment-and-packages"></a>Packages et environnement R

L’environnement R pris en charge dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] se compose d’un runtime, du langage open source et d’un moteur graphique pris en charge et étendu par plusieurs packages. Le langage autorise l’utilisation d’extensions qui sont implémentées à l’aide de packages.  

### <a name="using-other-r-packages"></a>Utilisation d’autres packages R

Outre les bibliothèques R propriétaires incluses avec Microsoft Machine Learning, vous pouvez utiliser presque tous les packages R de votre solution, notamment:

+ Packages R génériques de référentiels publics. Vous pouvez obtenir les packages R open source les plus populaires auprès de référentiels publics, tels que le CRAN, lequel héberge plus de 6 000 packages utilisables par les scientifiques des données.
  
  Pour la plateforme Windows, les packages R sont fournis sous forme de fichiers .zip, qui peuvent être téléchargés et installés avec la licence GPL.  
  
  Pour plus d’informations sur l’installation des packages tiers compatibles avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], consultez [Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
  
+ Autres packages et bibliothèques fournis par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].   
  
     Le package **RevoScaleR** comprend des fonctions avancées d’analytique de Big Data, versions améliorées des fonctions qui prennent en charge les tâches courantes de la science des données, les algorithmes d’apprentissage optimisés de Naive Bayes, la régression linéaire, les modèles de série chronologique et les réseaux neuronaux, ainsi que les bibliothèques de mathématiques avancées.  
  
     Le package **RevoPemaR** vous permet de développer vos propres algorithmes de mémoire externe parallèle dans R.  
  
     Pour plus d’informations sur ces packages et leur utilisation, consultez [qu’est-ce que RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) et [prise en main de RevoPemaR](https://docs.microsoft.com/machine-learning-server/r/how-to-developer-pemar). 

+ **MicrosoftML** contient une collection d’algorithmes de machine learning et de transformations de données hautement optimisés de l’équipe de science des données Microsoft. La plupart des algorithmes sont également utilisés dans Azure Machine Learning. Pour plus d’informations, consultez [MicrosoftML dans SQL Server](ref-r-microsoftml.md).

### <a name="r-development-tools"></a>Outils de développement R

Lors du développement de votre solution R, veillez à télécharger Microsoft R Client. Ce téléchargement gratuit comprend les bibliothèques nécessaires pour prendre en charge les contextes de calcul à distance et les alorithms évolutives:

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Distribution du runtime R et d’un ensemble de packages, tels que la bibliothèque de noyaux mathématiques Intel, qui améliorent les performances des opérations R standard.  
  
+ **RevoScaleR** Un package R qui vous permet de transmettre des calculs à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)] . Il inclut également un ensemble de fonctions R courantes qui ont été repensées pour offrir de meilleures performances et une plus grande scalabilité. Le préfixe **rx** identifie ces fonctions améliorées. Il inclut aussi des fournisseurs de données améliorées pour diverses sources. Ces fonctions ont le préfixe **Rx**.

Vous pouvez utiliser n’importe quel éditeur de code basé sur Windows qui prend en [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] charge R, tel que ou RStudio. Le téléchargement de [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] inclut également des outils en ligne de commande courants pour R, comme RGui.exe.

## <a name="use-new-data-sources-and-compute-contexts"></a>Utiliser de nouvelles sources de données et des contextes de calcul

Lorsque vous utilisez le package RevoScaleR pour vous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]connecter à, recherchez ces fonctions à utiliser dans votre code R:

+ **RxSqlServerData** est fournie dans le package RevoScaleR pour la prise en charge de la connectivité de données améliorée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
     Utilisez cette fonction dans votre code R pour définir la *source de données*. L’objet de source de données spécifie le serveur et les tables où les données résident et gère la tâche de lecture et d’écriture de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Le package **RxInSqlServer** permet de spécifier le *contexte de calcul*.  En d’autres termes, vous pouvez indiquer où le code R doit être exécuté : sur votre station de travail locale ou sur l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Pour plus d’informations, consultez [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler).
  
     Quand vous définissez le contexte de calcul, cela s’applique uniquement aux calculs qui prennent en charge le contexte d’exécution à distance, c’est-à-dire les opérations R fournies par le package RevoScaleR et les fonctions associées. En règle générale, les solutions R basées sur les packages CRAN standard ne peuvent pas s’exécuter dans un contexte de calcul à distance, mais elles peuvent être exécutées sur l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] si elles sont démarrées par T-SQL. Vous pouvez toutefois utiliser la fonction `rxExec` pour appeler des fonctions R de façon individuelle et les exécuter à distance dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

Pour obtenir des exemples de création et d’utilisation des sources de données et des contextes d’exécution, consultez les didacticiels suivants:

+ [Immersion dans la science des données](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [Analyse des données à l’aide de Microsoft R](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)

## <a name="deploy-r-code-to-production"></a>Déployer du code R en production

La science des données consiste principalement à échanger des analyses entre spécialistes ou à utiliser des modèles prédictifs pour les résultats ou les processus métier. Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], il est facile de passer en production lorsque votre script ou modèle R est prêt.

Pour plus d’informations sur la migration de votre code vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Operationalizing Your R Code](../../advanced-analytics/r/operationalizing-your-r-code.md).

En général, le processus de déploiement commence par nettoyer votre script afin d’éliminer le code qui n’est pas nécessaire en production. Lorsque vous déplacez les calculs plus près des données, vous pouvez trouver des moyens de déplacer, résumer ou présenter des données plus efficacement que de tout faire dans R.  Nous recommandons que le scientifique des données consulte un développeur de base de données sur les moyens d’améliorer les performances, en particulier si la solution effectue le nettoyage des données ou l’ingénierie des caractéristiques qui peuvent être plus efficaces dans SQL. Les processus ETL peuvent nécessiter des modifications qui vous assurent que les flux de travail de construction ou d’évaluation d’un modèle n’échouent pas et que les données d’entrée sont disponibles dans le format approprié.

## <a name="see-also"></a>Voir aussi

[Comparaison des fonctions R et RevoScaleR de base](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)

[Bibliothèque RevoScaleR dans SQL Server](ref-r-revoscaler.md)
