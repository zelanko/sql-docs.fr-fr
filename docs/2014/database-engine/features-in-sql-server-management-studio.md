---
title: Fonctionnalités de SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], about SQL Server Management Studio
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: e75504b9-7968-4e3b-8411-fd79fe09021e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 790e02374fe209576c963c5f1e9c6e63e8e2d16b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779787"
---
# <a name="features-in-sql-server-management-studio"></a>Fonctionnalités de SQL Server Management Studio
  
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] comprend les fonctionnalités générales suivantes :  
  
-   la prise en charge de la plupart des tâches d'administration pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)];  
  
-   un environnement unique intégré pour les tâches de gestion et de création dans le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ;  
  
-   des boîtes de dialogue de gestion des objets dans le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]et [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], qui vous permettent d'exécuter vos actions immédiatement, de les envoyer vers un éditeur de code ou de les mettre dans un script afin de les exécuter ultérieurement ;  
  
-   des boîtes de dialogue non modales et redimensionnables qui vous permettent d'avoir accès à plusieurs outils lorsqu'une boîte de dialogue est ouverte ;  
  
-   une boîte de dialogue de planification commune qui vous permet de réaliser des actions des boîtes de dialogue de gestion ultérieurement ;  
  
-   l'exportation et l'importation de l'inscription des serveurs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] d'un environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] dans un autre ;  
  
-   l'enregistrement ou l'impression de fichiers Showplan XML ou de blocage générés par le Générateur de profils afin de les revoir ultérieurement ou de les envoyer aux administrateurs à des fins d'analyse ;  
  
-   une nouvelle boîte de message d'erreur et d'information qui fournit davantage d'informations et qui vous permet d'envoyer à [!INCLUDE[msCoName](../includes/msconame-md.md)] un commentaire à propos des messages, de copier les messages dans le Presse-papiers et d'envoyer facilement les messages par courrier électronique à votre équipe de support technique ;  
  
-   un navigateur Web intégré pour parcourir rapidement MSDN ou l'aide en ligne ;  
  
-   l'intégration de l'Aide des communautés en ligne ;  
  
-   un didacticiel sur [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour vous aider à tirer parti des nombreuses nouvelles fonctionnalités et à devenir immédiatement productif ;  
  
-   un nouveau Moniteur d'activité avec des filtres et une fonction d'actualisation automatique ;  
  
-   des interfaces de messagerie de base de données intégrées.  
  
## <a name="new-scripting-capabilities"></a>Nouvelles fonctionnalités de script  
 Le composant Éditeur de code de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] contient des éditeurs de script intégrés pour la création de scripts [!INCLUDE[tsql](../includes/tsql-md.md)], MDX, DMX, et XML/A. Il permet d'effectuer les tâches suivantes :  
  
-   une aide dynamique pour un accès immédiat aux informations utiles lorsque vous travaillez ;  
  
-   un ensemble de modèles et la possibilité de créer des modèles personnalisés ;  
  
-   la prise en charge de l'écriture et de la modification des requêtes ou des scripts sans connexion à un serveur ;  
  
-   la prise en charge de scripts pour les requêtes et les scripts SQLCMD ;  
  
-   une nouvelle interface pour afficher les résultats XML ;  
  
-   un contrôle de code source pour les projets solutions et de script qui prend en charge le stockage et la gestion de copies de scripts au fur et à mesure de leur évolution ;  
  
-   
  [!INCLUDE[msCoName](../includes/msconame-md.md)] la prise en charge d’IntelliSense pour les instructions MDX.  
  
## <a name="object-explorer-features"></a>Fonctionnalités de l'Explorateur d'objets  
 Le composant Explorateur d'objets de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est un outil intégré d'affichage et de gestion des objets dans tous les types de serveurs. Il permet d'effectuer les tâches suivantes :  
  
-   filtrer par nom, schéma ou date complète ou partielle ;  
  
-   remplir de façon asynchrone des objets avec la possibilité de filtrer les objets selon leurs métadonnées ;  
  
-   avoir accès à l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur les serveurs de réplication à des fins d'administration.  
  
 Pour plus d’informations, consultez [Explorateur d’objets](../ssms/object/object-explorer.md).  
  
## <a name="extensibility"></a>Extensibilité  
 
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] repose sur le shell isolé Visual Studio, qui prend en charge intrinsèquement l’extensibilité (compléments/plug-ins). Il est possible d'exploiter les services d'extensibilité de Visual Studio dans les fonctions personnalisées de l'aire dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]; toutefois, cette extensibilité n'est pas prise en charge.  
  
 Certains utilisateurs et fournisseurs tiers ont développé des extensions de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Même si nous ne décourageons pas cette démarche, n’oubliez pas que cette extensibilité n’est pas prise en charge et qu’elle peut donc engendrer des problèmes de compatibilité descendante/ascendante. Microsoft ne publie pas de documentation pour l’extension de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Il existe toutefois des blogs communautaires et des exemples de code dont vous pourrez tirer parti.  
  
 Microsoft ne prend pas en charge les installations [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] avec les extensions [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] présentes, donc si vous avez installé les extensions [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , vous pouvez les supprimer avant d'appeler le support technique Microsoft à propos d'un problème lié à [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  
