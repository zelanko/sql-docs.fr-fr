---
title: Exploration des données et modélisation prédictive avec R - Services de SQL Server Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: de293cd7caf481c51e4195a82ac036526c477739
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642018"
---
# <a name="data-exploration-and-predictive-modeling-with-r-in-sql-server"></a>Exploration des données et modélisation prédictive avec R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les améliorations apportées au processus de science des données qui sont possibles grâce à l’intégration avec SQL Server.

S'applique à : SQL Server 2016 R Services, Services SQL Server 2017 Machine calculateur

## <a name="the-data-science-process"></a>Le processus de science des données

Les spécialistes de données adoptent le langage R pour explorer les données et créer des modèles prédictifs. C’est généralement un processus itératif d’essais et d’erreurs qui s’exécute jusqu’à obtenir un bon modèle prédictif. En tant que spécialiste des données, vous pouvez vous connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et extraire les données vers votre poste de travail local à l’aide du package RODBC, explorer vos données et créer un modèle prédictif à l’aide des packages R standard.

Toutefois, cette approche présente plusieurs inconvénients, qui possèdent entravé la plus large adoption de R dans l’entreprise. 

+ Le déplacement des données peuvent être lent, inefficace ou non sécurisé
+ R lui-même présente des limitations de performances et de mise à l’échelle

Ces inconvénients deviennent plus évidents lorsque vous avez besoin de déplacer et analyser de grandes quantités de données, ou utiliser des jeux de données qui ne tiennent pas dans la mémoire disponible sur votre ordinateur.

Le nouveau, évolutives et les fonctions R incluses avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vous aider à relever ces défis. 

## <a name="whats-different-about-revoscaler"></a>Nouveautés RevoScaleR ?

Le package **RevoScaleR** contient des implémentations de certaines fonctions R plus populaires, qui ont été repensées pour fournir les fonctionnalités de parallélisme et mise à l’échelle. Pour plus d’informations, consultez [Distributed Computing à l’aide de RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).

Le package RevoScaleR prend également en charge la modification du *contexte d’exécution*. Cela signifie que, pour une solution entière ou simplement une fonction, vous pouvez indiquer que les calculs doivent être effectués à l’aide des ressources de l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et non pas celles de votre poste de travail local. Cela présente plusieurs avantages : vous n’avez pas à déplacer des données inutiles et vous pouvez tirer parti des ressources de calcul supérieures sur l’ordinateur serveur.

## <a name="r-environment-and-packages"></a>Packages et environnement R

L’environnement R pris en charge dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] se compose d’un runtime, du langage open source et d’un moteur graphique pris en charge et étendu par plusieurs packages. Le langage autorise l’utilisation d’extensions qui sont implémentées à l’aide de packages.  

### <a name="using-other-r-packages"></a>À l’aide d’autres Packages R

Outre les bibliothèques R propriétaires inclus avec l’apprentissage de Microsoft, vous pouvez utiliser presque tous les packages R dans votre solution, notamment :

+ Packages R génériques de référentiels publics. Vous pouvez obtenir les packages R open source les plus populaires auprès de référentiels publics, tels que le CRAN, lequel héberge plus de 6 000 packages utilisables par les scientifiques des données.
  
  Pour la plateforme Windows, les packages R sont fournis sous forme de fichiers .zip, qui peuvent être téléchargés et installés avec la licence GPL.  
  
  Pour plus d’informations sur l’installation des packages tiers compatibles avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], consultez [Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
  
+ Autres packages et bibliothèques fournis par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].   
  
     Le package **RevoScaleR** comprend des fonctions avancées d’analytique de Big Data, versions améliorées des fonctions qui prennent en charge les tâches courantes de la science des données, les algorithmes d’apprentissage optimisés de Naive Bayes, la régression linéaire, les modèles de série chronologique et les réseaux neuronaux, ainsi que les bibliothèques de mathématiques avancées.  
  
     Le package **RevoPemaR** vous permet de développer vos propres algorithmes de mémoire externe parallèle dans R.  
  
     Pour plus d’informations sur ces packages et leur utilisation, consultez [What ' s RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) et [bien démarrer avec RevoPemaR](https://docs.microsoft.com/machine-learning-server/r/how-to-developer-pemar). 

+ **MicrosoftML** contient une collection d’algorithmes d’apprentissage automatique hautement optimisée et les transformations de données à partir de l’équipe de science des données de Microsoft. La plupart des algorithmes sont également utilisés dans Azure Machine Learning. Pour plus d’informations, consultez [MicrosoftML dans SQL Server](ref-r-microsoftml.md).

### <a name="r-development-tools"></a>Outils de développement R

Lorsque vous développez votre solution R, veillez à télécharger Microsoft R Client. Ce téléchargement gratuit comprend les bibliothèques nécessaires pour prendre en charge les contextes de calcul distants et alorithms évolutive :

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Une distribution du runtime R et un ensemble de packages, tels que Intel math kernel library, qui améliore les performances des opérations R standard.  
  
+ **RevoScaleR:** Un package R qui vous permet de transmettre des calculs à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)] . Il inclut également un ensemble de fonctions R courantes qui ont été repensées pour offrir de meilleures performances et une plus grande scalabilité. Le préfixe **rx** identifie ces fonctions améliorées. Il inclut aussi des fournisseurs de données améliorées pour diverses sources. Ces fonctions ont le préfixe **Rx**.

Vous pouvez utiliser n’importe quel éditeur de code basé sur Windows qui prend en charge R, tel que [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] ou RStudio. Le téléchargement de [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] inclut également des outils en ligne de commande courants pour R, comme RGui.exe.

## <a name="use-new-data-sources-and-compute-contexts"></a>Utilisation de nouvelles Sources de données et les contextes de calcul

Lorsque vous utilisez le package RevoScaleR pour vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], recherchez ces fonctions à utiliser dans votre code R :

+ **RxSqlServerData** est fournie dans le package RevoScaleR pour la prise en charge de la connectivité de données améliorée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
     Utilisez cette fonction dans votre code R pour définir la *source de données*. L’objet de source de données spécifie le serveur et les tables où les données résident et gère la tâche de lecture et d’écriture de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Le package **RxInSqlServer** permet de spécifier le *contexte de calcul*.  En d’autres termes, vous pouvez indiquer où le code R doit être exécuté : sur votre station de travail locale ou sur l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Pour plus d’informations, consultez [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler).
  
     Quand vous définissez le contexte de calcul, cela s’applique uniquement aux calculs qui prennent en charge le contexte d’exécution à distance, c’est-à-dire les opérations R fournies par le package RevoScaleR et les fonctions associées. En règle générale, les solutions R basées sur les packages CRAN standard ne peuvent pas s’exécuter dans un contexte de calcul à distance, mais elles peuvent être exécutées sur l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] si elles sont démarrées par T-SQL. Vous pouvez toutefois utiliser la fonction `rxExec` pour appeler des fonctions R de façon individuelle et les exécuter à distance dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

Pour obtenir des exemples montrant comment créer et utiliser des sources de données et les contextes d’exécution, consultez ces didacticiels :

+ [Immersion dans la science des données](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [Analyse de données à l’aide de Microsoft R](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)

## <a name="deploy-r-code-to-production"></a>Déployer le Code R en Production

La science des données consiste principalement à échanger des analyses entre spécialistes ou à utiliser des modèles prédictifs pour les résultats ou les processus métier. Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], il est facile de passer en production lorsque votre script ou modèle R est prêt.

Pour plus d’informations sur la migration de votre code vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Operationalizing Your R Code](../../advanced-analytics/r/operationalizing-your-r-code.md).

En général, le processus de déploiement commence par nettoyer votre script afin d’éliminer le code qui n’est pas nécessaire en production. Lorsque vous déplacez des calculs plus près aux données, vous pouvez trouver des façons de déplacer plus efficacement, résumer ou présenter les données que tout faire dans R.  Nous recommandons que les spécialistes des données, consultez avec un développeur de base de données sur les moyens d’améliorer les performances, surtout si la solution de nettoyage de données ou d’ingénierie qui peut être plus efficace dans SQL. Les processus ETL peuvent nécessiter des modifications qui vous assurent que les flux de travail de construction ou d’évaluation d’un modèle n’échouent pas et que les données d’entrée sont disponibles dans le format approprié.

## <a name="see-also"></a>Voir aussi

[Comparaison de Base R et les fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)

[Bibliothèque RevoScaleR dans SQL Server](ref-r-revoscaler.md)
