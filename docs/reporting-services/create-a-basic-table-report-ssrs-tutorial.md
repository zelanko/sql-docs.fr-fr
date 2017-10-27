---
title: "Créer un rapport de tableau de base (didacticiel SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
caps.latest.revision: 67
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 3fce85745c90ee7cae060c26a24042eccbd0ee10
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---

# <a name="create-a-basic-table-report-ssrs-tutorial"></a>Créer un rapport de tableau de base (didacticiel SSRS)

Dans ce didacticiel, vous utilisez le Concepteur de rapports dans SQL Server Data Tools pour créer un base [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] paginé de rapport avec une table, selon le  **[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]**  base de données. Vous pouvez également créer [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] des rapports du Générateur de rapports paginés. 

Tout au long de ce didacticiel, vous serez créer un projet de rapport, définir les informations de connexion, définir une requête, ajouter une région de données de Table, regrouper et nombre total de certains champs et afficher un aperçu du rapport.  
  
## <a name="requirements"></a>Spécifications  
Les éléments suivants doivent cependant être installés sur votre système :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]Moteur de base de données SQL Server.  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] en mode natif.  
  
-   La base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] .  Pour plus d’informations, consultez [Adventure Works 2014 Sample Databases](https://msftdbprodsamples.codeplex.com/releases/view/125550)(Exemples de bases de données Adventure Works 2014).  
  
 -   [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) avec les composants « SQL Server Reporting Services » installés afin que vous ayez le Concepteur de rapports.    
  
Vous devez également disposer d’autorisations en lecture seule pour pouvoir récupérer les données de la base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] .

**Durée estimée pour effectuer ce didacticiel :** 30 minutes.
  
## <a name="tasks"></a>Tâches  
[Leçon 1 : Création d’un projet Report Server &#40;Reporting Services&#41;](../reporting-services/lesson-1-creating-a-report-server-project-reporting-services.md)  
  
[Leçon 2 : Spécification des informations de connexion &#40;Reporting Services&#41;](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md)  
  
[Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
[Leçon 4 : Ajout d’une table au rapport &#40;Reporting Services&#41;](../reporting-services/lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
[Leçon 5 : Mise en forme d’un rapport &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md)  
  
[Leçon 6 : Ajout d’un regroupement et de totaux &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)  

## <a name="next-steps"></a>Étapes suivantes

[Didacticiels sur Reporting Services](../reporting-services/reporting-services-tutorials-ssrs.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

