---
title: Envoi de jeux de résultats au serveur (API de procédure stockée étendue)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: c0ba957f0cde17f7accfeee66952fe2488a854bd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767745"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Envoi de jeux de résultats au serveur (API de procédure stockée étendue)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Lors de l’envoi d’un jeu de résultats à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la procédure stockée étendue doit appeler l’API appropriée comme suit :  
  
-   La fonction **srv_sendmsg** peut être appelée dans n’importe quel ordre avant ou après que toutes les lignes (le cas échéant) ont été envoyées avec **srv_sendrow**. Tous les messages doivent être envoyés au client avant que l’état d’achèvement ne soit envoyé avec **srv_senddone**.  
  
-   La fonction **srv_sendrow** est appelée une fois pour chaque ligne envoyée au client. Toutes les lignes doivent être envoyées au client avant que les messages, valeurs d’État ou États d’achèvement ne soient envoyés avec **srv_sendmsg**, l’argument **srv_status** de **SRV_PFIELD**ou **srv_senddone**.  
  
-   L’envoi d’une ligne dont toutes les colonnes n’ont pas été définies avec **srv_describe** amène l’application à déclencher un message d’erreur d’information et à retourner Fail au client. Dans ce cas, la ligne n'est pas envoyée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de procédures stockées étendues](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
