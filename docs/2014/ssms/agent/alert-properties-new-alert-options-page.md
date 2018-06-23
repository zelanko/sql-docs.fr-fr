---
title: 'Propriétés de l’alerte : Nouvelle alerte (Page Options) | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b5e65400a2b7f82316ecdae3f92d34e40ac0715e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041291"
---
# <a name="alert-properties-new-alert-options-page"></a>Propriétés de l’alerte : Nouvelle alerte (Page Options)
  Cette page vous permet d'afficher et de modifier les options des alertes de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
 **Courrier électronique**  
 Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications par courrier électronique.  
  
 **Radiomessagerie**  
 Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications de radiomessagerie.  
  
 **Envoi réseau**  
 Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications d'envoi réseau.  
  
 **Message de notification supplémentaire à envoyer**  
 Tapez tout texte supplémentaire à inclure dans les messages de notification.  
  
 **Délai entre les réponses**  
 Spécifiez un délai pour les occurrences répétées de l'événement. Certains événements peuvent se produire fréquemment au court d'une courte période de temps. Dans ce cas, vous voudrez peut-être savoir que l'événement s'est produit sans vouloir de réponse pour chaque événement. Utilisez cette option pour spécifier un délai d'attente. Avec un délai, une fois que l'alerte a répondu à un événement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent attend jusqu'au délai spécifié avant de répondre de nouveau, que l'événement se produise ou non pendant ce délai d'attente.  
  
 **Minutes**  
 Spécifiez un délai en minutes. Pour répondre chaque fois qu'un événement se produit, spécifiez 0 minutes et 0 secondes.  
  
 **Secondes**  
 Spécifiez un délai en secondes. Pour répondre chaque fois qu'un événement se produit, spécifiez 0 minutes et 0 secondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Alertes](alerts.md)  
  
  