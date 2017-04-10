---
title: "Afficher les entr&#233;es de journal dans la fen&#234;tre Journaux d&#39;&#233;v&#233;nements | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "journaux [Integration Services], affichage"
  - "packages Integration Services, journaux"
  - "packages [Integration Services], journaux"
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Afficher les entr&#233;es de journal dans la fen&#234;tre Journaux d&#39;&#233;v&#233;nements
  Cette procédure explique comment exécuter un package et afficher les entrées de journal qu'il écrit. Vous pouvez visualiser les entrées du journal en temps réel. Les entrées de journal écrites dans la fenêtre **Journaux d’événements** peuvent également être copiées et enregistrées pour une analyse ultérieure.  
  
 Il n’est pas nécessaire d’écrire les entrées de journal dans un journal pour écrire ces entrées dans la fenêtre **Journaux d’événements**.  
  
### Pour afficher les entrées de journal  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans le menu **SSIS** , cliquez sur **Journaux d'événements**. Vous pouvez éventuellement afficher la fenêtre **Journaux d’événements** en mappant la commande View.LogEvents à une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options**.  
  
3.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
     Dès que l’exécution rencontre les événements et les messages personnalisés activés à des fins de journalisation, les entrées de journal de chaque événement ou message sont écrites dans la fenêtre **Journaux d’événements**.  
  
4.  Dans le menu **Débogage** , cliquez sur **Arrêter le débogage**.  
  
     Les entrées de journal restent disponibles dans la fenêtre **Journaux d’événements** jusqu’à la prochaine exécution du package, l’exécution d’un autre package ou la fermeture de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
5.  Affichez les entrées de journal dans la fenêtre **Journaux d’événements**.  
  
6.  Le cas échéant, cliquez sur les entrées de journal à copier, cliquez avec le bouton droit, puis cliquez sur **Copier**.  
  
7.  Vous pouvez également double-cliquer sur une entrée de journal, puis dans la boîte de dialogue **Entrée de journal**, afficher les détails d’une seule entrée de journal.  
  
8.  Dans la boîte de dialogue **Entrée de journal**, cliquez sur les flèches haut et bas pour afficher l’entrée de journal précédente ou suivante, puis cliquez sur l’icône de copie pour copier l’entrée de journal.  
  
9. Ouvrez un éditeur de texte, collez, puis enregistrez l'entrée de journal dans un fichier texte.  
  
## Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  