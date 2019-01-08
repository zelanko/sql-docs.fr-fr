---
title: Créer un rapport de tableau de base (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ab5e18825ec9a328db926829355b706cff2a58d8
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53366711"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>Créer un rapport de tableau de base (didacticiel SSRS)
  Ce didacticiel est conçu pour vous aider à créer un rapport de tableau de base selon la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] de base de données à l’aide du Concepteur de rapports. Pour créer des rapports, vous pouvez également utiliser le Générateur de rapports et l'Assistant Rapport. Dans ce didacticiel, vous allez créer un projet de rapport, configurer des informations de connexion, définir une requête, ajouter une région de données de table, regrouper certains champs et calculer leurs totaux et afficher un aperçu du rapport.  
  
> [!NOTE]  
>  Pour suivre ce didacticiel, vous devez exécuter [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif. Si vous exécutez [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode intégré SharePoint, les étapes faisant appel aux URL de serveur de rapports ne fonctionnent pas. Pour plus d’informations sur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modes, consultez [Reporting Services Report Server](reporting-services-report-server.md).  
  
## <a name="requirements"></a>Configuration requise  
 Les éléments suivants doivent cependant être installés sur votre système :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Moteur de base de données.  
  
-   La base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  Pour plus d’informations, consultez [Adventure Works pour SQL Server 2012 (Adventure Works pour SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471).. Pour plus d’informations sur la prise en charge de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bases de données et des exemples de code pour [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], consultez [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) sur le site CodePlex Web.  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 Vous devez également disposer d’autorisations en lecture seule pour pouvoir récupérer les données de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
## <a name="tasks"></a>Tâches  
 [Leçon 1 : Création d’un projet Report Server &#40;Reporting Services&#41;](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [Leçon 2 : Spécification des informations de connexion &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [Leçon 3 : Définition d’un Dataset pour le rapport de Table &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [Leçon 4 : Ajout d’une Table au rapport &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [Leçon 5 : Mise en forme d’un rapport &#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)  
  
 [Leçon 6 : Ajout de regroupements et des totaux &#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  Lorsque vous parcourez les didacticiels, nous vous recommandons d’ajouter **suivant** et **précédent** boutons à la barre d’outils Visionneuse de document. Pour plus d'informations, consultez  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](reporting-services-tutorials-ssrs.md)  
  
  
