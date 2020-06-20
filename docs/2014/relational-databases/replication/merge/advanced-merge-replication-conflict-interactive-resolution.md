---
title: Résolution interactive des conflits | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57d0de17c4d958a1b842748810ba24717e6866e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049456"
---
# <a name="interactive-conflict-resolution"></a>Interactive Conflict Resolution
  La réplication [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] propose un programme de résolution interactif qui vous permet de résoudre manuellement les conflits au cours d’une synchronisation à la demande dans le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Activé lors de l'exécution, le résolveur interactif est une interface graphique qui affiche des données pour chaque ligne conflictuelle et qui propose les options nécessaires à la consultation et à la modification de ces données, permettant ainsi de résoudre chaque conflit individuellement.  
  
 Le résolveur interactif ressemble à l'outil d'affichage des conflits. Cependant, l'outil d'affichage des conflits affiche les résultats des conflits déjà résolus après la synchronisation de fusion et le résolveur interactif affiche chaque conflit non résolu, ce qui vous permet de déterminer l'issue de chacun d'eux durant la synchronisation de fusion. Un opérateur doit être disponible pour analyser le résolveur interactif lorsqu'un conflit se produit.  
  
> [!NOTE]  
>  La résolution interactive nécessite le Gestionnaire de synchronisation Windows. Si une synchronisation est effectuée en dehors du Gestionnaire de synchronisation Windows (comme une synchronisation planifiée ou à la demande dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou le Moniteur de réplication), les conflits sont résolus automatiquement sans intervention de l'utilisateur, en fonction de l'outil de résolution spécifié pour l'article. Les conflits qui concernent des enregistrements logiques ne sont pas affichés dans le résolveur interactif. Pour afficher des informations sur ces conflits, utilisez des procédures stockées de réplication. Pour plus d’informations, consultez [Afficher les informations relatives aux conflits pour les publications de fusion &#40;programmation Transact-SQL de la réplication&#41;](../view-conflict-information-for-merge-publications.md).  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a>Résolveurs d'articles et résolveur interactif  
 Les résolveurs de conflits (qu'il s'agisse du résolveur par défaut, d'un gestionnaire de logique métier ou d'un résolveur personnalisé) sont affectés à des articles spécifiques lors de la création d'une publication, et ils font appel à un ensemble de règles prédéterminées pour définir le dataset à utiliser lorsque des données de ligne en conflit sont entrées. Le résolveur interactif n'est pas un résolveur de conflits isolé avec des règles permettant de distinguer les vainqueurs et les perdants d'un conflit, mais un outil utilisé conjointement avec les résolveurs de fusion par défaut et personnalisés. Le résolveur d'articles détermine toujours la ligne gagnante et la ligne perdante, mais le résolveur interactif permet aux utilisateurs d'intervenir pour accepter, rejeter ou modifier les résultats.  
  
 Pour utiliser le résolveur interactif, la résolution interactive doit être activée pour chaque article et abonnement qui l'exige. Une fois qu'il est activé pour un ou plusieurs articles et abonnements, le résolveur interactif est utilisé lorsqu'un conflit est détecté durant une synchronisation de fusion.  
  
 Pour utiliser le programme de résolution interactif, consultez [Spécifier la résolution interactive des conflits pour les articles de fusion](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution) et [Synchroniser un abonnement à l’aide du Gestionnaires de synchronisation Windows &#40;Gestionnaire de synchronisation Windows&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
