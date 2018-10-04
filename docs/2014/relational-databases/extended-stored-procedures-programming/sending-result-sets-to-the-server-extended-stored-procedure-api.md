---
title: Envoi de jeux de résultats au serveur (API de procédure stockée étendu) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9766b73f624362a24c4b9e91ccd279cbcaabc527
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137889"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Envoi de jeux de résultats au serveur (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Lors de l’envoi d’un jeu de résultats à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la procédure stockée étendue doit appeler l’API appropriée comme suit :  
  
-   Le **srv_sendmsg** fonction peut être appelée dans n’importe quel ordre avant ou après que toutes les lignes (le cas échéant) ont été envoyées avec **srv_sendrow**. Tous les messages doivent être envoyés au client avant que l’état d’achèvement est envoyé avec **srv_senddone**.  
  
-   La fonction **srv_sendrow** est appelée une fois pour chaque ligne envoyée au client. Toutes les lignes doivent être envoyées au client avant que les messages, les valeurs d’état ou états d’achèvement sont envoyées avec **srv_sendmsg**, le **srv_status** argument de **srv_pfield**, ou **srv_senddone**.  
  
-   L’envoi d’une ligne qui n’ont pas été toutes ses colonnes définies avec **srv_describe** oblige l’application à déclencher un message d’erreur d’information et à retourner FAIL au client. Dans ce cas, la ligne n'est pas envoyée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de procédures stockées étendues](creating-extended-stored-procedures.md)  
  
  
