---
title: srv_sendrow (API de procédure stockée étendue) | Microsoft Docs
description: En savoir plus sur les srv_sendrow dans l’API de procédure stockée étendue. srv_sendrow transmet une ligne de données au client.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_sendrow
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cbe5886d19ca1da9bdc2bdea09ce86d142b44d9
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248209"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a>srv_sendrow (API de procédure stockée étendue)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Transmet une ligne de données au client.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la demande de langue). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **srv_sendrow** est appelée une fois pour chaque ligne envoyée au client. Toutes les lignes doivent être envoyées au client avant que les messages, valeurs d'état ou états d'achèvement ne soient envoyés avec **srv_sendmsg**, **srv_status**ou **srv_senddone**.  
  
 L'envoi d'une ligne dont toutes les colonnes n'ont pas été définies avec **srv_describe** oblige l'application de l'API de procédure stockée étendue à déclencher un message d'erreur d'information et à retourner FAIL au client. Dans ce cas, la ligne n'est pas envoyée.  
  
> [!NOTE]  
>  L'API de procédure stockée étendue ne prend pas en charge l'envoi de lignes calculées au client. En outre, si une ligne contenant des données **ntext**, **text**ou **image** est envoyée au client, le pointeur de texte et l'horodateur de texte ne sont pas inclus.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_describe &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
