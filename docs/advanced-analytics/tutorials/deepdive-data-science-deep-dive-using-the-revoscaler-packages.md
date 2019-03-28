---
title: 'Didacticiel de présentation approfondie : SQL Server Machine Learning de fonction RevoScaleR'
description: Dans ce didacticiel, découvrez comment appeler des fonctions RevoScaleR à l’aide de l’intégration SQL Server Machine Learning R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 48d65bfe54890c5ea0d8bfdca9c76fa0978a917d
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511726"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Didacticiel : Utiliser les fonctions RevoScaleR R avec des données de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est un package de Microsoft R fournissant distribué et le traitement en parallèle de science des données et des charges de travail d’apprentissage. Pour le développement R dans SQL Server, **RevoScaleR** est un des principaux packages intégrés, avec des fonctions pour la création d’objets de source de données, définir un contexte de calcul, la gestion des packages et plus important encore : utilisation des données-bout, à partir de l’importation de visualisation et d’analyse. Algorithmes d’apprentissage automatique dans SQL Server ont une dépendance sur **RevoScaleR** des sources de données. Étant donné l’importance de **RevoScaleR**, savoir quand et comment appeler ses fonctions est une compétence essentielle. 

Dans ce didacticiel en plusieurs parties, vous découvrirez une plage de **RevoScaleR** fonctions pour les tâches liées à la science des données. Dans le processus, vous allez apprendre à créer un contexte de calcul à distance, de déplacer des données entre les contextes de calcul locaux et distants et d’exécuter du code R sur un serveur SQL distant. Vous découvrez également comment analyser et tracer des données à la fois localement et sur le serveur distant et comment créer et déployer des modèles.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité R, ou [SQL Server 2016 R Services (en base de données)](../install/sql-r-services-windows-install.md)
  
+ [Autorisations de base de données](../security/user-permission.md) et une connexion d’utilisateur de base de données SQL Server

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ Un IDE tel que RStudio ou l’outil RGUI intégré inclus avec R

Pour basculer entre les contextes de calcul locaux et distants, vous avez besoin des deux systèmes. Locale est généralement une station de travail de développement grâce à une puissance suffisante pour les charges de travail de science des données. À distance dans ce cas est SQL Server 2017 ou SQL Server 2016 avec la fonctionnalité R activée. 

Basculement des contextes de calcul est basée sur la même version **RevoScaleR** sur les systèmes locaux et distants. Sur une station de travail locale, vous pouvez obtenir le **RevoScaleR** fournisseurs connexes en installant Microsoft R Client et packages.

Si vous avez besoin de placer le client et le serveur sur le même ordinateur, veillez à installer un deuxième ensemble de bibliothèques Microsoft R pour l’envoi de script R à partir d’un client « distant ». N’utilisez pas les bibliothèques R qui sont installés dans les fichiers de programme de l’instance de SQL Server. Plus précisément, si vous utilisez un seul ordinateur, vous devez le **RevoScaleR** bibliothèque dans ces deux emplacements pour prendre en charge les opérations de client et serveur.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

Pour obtenir des instructions sur la configuration du client, consultez [configurer un client de science des données pour le développement R](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>Outils de développement R

Les développeurs de R utilisent généralement les IDE pour l’écriture et débogage du code R. Voici quelques suggestions :

- **Outils R pour Visual Studio** (RTVS) est un plug-in qui fournit Intellisense, le débogage et le support pour Microsoft R. Vous pouvez l’utiliser avec R Server et SQL Server Machine Learning Services. Pour télécharger, consultez [Outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **RStudio** est un des environnements les plus populaires pour le développement R. Pour plus d’informations, consultez [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

- Outils de base R (R.exe, RTerm.exe, RScripts.exe) sont également installés par défaut lorsque vous installez R dans SQL Server ou de R Client. Si vous ne souhaitez pas installer un IDE, vous pouvez utiliser les outils intégrés de R pour exécuter le code dans ce didacticiel.

N’oubliez pas que **RevoScaleR** est requis sur les ordinateurs locaux et distants. Vous ne pouvez pas suivre ce didacticiel à l’aide d’une installation générique de RStudio ou un autre environnement qui n’a pas les bibliothèques Microsoft R. Pour plus d’informations, consultez [Configurer un client de science des données](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Résumé des tâches

+ Les données obtenues initialement proviennent de fichiers CSV ou XDF. Vous importez les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant les fonctions dans le **RevoScaleR** package.
+ Modèle d’apprentissage et de notation sont effectuée à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contexte de calcul. 
+ Utilisez **RevoScaleR** fonctions pour créer de nouveaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables pour enregistrer vos résultats de la notation.
+ Créer des graphiques à la fois sur le serveur et le contexte de calcul local.
+ Former un modèle de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données, en cours d’exécution R le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.
+ Extraire un sous-ensemble de données et les enregistrer dans un fichier XDF pour une réutilisation dans l’analyse sur votre station de travail locale.
+ Obtenir de nouvelles données pour calculer les scores, en ouvrant une connexion ODBC à le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. Calcul de score est effectué sur la station de travail locale.
+ Créer une fonction R personnalisée et l’exécuter dans le serveur de contexte de calcul pour effectuer une simulation.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Leçon 1 : Créer une base de données et les autorisations](deepdive-work-with-sql-server-data-using-r.md)