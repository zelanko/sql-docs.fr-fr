---
title: "Dépannage de rapports pour l’exécution du Package | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc476ac-bd69-434e-9636-70776e0b3b6c
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 713868eea3eaee8597a63441b84a5c16ec676215
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="troubleshooting-reports-for-package-execution"></a>Dépannage des rapports pour l'exécution des packages
  Dans la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], deux rapports standard sont disponibles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour vous aider à analyser et à dépanner les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Deux types de rapports de package peuvent notamment vous aider à consulter l'état d'exécution du package et à identifier la cause des erreurs d'exécution.  
  
-   **Tableau de bord Integration Services** - Ce rapport fournit une vue d’ensemble de toutes les exécutions de package sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au cours des dernières 24 heures. Le rapport affiche des informations telles que l'état, le type d'opération, le nom du package, etc., pour chaque package.  
  
     L'heure de début, l'heure de fin et la durée peuvent être interprétées comme suit :  
  
    -   Si le package fonctionne toujours, alors Durée = heure actuelle - heure de début  
  
    -   Si le package est terminé, alors Durée = heure de fin - heure de début  
  
     Pour chaque package qui s'est exécuté sur le serveur, le tableau de bord vous permet de « zoomer » pour rechercher des détails spécifiques sur les erreurs d'exécution du package qui se sont produites. Pour un exemple, cliquez sur **Vue d’ensemble** pour afficher un aperçu détaillé de l’état des tâches dans l’exécution, ou **Tous les messages** pour afficher les messages détaillés capturés dans le cadre de l’exécution du package.  
  
     Vous pouvez filtrer la table affichée dans une page en cliquant sur **Filtrer** et en sélectionnant des critères dans la boîte de dialogue **Paramètres du filtre** . Les critères de filtre disponibles dépendent des données qui sont affichées. Vous pouvez modifier l’ordre de tri du rapport en cliquant sur l’icône de tri dans la boîte de dialogue **Paramètres du filtre** .  
  
-   **Activité - Rapport Toutes les exécutions** - Ce rapport affiche un résumé de toutes les exécutions de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] exécutées sur le serveur. Le résumé affiche les informations relatives à chaque exécution telles que l'état, l'heure de début et l'heure de fin. Chaque entrée de résumé inclut des liens vers des informations concernant l'exécution, notamment les messages générés pendant l'exécution et les données de performances. Comme avec le Tableau de bord Integration Services, vous pouvez appliquer un filtre à la table afin de réduire les informations affichées.  
  
## <a name="related-content"></a>Contenu connexe  
 [Rapports du serveur Integration Services](../../integration-services/performance/monitor-running-packages-and-other-operations.md#reports)  
  
 [Outils de dépannage pour l'exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
