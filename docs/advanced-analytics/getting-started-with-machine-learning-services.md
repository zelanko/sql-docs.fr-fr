---
title: "Prise en main d’apprentissage dans SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 09d6e887a8c64c98a1c3f68c78b07c26da6ffb76
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-machine-learning-in-sql-server"></a>Prise en main d’apprentissage dans SQL Server

Microsoft fournit un ensemble intégré et évolutif des solutions d’apprentissage pour à la fois localement et le cloud :

+ **Intégré**, car vous pouvez exécuter R ou Python dans SQL Server. Cela vous permet de facilement processus d’entreprise de fusion pour ETL et de création de rapports avec les données des tâches de science telles que la fonctionnalité d’ingénierie, de la création du modèle et le score.
+ **Évolutive**, car le chercheur de données permettre développer et tester une solution sur un ordinateur portable et puis le déployer sur plusieurs plateformes pour distribuées ou le traitement parallèle des opérations de clé comme modèle d’apprentissage et de calcul de score. Plateformes prises en charge incluent SQL Server sur Windows, Hadoop et Spark.

Cet article fournit des liens vers des ressources pour chaque produit dans la plateforme Microsoft Machine Learning.

## <a name="machine-learning-in-sql-server"></a>Apprentissage automatique dans SQL Server

+ SQL Server 2017

  À partir de SQL Server 2017 CTP 2.0, prise en charge pour Python a été ajouté et modifié le nom de Machine Learning Services (de-de base de données) afin de refléter la prise en charge pour une plus large gamme de solutions d’apprentissage machine. Maintenant vous pouvez automatiser les tâches d’apprentissage automatique à l’aide des outils SQL pour exécuter le code R ou Python. Sinon, utilisez l’ordinateur SQL Server en tant que le _contexte de calcul_ pour les travaux lancés à partir d’un environnement de développement à distance.

    + [Présentation de l’architecture pour Python dans SQL Server](python/architecture-overview-sql-server-python.md)
    + [Configurer SQL Server R Services ou des Services de Machine Learning](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

+ SQL Server 2016

  SQL Server 2016 prend en charge l’exécution du code R dans SQL Server à l’aide de procédures stockées. Cela facilite l’automatisation des tâches d’apprentissage automatique à l’aide des outils SQL. Ou bien, vous pouvez exécuter le code R à partir d’un ordinateur portable à distance ou d’un environnement de développement R, lors de l’utilisation de l’ordinateur SQL Server en tant que le _contexte de calcul_.

  Cette intégration offre une sécurité pour vos données et vous permet de gérer et d’équilibrer les ressources utilisées par R.

    + [Prise en main en utilisant SQL Server R Services](r/getting-started-with-sql-server-r-services.md)
    + [Configurer SQL Server R Services ou des Services de Machine Learning](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

## <a name="microsoft-machine-learning-server-microsoft-r-server"></a>Microsoft Machine Learning Microsoft R (serveur)

L’option d’installation de Microsoft Machine Learning Server est fournie dans 2017 du serveur SQL pour prendre en charge les clients d’entreprise qui souhaitent exécuter distribuée et évolutive d’apprentissage travaux, mais qui n’ont besoin de l’intégration avec le moteur de base de données SQL Server, telles que l’utilisation de contextes de calcul SQL.

Dans SQL Server 2016, utilisez l’option pour installer Microsoft R Server.
  
  + [Présentation de Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver)
  
Vous pouvez également installer R Server via les programmes d’installation de la plateforme spécifique disponibles à partir de MSDN :

  + [R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
  + [R Server pour Linux](https://msdn.microsoft.com/microsoft-r/rserver-install-linux-server)
  + [R Server pour Hadoop](https://msdn.microsoft.com/microsoft-r/rserver-install-hadoop)

> [!IMPORTANT]
> Si vous souhaitez exécuter Python à l’aide de R Server, veillez à installer la version la plus récente, **Machine Learning Server**, qui est disponible uniquement via le programme d’installation de SQL Server 2017 :
> 
>    + [Configurer Microsoft R Server ou un serveur de Machine Learning](../advanced-analytics/r/create-a-standalone-r-server.md)

## <a name="related-products"></a>Produits connexes

+ [Configurer un Client de science des données](../advanced-analytics/r/set-up-a-data-science-client.md)

  Si vous avez déjà installé un des produits serveur d’apprentissage, cet article fournit des informations sur la façon de configurer un ordinateur distinct pour le développement et le test de solutions, notamment des outils et bibliothèques requises.

+ [Machine virtuelle pour la science des données](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

  Lancer votre entrée en apprentissage automatique en obtenant cette solution à partir d’Azure Marketplace d’apprentissage complete. La machine virtuelle de science des données (souvent abrégée « DSVM ») inclut SQL Server, Microsoft Machine Learning Server et tous les outils de développement.
  
  La version la plus récente de la Machine virtuelle de science des données (DSVM) s’exécute sur la version d’évaluation Windows 2016, pour fournir l’aspect personnalisable de nettoyage de Windows 10. Elle est préconfigurée avec les pilotes, CUDA Toolkit 8.0 et la bibliothèque de cuDNN NVIDIA pour les charges de travail GPU NVIDIA.

## <a name="resources-for-learning"></a>Ressources d’apprentissage

+ [Didacticiels d’apprentissage machine](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

  Démarrez ici pour rechercher une liste de toutes les ressources pour en savoir plus sur les solutions d’apprentissage machine à l’aide de SQL Server 2017 et SQL Server 2017.

### <a name="r-tutorials"></a>Didacticiels de R

+ [Didacticiels de SQL Server R](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

   Découvrez comment exécuter R dans SQL Server, créer et utiliser les contextes de calcul à distance ou effectuer des simulations dans R à l’aide de SQL Server.
   
   Inclut des didacticiels de « tout le code fourni » afin que vous pouvez exécuter une solution R à partir de SQL Server Management Studio, sans jamais ouvrir un IDE R !

+ [Explorer R et ScaleR 25 fonctions courtes](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

   Vous débutez avec R ? Vous vous demandez la manière dont Microsoft R (ou RevoScaleR) compare à R standard ? Pour R Server, consultez ces rapide-démarre.

### <a name="python-tutorials"></a>Didacticiels de Python

+ [Didacticiels de SQL Server Python](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

  Découvrez comment exécuter Python dans SQL Server. Générer un modèle à l’aide de Python et l’utiliser pour évaluer des données de SQL Server.

   Une solution de bout en bout pour les développeurs SQL fournit tout le code que vous devez exécuter Python à partir de SQL Server Management Studio.

+ [Publier et utiliser du Code Python](../advanced-analytics/python/publish-consume-python-code.md)

  Cette procédure pas à pas est fourni avec tout le code nécessaire pour déployer un modèle à un service web à l’aide de la Machine Learning Server.

### <a name="product-samples-with-code"></a>Exemples de produit avec le code

Ces solutions à partir de l’équipe de développement de SQL Server exécutent dans Python ou R et illustrent des scénarios courants pour l’intégration d’apprentissage automatique avec les applications métiers.

+ [Créer une application intelligente avec SQL Server et R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

+ [Créer une application intelligente avec SQL Server et Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

### <a name="data-science-solution-templates"></a>Modèles de solution de science des données

Les modèles de solution à partir de l’équipe Microsoft pour la science des données représentent des solutions exemple complet adaptées aux scénarios ou des secteurs spécifiques. Elles sont destinées à servir comme blocs de construction pour vous aider à implémenter une solution rapide, ou pour illustrer les meilleures pratiques. Chaque modèle inclut des exemples de données et de code personnalisables.

+ [Modèles de solution](../advanced-analytics/tutorials/data-science-scenarios-and-solution-templates.md)

## <a name="next-steps"></a>Étapes suivantes

[Prise en main Machine Learning Services SQL Server](../advanced-analytics/r/getting-started-with-sql-server-r-services.md)

[Prise en main Server d’apprentissage Microsoft](../advanced-analytics/r/getting-started-with-microsoft-r-server-standalone.md)

