---
title: "Ajouter un journal pour les compteurs de performances de flux de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compteurs de performances [Integration Services]"
  - "compteurs [Integration Services]"
  - "journaux [Integration Services], compteurs de flux de données"
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Ajouter un journal pour les compteurs de performances de flux de donn&#233;es
  Cette procédure décrit comment ajouter un journal pour les compteurs de performances fournis par le moteur de flux de données.  
  
> [!NOTE]  
>  Si vous installez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur un ordinateur qui exécute [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], puis que vous mettez à niveau cet ordinateur vers [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)], le processus de mise à niveau supprime les compteurs de performances [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de l’ordinateur. Pour restaurer les compteurs de performances de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur l’ordinateur, exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode réparation.  
  
### Pour ajouter un journal des compteurs de performances  
  
1.  Dans le **Panneau de configuration**, si vous utilisez l’affichage classique, cliquez sur **Outils d’administration**. Si vous utilisez l’affichage des catégories, cliquez sur **Performances et maintenance**, puis sur **Outils d’administration**.  
  
2.  Cliquez sur **Performances**.  
  
3.  Dans la boîte de dialogue **Performances**, développez **Journaux et alertes de performances**, cliquez avec le bouton droit sur **Journaux de compteurs**, puis cliquez sur **Nouveaux paramètres de journal**. Tapez le nom du journal. Par exemple, tapez **MonJournal**.  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **MonJournal**, cliquez sur **Ajouter des compteurs**.  
  
6.  Cliquez sur **Utiliser les compteurs locaux de l’ordinateur** pour journaliser les compteurs de performances sur l’ordinateur local ou cliquez sur **Choisir les compteurs sur :** et sélectionnez un ordinateur dans la liste pour journaliser les compteurs de performances sur l’ordinateur spécifié.  
  
7.  Dans la boîte de dialogue **Ajouter des compteurs**, sélectionnez **SQL Server : pipeline SSIS** dans la liste **Objet de performance**.  
  
8.  Pour sélectionner les compteurs de performances, effectuez l'une des actions suivantes :  
  
    -   Sélectionnez **Tous les compteurs** pour journaliser tous les compteurs de performances.  
  
    -   Sélectionnez **Sélectionner les compteurs dans la liste** et sélectionnez les compteurs de performances à utiliser.  
  
9. Cliquez sur **Ajouter**.  
  
10. Cliquez sur **Fermer**.  
  
11. Dans la boîte de dialogue **MonJournal**, vérifiez la liste des compteurs de performances journalisés dans la liste **Compteurs**.  
  
12. Pour ajouter des compteurs supplémentaires, répétez les étapes 5 à 10.  
  
13. Cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Vous devez démarrer le service Journaux et alertes de performance à l'aide d'un compte local ou d'un compte de domaine membre du groupe Administrateurs.  
  
## Voir aussi  
 [Compteurs de performances](../../integration-services/performance/performance-counters.md)   
 [Afficher les entrées de journal dans la fenêtre Journaux d'événements](../../integration-services/performance/view-log-entries-in-the-log-events-window.md)  
  
  