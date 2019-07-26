---
title: Didacticiel approfondi sur la fonction RevoScaleR-SQL Server Machine Learning
description: Dans ce didacticiel, vous allez apprendre à appeler les fonctions RevoScaleR à l’aide de SQL Server Machine Learning l’intégration de R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: c326d51e9b3ac4edac61f97bf5f7fa3143d8d350
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470629"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Tutoriel : Utiliser des fonctions R RevoScaleR avec des données SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est un package Microsoft R fournissant un traitement distribué et parallèle pour la science des données et les charges de travail de machine learning. Pour le développement R dans SQL Server, **RevoScaleR** est l’un des packages intégrés de base, avec des fonctions pour la création d’objets de source de données, la définition d’un contexte de calcul, la gestion des packages et plus important: l’utilisation de données de bout en bout, de l’importation à visualisation et analyse. Les algorithmes de Machine Learning dans SQL Server ont une dépendance sur les sources de données **RevoScaleR** . Étant donné l’importance de **RevoScaleR**, savoir quand et comment appeler ses fonctions est une compétence essentielle. 

Dans ce didacticiel en plusieurs parties, vous avez introduit une série de fonctions **RevoScaleR** pour les tâches associées à la science des données. Dans le processus, vous allez apprendre à créer un contexte de calcul distant, à déplacer des données entre des contextes de calcul locaux et distants et à exécuter du code R sur une SQL Server distante. Vous allez également apprendre à analyser et à tracer des données à la fois localement et sur le serveur distant, et comment créer et déployer des modèles.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 machine learning services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité r ou [SQL Server 2016 r services (en base de données)](../install/sql-r-services-windows-install.md)
  
+ [Autorisations de base de](../security/user-permission.md) données et connexion utilisateur de base de données SQL Server

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ Un IDE tel que RStudio ou l’outil RGUI intégré fourni avec R

Pour basculer entre les contextes de calcul locaux et distants, vous avez besoin de deux systèmes. Local est généralement une station de travail de développement avec une puissance suffisante pour les charges de travail de science des données. Dans ce cas, la fonction distante est SQL Server 2017 ou SQL Server 2016 avec la fonctionnalité R activée. 

Le basculement des contextes de calcul dépend de la **RevoScaleR** de la version identique sur les systèmes locaux et distants. Sur une station de travail locale, vous pouvez obtenir les packages **RevoScaleR** et les fournisseurs associés en installant Microsoft R client.

Si vous devez placer le client et le serveur sur le même ordinateur, veillez à installer un deuxième ensemble de bibliothèques Microsoft R pour envoyer un script R à partir d’un client «distant». N’utilisez pas les bibliothèques R qui sont installées dans les fichiers programme de l’instance SQL Server. Plus précisément, si vous utilisez un ordinateur, vous avez besoin de la bibliothèque **RevoScaleR** dans ces deux emplacements pour prendre en charge les opérations du client et du serveur.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

Pour obtenir des instructions sur la configuration du client, consultez [configurer un client de science des données pour le développement R](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>Outils de développement R

Les développeurs r utilisent généralement des IDE pour écrire et déboguer du code R. Voici quelques suggestions :

- **Outils R pour Visual Studio** (RTVS) est un plug-in gratuit qui fournit IntelliSense, le débogage et la prise en charge de Microsoft R. Vous pouvez l’utiliser avec R Server et SQL Server Machine Learning Services. Pour télécharger, consultez [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **RStudio** est un des environnements les plus populaires pour le développement R. Pour plus d’informations, [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)consultez.

- Les outils R de base (R. exe, RTerm. exe, RScripts. exe) sont également installés par défaut lorsque vous installez R dans SQL Server ou R client. Si vous ne souhaitez pas installer un IDE, vous pouvez utiliser les outils R intégrés pour exécuter le code de ce didacticiel.

Rappelez-vous que **RevoScaleR** est requis sur les ordinateurs locaux et distants. Vous ne pouvez pas effectuer ce didacticiel à l’aide d’une installation générique de RStudio ou d’un autre environnement qui ne contient pas les bibliothèques Microsoft R. Pour plus d’informations, consultez [Configurer un client de science des données](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Résumé des tâches

+ Les données obtenues initialement proviennent de fichiers CSV ou XDF. Vous importez les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données dans à l’aide des fonctions du package **RevoScaleR** .
+ L’apprentissage et l’évaluation du modèle sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectués à l’aide du contexte de calcul. 
+ Utilisez les fonctions **RevoScaleR** pour créer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des tables afin d’enregistrer les résultats de votre évaluation.
+ Créer des tracés sur le serveur et dans le contexte de calcul local.
+ Effectuer l’apprentissage d’un modèle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur les données de la base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données, en exécutant R dans l’instance.
+ Extrayez un sous-ensemble de données et enregistrez-le en tant que fichier XDF pour une réutilisation dans l’analyse sur votre station de travail locale.
+ Obtenir de nouvelles données pour le calcul des scores, en ouvrant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une connexion ODBC à la base de données. Le calcul du score s’effectue sur la station de travail locale.
+ Créez une fonction R personnalisée et exécutez-la dans le contexte de calcul du serveur pour effectuer une simulation.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Leçon 1 : Créer une base de données et des autorisations](deepdive-work-with-sql-server-data-using-r.md)