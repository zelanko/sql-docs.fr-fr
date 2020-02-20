---
title: Didacticiel approfondi de RevoScaleR
description: Dans cette série de tutoriels, vous allez apprendre à appeler les fonctions RevoScaleR à l’aide de l’intégration R de SQL Server Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fc1f427659155b5379a681787a633b6037b4bd87
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918829"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Tutoriel : Utilisation des fonctions R de RevoScaleR avec les données SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cette série de tutoriels en plusieurs parties, nous vous présentons une plage de fonctions **RevoScaleR** pour les tâches associées à la science des données. Par la même occasion, vous allez apprendre à créer un contexte de calcul distant, à déplacer des données entre des contextes de calcul locaux et distants et à exécuter du code R sur une instance de SQL Server distante. Vous allez également apprendre à analyser et à tracer des données en local et sur le serveur distant, ainsi qu’à créer et déployer des modèles.

[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) est un package R Microsoft qui fournit un traitement distribué et parallèle pour la science des données et les charges de travail de Machine Learning. Pour le développement R dans SQL Server, **RevoScaleR** est l’un des principaux packages intégrés, avec des fonctions permettant de créer des objets source de données, de définir un contexte de calcul, de gérer des packages et, plus important encore, d’utiliser des données du début à la fin, de l’importation à la visualisation et à l’analyse. Les algorithmes de Machine Learning dans SQL Server dépendent des sources de données **RevoScaleR**. Étant donné l’importance de **RevoScaleR**, il est essentiel de savoir quand et comment appeler ses fonctions. 

## <a name="prerequisites"></a>Conditions préalables requises

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) avec la fonctionnalité R ou [SQL Server R Services (dans la base de données)](../install/sql-r-services-windows-install.md)
  
+ [Autorisations de base de données](../security/user-permission.md) et une connexion d’utilisateur de base de données SQL Server

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ Un IDE R comme RStudio ou l’outil RGUI intégré fourni avec R

Pour basculer entre les contextes de calcul locaux et distants, vous avez besoin de deux systèmes. Le contexte local est généralement une station de travail de développement avec une puissance suffisante pour prendre en charge les charges de travail de science des données. Le contexte distant, dans ce cas, est SQL Server avec la fonctionnalité R activée. 

Le changement de contextes de calcul implique l’utilisation de la même version de **RevoScaleR** sur les systèmes locaux et distants. Sur une station de travail locale, vous pouvez obtenir les packages **RevoScaleR** et les fournisseurs associés en installant Microsoft R Client.

Si vous devez placer le client et le serveur sur le même ordinateur, veillez à installer un deuxième ensemble de bibliothèques Microsoft R pour envoyer un script R depuis un client « distant ». N’utilisez pas les bibliothèques R qui sont installées dans les fichiers programme de l’instance SQL Server. Plus précisément, si vous utilisez un ordinateur, vous avez besoin de la bibliothèque **RevoScaleR** dans ces deux emplacements pour prendre en charge les opérations du client et du serveur.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

Pour obtenir des instructions sur la configuration du client, consultez [Configurer un client de science des données pour le développement R](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>Outils de développement R

Les développeurs R utilisent généralement des IDE pour écrire et déboguer le code R. Voici quelques suggestions :

- Les **Outils R pour Visual Studio** (RTVS) sont un plug-in gratuit qui fournit Intellisense, des fonctionnalités de débogage et la prise en charge de Microsoft R. Vous pouvez l’utiliser avec R Server et SQL Server Machine Learning Services. Pour télécharger, consultez [Outils R pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=MikhailArkhipov007.RTVS2019).

- **RStudio** est un des environnements les plus populaires pour le développement R. Pour plus d’informations, consultez [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).

- Les outils R de base (R.exe, RTerm.exe, RScripts.exe) sont aussi installés par défaut quand vous installez R dans SQL Server ou R Client. Si vous ne souhaitez pas installer un IDE, vous pouvez utiliser les outils R intégrés pour exécuter le code de ce didacticiel.

N’oubliez pas que vous aurez besoin de **RevoScaleR** sur les ordinateurs locaux et distants. Vous ne pouvez pas suivre ce didacticiel avec une installation générique de RStudio ou d’un autre environnement qui ne contient pas les bibliothèques Microsoft R. Pour plus d’informations, consultez [Configurer un client de science des données](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Récapitulatif des options

+ Les données obtenues initialement proviennent de fichiers CSV ou XDF. Vous importez des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des fonctions du package **RevoScaleR**.
+ L’apprentissage et le scoring des modèles sont effectués dans le contexte de calcul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
+ Utilisez les fonctions **RevoScaleR** pour créer de nouvelles tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour enregistrer les résultats de vos scorings.
+ Créez des tracés sur le serveur et dans le contexte de calcul en local.
+ Effectuez l’apprentissage d’un modèle à partir des données de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en exécutant R dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
+ Extrayez un sous-ensemble de données et enregistrez-le dans un fichier XDF pour pouvoir le réutiliser dans les analyses sur votre station de travail locale.
+ Obtenez de nouvelles données pour le scoring, en ouvrant une connexion ODBC à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le scoring s’effectue sur la station de travail locale.
+ Créez une fonction R personnalisée et exécutez-la en utilisant le contexte de calcul du serveur pour faire une simulation.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel 1 : Créer une base de données et des autorisations](deepdive-work-with-sql-server-data-using-r.md)