---
title: Didacticiel sur RevoScaleR fonctionne avec SQL Server Machine Learning | Microsoft Docs
description: Dans ce didacticiel, découvrez comment appeler la fonction RevoScaleR dans SQL Server Machine Learning avec R pris en charge est activée.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ee810c998f8aecf17c3496540c65471e0b29e102
ms.sourcegitcommit: a083e9d59e2014a06cda9138b7e17c17ecab90e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44343084"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Didacticiel : Les fonctions utilisent RevoScaleR R avec des données SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR est un package de Microsoft R permettant de traiter des parallèle et distribuée pour la science des données et des charges de travail d’apprentissage. Pour le développement R dans SQL Server, RevoScaleR est un des principaux intégrés packages, avec des fonctions permettant de définir un contexte de calcul, la gestion des packages et plus important encore : utilisation des données-bout, à partir de l’importation de visualisation et d’analyse. Algorithmes d’apprentissage automatique dans SQL Server ont une dépendance sur les sources de données de RevoScaleR. Étant donné l’importance de RevoScaleR, savoir quand et comment appeler ses fonctions est une compétence essentielle. 

Dans ce didacticiel, vous allez apprendre à créer un contexte de calcul à distance, de déplacer des données entre les contextes de calcul locaux et distants et d’exécuter du code R sur un serveur SQL distant. Vous découvrez également comment analyser et tracer des données à la fois localement et sur le serveur distant et comment créer et déployer des modèles.

+ Les données obtenues initialement proviennent de fichiers CSV ou XDF. Vous importez les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant les fonctions dans le package RevoScaleR.
+ Modèle d’apprentissage et de notation sont effectuée à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contexte de calcul. 
+ Utiliser les fonctions RevoScaleR pour créer de nouveaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables pour enregistrer vos résultats de la notation.
+ Créer des graphiques à la fois sur le serveur et le contexte de calcul local.
+ Former un modèle de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données, en cours d’exécution R le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.
+ Extraire un sous-ensemble de données et les enregistrer dans un fichier XDF pour une réutilisation dans l’analyse sur votre station de travail locale.
+ Obtenir de nouvelles données pour calculer les scores, en ouvrant une connexion ODBC à le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. Calcul de score est effectué sur la station de travail locale.
+ Créer une fonction R personnalisée et l’exécuter dans le serveur de contexte de calcul pour effectuer une simulation.

## <a name="target-audience"></a>Public cible

Ce didacticiel est prévu pour scientifiques des données ou pour les personnes qui sont déjà familiarisées avec R et tâches de science des données telles que des résumés et la création de modèles. Toutefois, tout le code est fourni, même si vous débutez avec R, vous pouvez donc exécuter le code et suivre la procédure, en supposant que vous avez des environnements client et serveur nécessaires.

Vous devez également être familiarisé avec [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe et savoir comment accéder à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données à l’aide des outils tels que ceux-ci :

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Outils de base de données dans Visual Studio 
+ La version gratuite [extension mssql pour Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).
  
> [!TIP]
> Enregistrez votre espace de travail R entre les leçons pour pouvoir facilement reprendre là où vous en étiez.

## <a name="prerequisites"></a>Prérequis

- **SQL Server avec la prise en charge de R**
  
    Installer [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité R, ou installez [SQL Server 2016 R Services (en base de données)](../install/sql-r-services-windows-install.md).

    Assurez-vous que l’écriture de scripts externes est activé, le service Launchpad est en cours d’exécution, et que vous disposez des autorisations pour accéder au service.
  
-  **Autorisations de base de données**
  
    Pour exécuter les requêtes utilisées pour former le modèle, vous devez disposer des privilèges de **db_datareader** sur la base de données où sont stockées les données. Pour exécuter R, l’utilisateur doit disposer de l’autorisation EXECUTE ANY EXTERNAL SCRIPT.

-   **Ordinateur de développement de science des données**
  
    Pour basculer entre les contextes de calcul locaux et distants, vous avez besoin des deux systèmes. Locale est généralement une station de travail de développement grâce à une puissance suffisante pour les charges de travail de science des données. À distance dans ce cas est SQL Server 2017 ou SQL Server 2016 avec la fonctionnalité R activée. 
    
    Basculement des contextes de calcul dépend ayant la même version RevoScaleR sur les systèmes locaux et distants. Sur une station de travail locale, vous pouvez obtenir les packages RevoScaleR et les fournisseurs associés par l’installation ou à l’aide de l’une des opérations suivantes : [machine virtuelle de science des données sur Azure](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview), [(gratuit) de Microsoft R Client](https://docs.microsoft.com/en-us/machine-learning-server/r-client/what-is-microsoft-r-client), ou [ Microsoft Machine Learning Server (autonome)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-install). Pour l’option de serveur autonome, installez l’édition gratuite pour les développeurs, à l’aide de programmes d’installation de Linux ou Windows. Vous pouvez également utiliser le programme d’installation de SQL Server pour installer un serveur autonome.
      
-   **Packages R supplémentaires**
  
    Dans ce didacticiel, vous installez les packages suivants : **dplyr**, **ggplot2**, **ggthemes**, **reshape2**, et **e1071** . Des instructions sont fournies dans le didacticiel.
  
    Tous les packages doivent être installés dans deux emplacements : sur la station de travail utilisé pour le développement de solutions R et sur l’ordinateur SQL Server où les scripts R sont exécutées. Si vous n’êtes pas autorisé à installer des packages sur l’ordinateur du serveur, demandez à un administrateur. 
    
    **N’installez pas les packages dans une bibliothèque d’utilisateur.** Les packages doivent être installés dans la bibliothèque de packages R qui est utilisée par l’instance de SQL Server.

## <a name="r-development-tools"></a>Outils de développement R

Les développeurs de R utilisent généralement les IDE pour l’écriture et débogage du code R. Voici quelques suggestions :

- **Outils R pour Visual Studio** (RTVS) est un plug-in qui fournit Intellisense, le débogage et le support pour Microsoft R. Vous pouvez l’utiliser avec R Server et SQL Server Machine Learning Services. Pour télécharger, consultez [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **RStudio** est un des environnements les plus populaires pour le développement R. Pour plus d’informations, consultez [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

- Outils de base R (R.exe, RTerm.exe, RScripts.exe) sont également installés par défaut lorsque vous installez R dans SQL Server ou de R Client. Si vous ne souhaitez pas installer un IDE, vous pouvez utiliser les outils intégrés de R pour exécuter le code dans ce didacticiel.

Rappelez-vous que RevoScaleR est requis sur les ordinateurs locaux et distants. Vous ne pouvez pas suivre ce didacticiel à l’aide d’une installation générique de RStudio ou un autre environnement qui n’a pas les bibliothèques Microsoft R. Pour plus d’informations, consultez [Configurer un client de science des données](../r/set-up-a-data-science-client.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Leçon 1 : Créer la base de données et les autorisations](deepdive-work-with-sql-server-data-using-r.md)

