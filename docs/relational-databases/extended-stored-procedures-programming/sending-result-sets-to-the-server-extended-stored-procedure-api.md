---
title: "Envoi de jeux de résultats sur le serveur (API de procédure stockée étendu) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37eb992a4ef260b1d8b94991e95fae6e9326bd6f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Envoi de jeux de résultats au serveur (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Lors de l’envoi d’un jeu de résultats à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la procédure stockée étendue doit appeler l’API appropriée comme suit :  
  
-   Le **srv_sendmsg** fonction peut être appelée dans n’importe quel ordre avant ou après toutes les lignes (le cas échéant) ont été envoyées avec **srv_sendrow**. Tous les messages doivent être envoyés au client avant que l’état d’achèvement soit envoyé avec **srv_senddone**.  
  
-   La fonction **srv_sendrow** est appelée une fois pour chaque ligne envoyée au client. Toutes les lignes doivent être envoyés au client avant que les messages, les valeurs d’état ou états d’achèvement sont envoyés avec **srv_sendmsg**, le **srv_status** argument de **srv_pfield**, ou **srv_senddone**.  
  
-   Envoi d’une ligne qui n’a pas de toutes ses colonnes définies avec **srv_describe** entraîne l’application génère un message d’erreur d’information et le renvoi de FAIL au client. Dans ce cas, la ligne n'est pas envoyée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de procédures stockées étendues](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
