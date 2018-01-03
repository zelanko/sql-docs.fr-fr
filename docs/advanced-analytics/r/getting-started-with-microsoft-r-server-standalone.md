---
title: Prise en main de Microsoft R Server (autonome) | Microsoft Docs
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: "21"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 5ff9e6bc9b6cebb4602683180737aa78e7deb6e3
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2017
---
# <a name="getting-started-with-machine-learning-server-standalone"></a>Prise en main de Machine Learning Server (autonome)
 
Dans SQL Server 2016, Microsoft R Server (autonome) a permis de mettre le langage R open source populaire dans l’entreprise, pour activer des solutions d’analytique de hautes performances et l’intégration avec d’autres applications d’entreprise.  

Dans SQL Server 2017, le nom a été modifié pour la Machine Learning Server (autonome) pour refléter l’ajout de la prise en charge pour le langage Python. Les deux versions sont disponibles gratuitement pour les utilisateurs de l’édition Enterprise ou Software Assurance.

Cet article fournit une vue d’ensemble de comment vous pouvez utiliser Machine Learning serveur (ou R Server) et la prise en main des exemples et d’installation.

## <a name="why-use-a-standalone-server-for-machine-learning"></a>Pourquoi utiliser un serveur autonome pour l’apprentissage

Si vous n’avez pas besoin d’intégrer vos solutions avec des données SQL Server d’apprentissage Machine Learning Server vous donne le même support distribué et évolutif pour R et Python et plus prend en charge le déploiement des solutions à Hadoop, Spark ou Linux.

Machine Learning Server inclut également des modèles d’analyse d’image et d’analyse de sentiments, que vous pouvez utiliser immédiatement dans les applications dont l’apprentissage.

Les fonctionnalités à l’Opérationnalisation du serveur de Machine Learning prend en charge le déploiement et de distribuer des solutions R et Python à l’aide des services web, avec l’exécution à distance, les topologies de cluster pour Spark et Hadoop MapReduce et prend en charge pour Windows ou Linux.

**SQL Server 2016**

+ Installer Microsoft R Server (autonome) du programme d’installation de SQL Server 2016.

    Cette option crée un serveur autonome qui est entièrement indépendant de R Services (de-de base de données). Cette version prend uniquement en charge R. Le programme d’installation d’un serveur autonome est inclus dans votre stratégie de prise en charge de SQL Server Enterprise Edition. Pour plus d’informations, consultez [Créer un serveur R autonome](../../advanced-analytics/r/create-a-standalone-r-server.md).

+ Installer R Server à l’aide du programme d’installation Windows distinct.

    Ce programme d’installation crée une toute nouvelle instance de Microsoft R Server qui utilise la stratégie de prise en charge Microsoft moderne logiciel du cycle de vie. Vous pouvez également installer R Server pour Linux, Cloudera, Teradata et Hadoop.
    
    Pour plus d’informations, consultez [installer R Server 9.1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

**SQL Server 2017**

+ Installez Machine Learning Server (autonome) du programme d’installation de SQL Server 2017. 

    Cette option crée un serveur autonome pour prendre en charge à l’Opérationnalisation d’apprentissage dans R, Python ou les deux. Le programme d’installation d’un serveur autonome est inclus dans votre stratégie de prise en charge de SQL Server Enterprise Edition. Pour plus d’informations, consultez [Créer un serveur R autonome](../../advanced-analytics/r/create-a-standalone-r-server.md).  

+ Utilisez le nouveau programme d’installation de Windows autonome.

    Cette méthode d’installation crée une nouvelle instance de Machine Learning Server qui utilise la stratégie de prise en charge Microsoft moderne logiciel du cycle de vie. Vous pouvez également installer Machine Learning Server sur Linux, Hadoop et/ou Spark sans coût supplémentaire.
    
    Pour plus d’informations, consultez [installer Machine Learning pour Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

**Mise à niveau un serveur existant**

+ Si vous avez un serveur existant ou une instance que vous souhaitez mettre à niveau, téléchargez et exécutez le programme d’installation basé sur Windows pour obtenir les mises à jour. 

    Pour plus d’informations, consultez [à l’aide de SqlBindR pour mettre à niveau une instance](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="start-using-machine-learning-server"></a>Commencer à utiliser le serveur de Machine Learning

 Après avoir configuré les composants serveur et configuré votre IDE pour utiliser les fichiers binaires du serveur de Machine Learning, vous pouvez commencer à développer votre solution en utilisant les nouvelles API, tel que le RevoScaleR revoscalepy, MicrosoftML et olapR.
    
Pour commencer, consultez ces guides :

+ [Modèles de solution](https://docs.microsoft.com/machine-learning-server/r/sample-solutions)

    Les exemples de ces des solutions qui montrent comment appliquer l’apprentissage automatique dans des secteurs spécifiques. Scénarios en cours sont dans la vente au détail, les finances, les soins de santé et marketing.

+ [Explorer R et ScaleR dans les 25 fonctions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): Explorer cette collection de fonctions analytiques distribuables qui fournissent des performances élevées et la mise à l’échelle pour des solutions R. Inclut des versions parallélisables des packages de modélisation R les plus populaires comme le clustering k-means, les arbres de décision, les forêts de décision et les outils de manipulation des données.

- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx)

    Le package MicrosoftML est un ensemble d’apprentissage nouveaux algorithmes et des transformations développées par Microsoft qui sont rapides et évolutives. Vous pouvez l’utiliser dans R ou Python. Pour plus d’informations, consultez [MicrosoftML pour Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) et [MicrosoftML pour R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package).

## <a name="see-also"></a>Voir aussi

[Prise en main de SQL Server d’apprentissage Services](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)