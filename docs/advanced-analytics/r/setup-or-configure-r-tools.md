---
title: "Outils de R inclus dans le programme d’installation de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b45c1a9c58ede0342953caae58c3bd6822501c24
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="r-tools-included-with-sql-server-setup"></a>Outils de R inclus dans le programme d’installation de SQL Server

Lorsque vous installez R avec SQL Server, vous obtenez les mêmes outils R qui sont installés avec les **base** installation de R, tels que RGui, Rterm et ainsi de suite. Par conséquent techniquement, vous devez tous les outils dont vous avez besoin pour développer et tester le code R.

Cette rubrique répertorie les outils inclus avec l’installation.

> [!TIP]
> 
> En général, il est plus facile à déboguer et tester le code R à l’aide d’un environnement de développement dédié. Vous trouverez plus facile d’exécuter votre code R dans SQL Server, si vous le testez au préalable dans un outil externe, afin que vous pouvez lire les messages d’erreur détaillés et déboguer la solution.
> 
> Consultez cet article pour obtenir la liste des outils gratuits que vous pouvez utiliser pour développer des solutions R et comment les configurer pour fonctionner avec SQL Server : [configurer un client de science des données](set-up-a-data-science-client.md)

**S’applique à :** SQL Server 2016 R Services (de-de base de données) et Microsoft R Server (autonome) ; SQL Server 2017 Machine Learning Services (de-de base de données) et d’apprentissage automatique Server (autonome)

## <a name="r-tools-included-with-installation"></a>Outils R inclus avec l’installation

Les outils R standards suivants sont inclus dans un *installation de base* de R et par conséquent, sont installés par défaut.

+ **RTerm**: un terminal de ligne de commande pour l’exécution des scripts R

+ **RGui.exe** : éditeur interactif simple pour R. Les arguments de ligne de commande sont les mêmes pour RGui.exe et RTerm.

+ **RScript** : outil en ligne de commande pour l’exécution de scripts R en mode batch.

Pour rechercher ces outils, déterminez la bibliothèque R qui a été installée lorsque vous installez SQL Server ou la fonctionnalité d’apprentissage autonome. Par exemple, dans une installation par défaut, les outils R sont situés dans ces dossiers :

+ SQL Server 2016 R Services :`~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server autonome :`~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 apprentissage Services :`~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Apprentissage Server (autonome) :`~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Si vous avez besoin d’aide avec les outils R, ouvrez simplement **RGui**, cliquez sur **aide**, puis sélectionnez une des options.

## <a name="introducing-microsoft-r-client"></a>Présentation de Microsoft R Client

Microsoft R Client est un téléchargement gratuit qui vous permet d’accéder aux packages RevoScaleR à des fins de développement. En installant le Client de R, vous pouvez créer des solutions R qui peuvent être exécutées dans tous les contextes de calcul pris en charge, y compris analytique dans base de données de SQL Server et traitements distribués R sur Hadoop, Spark ou Linux à l’aide de la Machine Learning Server.

Si vous avez déjà installé un autre environnement de développement R, tels que RStudio, veillez à reconfigurer l’environnement pour utiliser les bibliothèques et les exécutables fournis par le Client de Microsoft R. En procédant comme vous pouvez donc utiliser toutes les fonctionnalités du package RevoScaleR, bien que les performances seront en trouvent limitées.

Pour plus d’informations, consultez [qu’est Microsoft R Client ?](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)
