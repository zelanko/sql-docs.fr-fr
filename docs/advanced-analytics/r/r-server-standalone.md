---
title: R Server (autonome) | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
vms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: ca9e48f1-67b8-4905-9b78-56752d7a4e81
caps.latest.revision: "22"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: aa740dc305bf3a34afac42371dbd1ba554b11924
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2017
---
# <a name="r-server-standalone"></a>R Server (autonome)

Dans SQL Server 2016, Microsoft a publié **R Server (autonome)**, dans le cadre de sa plate-forme pour prendre en charge d’analytique de l’entreprise.  Microsoft R Server fournit l’évolutivité et la sécurité pour le langage R et résout les limitations de mémoire de l’open source R. Comme SQL Server R Services, Microsoft R Server (autonome) fournit le traitement parallèle et mémorisé en bloc de données, permettant aux utilisateurs de R d’utiliser beaucoup plus volumineuses que la mémoire peut contenir des données.

Dans SQL Server 2017, prise en charge a été ajoutée pour le langage Python, qui bénéficie d’une prise en charge étendue de la Communauté de machine learning et inclut les bibliothèques pour l’analytique de texte et l’apprentissage approfondie.  Pour refléter cet plus large ensemble de langues, nous avons également renommé en **Microsoft Machine Learning Server (autonome)**.

## <a name="benefits-of-microsoft-r-server"></a>Avantages de Microsoft R Server

Vous pouvez utiliser Microsoft R Server pour l’informatique distribuée sur plusieurs plateformes. Lors de l’installation du programme d’installation de SQL Server, vous obtenez le serveur Windows et tous les outils requis pour les modèles de publication et de déploiement. Pour plus d’informations sur les autres plateformes, consultez ces ressources dans la bibliothèque MSDN :

+ [Présentation de Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver)
+ [R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)

Vous pouvez également installer Microsoft R Server à utiliser comme un client de développement, pour obtenir les bibliothèques de RevoScaleR et les outils nécessaires pour créer des solutions R qui peuvent être déployées vers SQL Server.

## <a name="whats-new-in-microsoft-machine-learning-server"></a>Nouveautés de Microsoft Machine Learning Server

Si vous installez à l’aide du programme d’installation de SQL Server 2017 Machine Learning Services (autonome), vous avez désormais la possibilité d’ajouter le langage Python. Naturellement, le langage R est toujours une option de prise en charge, et vous pouvez même installer les deux langages si vous le souhaitez.
 
Dans SQL Server 2017 CTP 2.0, l’installation du serveur inclut également le package mrsdeploy et autres utilitaires utilisées pour les modèles à mettre en application. Pour plus d’informations, consultez [à l’Opérationnalisation avec mrsdeploy](../../advanced-analytics/operationalization-with-mrsdeploy.md).

Utilisateurs de l’entreprise de l’apprentissage de SQL Server peuvent utiliser les programmes d’installation téléchargeables pour Microsoft R Server pour mettre à niveau leurs composants R, dans un processus appelé liaison. Pour plus d’informations, consultez [SqlBindR d’utilisation pour la mise à niveau et l’Instance de SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

## <a name="get-microsoft-r-server-or-machine-learning-server-standalone"></a>Obtenir Microsoft R Server ou Machine Learning Server (autonome)

 Il existe plusieurs options pour l’installation de Microsoft R Server :

+ Utilisez l’Assistant Installation de SQL Server

  [Créer un serveur R autonome](../r/create-a-standalone-r-server.md)

  Exécutez le programme d’installation de SQL Server 2016 à installer **Microsoft R Server (autonome)**. Le langage R est ajouté par défaut.
  Ou bien, exécutez le programme d’installation de SQL Server 2017 pour installer **Machine Learning Server (autonome)** et sélectionnez R ou Python ou les deux.

  > [!IMPORTANT]
  > L’option pour installer le serveur est dans le **fonctionnalités partagées** section du programme d’installation. N’installez pas d’autres composants.
  >
  > De préférence, n’installez pas le serveur sur un ordinateur où SQL Server R Services ou SQL Server Machine Learning Services a été installés.

+ Utiliser les options de ligne de commande pour le programme d’installation de SQL Server

  [Installer Microsoft R Server à partir de la ligne de commande](../r/install-microsoft-r-server-from-the-command-line.md)

  Le programme d’installation de SQL Server prend en charge les installations sans assistance via un ensemble d’arguments de ligne de commande.

+ Utilisez le programme d’installation autonome

  [Exécutez Microsoft R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).

  Vous pouvez désormais utiliser un nouveau programme d’installation de Windows pour configurer une nouvelle instance de Microsoft R Server ou Microsoft Machine Learning Server.  Microsoft R Server (et serveur de Microsoft Machine Learning) requiert un contrat de SQL Server Enterprise. Toutefois, après avoir exécuté le programme d’installation autonome, la stratégie de prise en charge pour une installation existante est mise à jour, la nouvelle stratégie de cycle de vie moderne. Cette option de prise en charge garantit que les mises à jour des composants de machine learning sont appliqués plus fréquemment qu’ils seraient lorsque vous utilisez les versions de service SQL Server.

  
+ Mise à niveau une instance de SQL Server

  [Pour mettre à niveau une Instance de R Services à l’aide de SqlBindR](./use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).
  
  Vous pouvez utiliser le programme d’installation autonome pour mettre à niveau une instance de SQL Server 2016 R Services à utiliser la dernière version de R. Lorsque vous exécutez le programme d’installation, la stratégie de prise en charge du cycle de vie moderne sera appliquée au serveur, et les composants R obtiendra les mises à jour plus fréquentes.
  
  > [! Remarque} actuellement cette méthode de mise à jour est disponible uniquement pour les installations existantes de SQL Server 2016. Toutefois, les mises à niveau prendra en charge pour SQL Server 2017 dans les futures.

## <a name="related-machine-learning-products"></a>Produits apprentissage connexe

+ Machines virtuelles avec R Server

  [Configurer une Machine virtuelle du serveur R](../../advanced-analytics/r-services/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace inclut plusieurs images de machine virtuelle qui incluent R Server. Création d’un ordinateur virtuel R Server dans Microsoft Azure est le moyen le plus rapide pour configurer un serveur à utiliser pour développer et déployer des modèles prédictifs. Les images sont fournis avec les fonctionnalités de mise à l’échelle et de partage déjà configuré, ce qui le rend plus facile à incorporer analytique R dans des applications et d’intégrer R avec les systèmes back-end.

+ Machine virtuelle de science des données

  [Machine virtuelle de science des données - Windows 2016 Preview](http://aka.ms/dsvm/win2016)

  La dernière version de la machine virtuelle de science des données comprend des R Server, SQL Server, plus un tableau des outils les plus utilisés pour l’apprentissage, tout préinstallé et testé. Créer les blocs-notes Notebook, développer des solutions dans Julia et utiliser des bibliothèques de GPU compatible de formation approfondie, MXNet, CNTK et TensorFlow.

## <a name="resources"></a>Ressources

Pour plus d’exemples, didacticiels et plus d’informations sur Microsoft R Server, consultez [produits de Microsoft R](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started).

## <a name="see-also"></a>Voir aussi

 [SQL Server R Services](../../advanced-analytics/r/sql-server-r-services.md)

