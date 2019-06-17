---
title: Afficher les entrées de journal dans la fenêtre journaux d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ed348a4525024052946ac30bfe6ec780ca86a4b6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66054626"
---
# <a name="view-log-entries-in-the-log-events-window"></a>Afficher les entrées de journal dans la fenêtre Journaux d’événements
  Cette procédure explique comment exécuter un package et afficher les entrées de journal qu'il écrit. Vous pouvez visualiser les entrées du journal en temps réel. Les entrées de journal écrites dans la fenêtre **Journaux d’événements** peuvent également être copiées et enregistrées pour une analyse ultérieure.  
  
 Il n’est pas nécessaire d’écrire les entrées de journal dans un journal pour écrire ces entrées dans la fenêtre **Journaux d’événements** .  
  
### <a name="to-view-log-entries"></a>Pour afficher les entrées de journal  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans le menu **SSIS** , cliquez sur **Journaux d'événements**. Vous pouvez éventuellement afficher la fenêtre **Journaux d’événements** en mappant la commande View.LogEvents à une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options** .  
  
3.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
     Dès que l’exécution rencontre les événements et les messages personnalisés activés à des fins de journalisation, les entrées de journal de chaque événement ou message sont écrites dans la fenêtre **Journaux d’événements** .  
  
4.  Dans le menu **Débogage** , cliquez sur **Arrêter le débogage**.  
  
     Les entrées de journal restent disponibles dans la fenêtre **Journaux d’événements** jusqu’à la prochaine exécution du package, l’exécution d’un autre package ou la fermeture de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
5.  Affichez les entrées de journal dans la fenêtre **Journaux d’événements** .  
  
6.  Le cas échéant, cliquez sur les entrées de journal à copier, cliquez avec le bouton droit, puis cliquez sur **Copier**.  
  
7.  Vous pouvez également double-cliquer sur une entrée de journal, puis dans la boîte de dialogue **Entrée de journal** , afficher les détails d’une seule entrée de journal.  
  
8.  Dans la boîte de dialogue **Entrée de journal** , cliquez sur les flèches haut et bas pour afficher l’entrée de journal précédente ou suivante, puis cliquez sur l’icône de copie pour copier l’entrée de journal.  
  
9. Ouvrez un éditeur de texte, collez, puis enregistrez l'entrée de journal dans un fichier texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
