---
title: Planifier les stratégies | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8becd7ad30acf1ea2a63feae4760091aede70c06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033501"
---
# <a name="schedule-the-policies"></a>Planifier les stratégies
  Dans cette tâche, vous planifierez les stratégies des meilleures pratiques que vous avez importées dans la tâche précédente.  
  
### <a name="to-schedule-the-best-practices-policies"></a>Pour planifier les stratégies des meilleures pratiques  
  
1.  Dans l’Explorateur d’objets, développez **gestion**, gestion de la **stratégie**, **stratégies**, cliquez avec le bouton droit sur une stratégie des meilleures pratiques, puis cliquez sur **Propriétés**.  
  
    > [!NOTE]  
    >  En guise d’alternative, pour identifier facilement les stratégies associées aux meilleures pratiques et trier les catégories des meilleures pratiques, développez **gestion**, gestion de la **stratégie**, puis cliquez sur **stratégies**. Dans le menu **Affichage** , cliquez sur **Détails de l’Explorateur d’objets**. Dans le volet Détails de l' **Explorateur d’objets** , cliquez sur l’en-tête **catégorie** pour trier les stratégies par catégorie. Les stratégies des meilleures pratiques ont le préfixe **Microsoft Best Practices**. Cliquez avec le bouton droit sur la stratégie que vous souhaitez configurer, puis cliquez sur **Propriétés**.  
  
2.  Sur la page **général** de la boîte de dialogue **ouvrir une stratégie** , dans la liste mode d' **évaluation** , cliquez sur **planification**.  
  
3.  En regard de la zone **planification** , cliquez sur **choisir** pour spécifier une planification existante ou sur **nouveau** pour créer une planification.  
  
4.  Une fois que vous avez configuré une planification, vous pouvez activer la case à cocher **activé** vers le haut de la page pour activer la stratégie planifiée.  
  
5.  Répétez les étapes 1 à 4 pour chaque stratégie à planifier.  
  
    > [!NOTE]  
    >  Pour afficher les résultats d'évaluation après l'exécution d'une stratégie planifiée, ouvrez le journal Historique de la stratégie sur l'instance cible. Pour ouvrir le journal, cliquez avec le bouton droit sur **gestion des stratégies**, puis cliquez sur **afficher l’historique**.  
  
## <a name="summary"></a>Récapitulatif  
 Vous avez configuré l'exécution de stratégies planifiées sur une instance unique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si vous souhaitez déployer des stratégies planifiées vers plusieurs instances, passez à la tâche suivante dans ce didacticiel.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Déployer des stratégies planifiées sur plusieurs instances](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
