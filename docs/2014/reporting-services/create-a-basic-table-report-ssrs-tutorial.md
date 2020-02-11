---
title: Créer un rapport de tableau de base (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08ed0c207b92075952ffc71669b45100e4ff7d06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109680"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>Créer un rapport de tableau de base (didacticiel SSRS)
  Ce didacticiel est conçu pour vous aider à créer un rapport de table de base à l’aide du Concepteur de rapports, à partir de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]. Pour créer des rapports, vous pouvez également utiliser le Générateur de rapports et l'Assistant Rapport. Dans ce didacticiel, vous allez créer un projet de rapport, configurer des informations de connexion, définir une requête, ajouter une région de données de table, regrouper certains champs et calculer leurs totaux et afficher un aperçu du rapport.  
  
> [!NOTE]  
>  Pour suivre ce didacticiel, vous devez exécuter [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif. Si vous exécutez [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode intégré SharePoint, les étapes faisant appel aux URL de serveur de rapports ne fonctionnent pas. Pour plus d’informations [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur les modes, consultez [Reporting Services serveur de rapports](reporting-services-report-server.md).  
  
## <a name="requirements"></a>Spécifications  
 Les éléments suivants doivent cependant être installés sur votre système :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] moteur de base de données.  
  
-   La base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  Pour plus d’informations, consultez [Adventure Works pour SQL Server 2012 (Adventure Works pour SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471).. Pour plus d’informations sur la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prise en charge des exemples de bases [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]de données et d’exemples de code pour, consultez [vue d’ensemble des bases de données et exemples](https://go.microsoft.com/fwlink/?LinkId=110391) sur le site Web CodePlex.  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 Vous devez également disposer d’autorisations en lecture seule pour pouvoir récupérer les données de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
## <a name="tasks"></a>Tâches  
 [Leçon 1 : Création d’un projet Report Server &#40;Reporting Services&#41;](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [Leçon 2 : Spécification des informations de connexion &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [Leçon 4 : Ajout d’une table au rapport &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [Leçon 5 : Mise en forme d’un rapport &#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)  
  
 [Leçon 6 : Ajout d’un regroupement et de totaux &#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  Lorsque vous examinez des didacticiels, nous vous recommandons d’ajouter les boutons **suivant** et **précédent** dans la barre d’outils de la visionneuse de documents. Pour plus d’informations, consultez.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](reporting-services-tutorials-ssrs.md)  
  
  
