---
title: Planifier les stratégies | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ab324e94efdfdebea0387a2212440ed971c11aa5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094439"
---
# <a name="schedule-the-policies"></a>Planifier les stratégies
  Dans cette tâche, vous planifierez les stratégies des meilleures pratiques que vous avez importées dans la tâche précédente.  
  
### <a name="to-schedule-the-best-practices-policies"></a>Pour planifier les stratégies des meilleures pratiques  
  
1.  Dans l’Explorateur d’objets, développez **gestion**, développez **gestion des stratégies de**, développez **stratégies**, avec le bouton droit à une stratégie des meilleures pratiques, puis cliquez sur  **Propriétés**.  
  
    > [!NOTE]  
    >  Comme alternative, voir facilement les stratégies qui sont associés aux meilleures pratiques et trier les meilleures pratiques des catégories, développez **gestion**, développez **gestion des stratégies de**, puis cliquez sur **Stratégies**. Dans le menu **Affichage** , cliquez sur **Détails de l’Explorateur d’objets**. Dans le **détails de l’Explorateur d’objets** volet, cliquez sur le **catégorie** titre pour trier les stratégies par catégorie. Les stratégies des meilleures pratiques ont le préfixe **meilleures pratiques Microsoft**. Avec le bouton droit de la stratégie que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
2.  Sur le **général** page de la **ouvrir une stratégie** boîte de dialogue le **Mode d’évaluation** , cliquez sur **selon planification**.  
  
3.  À côté du **planification** , cliquez sur **choisir** pour spécifier une planification existante ou cliquez sur **New** pour créer une planification.  
  
4.  Une fois que vous avez configuré une planification, vous pouvez sélectionner le **activé** case à cocher en haut de la page pour activer la stratégie planifiée.  
  
5.  Répétez les étapes 1 à 4 pour chaque stratégie à planifier.  
  
    > [!NOTE]  
    >  Pour afficher les résultats d'évaluation après l'exécution d'une stratégie planifiée, ouvrez le journal Historique de la stratégie sur l'instance cible. Pour ouvrir le journal, avec le bouton droit **gestion des stratégies de**, puis cliquez sur **afficher l’historique**.  
  
## <a name="summary"></a>Résumé  
 Vous avez configuré l'exécution de stratégies planifiées sur une instance unique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si vous souhaitez déployer des stratégies planifiées vers plusieurs instances, passez à la tâche suivante dans ce didacticiel.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Déployer des stratégies planifiées sur plusieurs instances](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
