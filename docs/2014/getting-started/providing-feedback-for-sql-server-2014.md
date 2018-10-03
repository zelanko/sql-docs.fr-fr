---
title: Envoi de commentaires sur SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sending feedback to Microsoft
- errors [SQL Server], feedback reporting
- feedback [SQL Server]
- submitting feedback [SQL Server]
- bug reporting [SQL Server]
- reporting usage information to Microsoft
- reporting errors to Microsoft
- SQL Server, feedback reporting
- documentation feedback [SQL Server]
- usage information reporting [SQL Server]
- product feedback [SQL Server]
- automatic error or usage reporting
ms.assetid: 28f3ebf0-ad71-4816-86a6-18a46f023cfe
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32068cf03a971cd6b8010618d7b74d1a613ec856
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109891"
---
# <a name="providing-feedback-for-sql-server-2014"></a>Envoi de commentaires sur SQL Server 2014
  [!INCLUDE[msCoName](../includes/msconame-md.md)] vous remercie de l'aide que vous lui apportez afin d'améliorer ses produits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et leur documentation. Vous pouvez transmettre vos suggestions et rapports de bogues sur les caractéristiques et l'interface utilisateur d'un produit, soumettre des commentaires sur la documentation, ou envoyer automatiquement des rapports d'erreurs et des données sur l'utilisation à [!INCLUDE[msCoName](../includes/msconame-md.md)] en vue de leur analyse. Chacune de ces trois options d'envoi de commentaires est décrite ici.  
  
## <a name="submitting-feedback-about-the-product"></a>Envoi de commentaires sur le produit  
 Utilisez la page de commentaires sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connect pour envoyer vos suggestions et rapports de bogues sur les fonctionnalités de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], notamment les outils, les utilitaires, les langages et les interfaces de programmation.  
  
 Pour accéder à la page de commentaires sur [!INCLUDE[msCoName](../includes/msconame-md.md)] de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Connect, vous pouvez procéder de l'une des manières suivantes.  
  
-   Accédez à la [page web](http://go.microsoft.com/fwlink/?linkid=34178) de commentaires sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connect.  
  
-   Cliquez sur le bouton **Envoyer des commentaires** de la barre d’outils d’aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ou sélectionnez la commande **Communauté/Envoyer des commentaires**.  
  
-   Dans la barre d’outils d’aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez sur le bouton **Envoyer des commentaires**.  
  
-   En haut des rubriques de documentation en ligne [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], cliquez sur le bouton **Envoyer des commentaires**.  
  
 La barre d'outils d'aide n'apparaît pas dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ou [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] tant que :  
  
-   vous n'accédez pas à l'aide à partir de l'utilitaire ;  
  
-   vous ne cochez pas **Aide** sous l’onglet **Barres d’outils** de la commande **Outils/Personnaliser** .  
  
## <a name="automatic-error-and-usage-reporting"></a>Rapports d'erreur et d'utilisation automatiques  
 Vous pouvez décider d'envoyer automatiquement des rapports d'erreur ou des informations sur la façon dont vous utilisez le logiciel et les services de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[msCoName](../includes/msconame-md.md)] se sert de ces informations pour améliorer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutes les données sont traitées de manière confidentielle.  
  
### <a name="managing-automatic-usage-reporting"></a>Gestion des rapports d'utilisation automatiques  
 Les rapports d'utilisation automatiques vous permettent de décider s'il faut recueillir et envoyer des données à [!INCLUDE[msCoName](../includes/msconame-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise deux pipelines pour signaler des données d'utilisation. Ces deux pipelines collectent des données similaires, mais relèvent les informations d'utilisation de programmes différents. Ils peuvent être activés ou désactivés séparément. Si vous activez ou désactivez un pipeline à l'aide d'un des programmes qui l'utilise, vous arrêtez ou démarrez la collecte des données à partir des autres programmes qui partagent ce pipeline.  
  
-   Le premier pipeline sert à collecter les données d'utilisation pour tous les composants de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], à l'exception de la documentation en ligne et de certains éléments d'interface utilisateur, basés sur [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio, des outils de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Après l'installation, vous pouvez également désactiver (ou activer) ce pipeline. Pour ce faire, dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez un projet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis, dans le menu **Aide**, sélectionnez **Options pour les commentaires client**. Cette commande n'apparaît que si vous ouvrez un projet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   L'autre pipeline est utilisé pour la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], pour les éléments d'interface utilisateur basés sur Visual Studio des outils de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et pour Visual Studio. Après l'installation, vous pouvez également désactiver (ou activer) ce pipeline. Pour ce faire, dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez un projet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis, dans le menu **Aide**, sélectionnez **Options pour les commentaires client**. Cette commande n'apparaît que si vous ouvrez un projet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="helping-build-a-better-books-online"></a>Contribution à une documentation en ligne de meilleure qualité  
 En activant les rapports d'utilisation pour la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous aidez l'équipe chargée de la documentation à s'améliorer. Les données agrégées que nous recevons nous aident à mieux comprendre les besoins des lecteurs. Nous comprenons ainsi comment ils parcourent les rubriques, combien de fois ils les consultent et nous arrivons à déterminer celles qu'ils considèrent les plus utiles.  
  
 Vos commentaires nous permettent de comprendre comment vous utilisez la documentation. Cela nous aide à concentrer nos ressources de rédaction sur les rubriques les plus importantes et à concevoir les futurs systèmes de documentation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ces informations d'utilisation de la documentation en ligne nous aident également à identifier les fonctionnalités qui génèrent une utilisation fréquente de l'aide. Elles nous indiquent les domaines nécessitant des améliorations en terme de facilité d'utilisation.  
  
  
