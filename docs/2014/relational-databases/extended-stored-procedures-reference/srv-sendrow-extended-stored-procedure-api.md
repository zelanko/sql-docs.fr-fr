---
title: srv_sendrow (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 39635048aead2326468259f7b10d023b85bcc1b7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143253"
---
# <a name="srvsendrow-extended-stored-procedure-api"></a>srv_sendrow (API de procédure stockée étendue)
    
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
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **srv_sendrow** est appelée une fois pour chaque ligne envoyée au client. Toutes les lignes doivent être envoyées au client avant que les messages, valeurs d'état ou états d'achèvement ne soient envoyés avec **srv_sendmsg**, **srv_status**ou **srv_senddone**.  
  
 L'envoi d'une ligne dont toutes les colonnes n'ont pas été définies avec **srv_describe** oblige l'application de l'API de procédure stockée étendue à déclencher un message d'erreur d'information et à retourner FAIL au client. Dans ce cas, la ligne n'est pas envoyée.  
  
> [!NOTE]  
>  L'API de procédure stockée étendue ne prend pas en charge l'envoi de lignes calculées au client. En outre, si une ligne contenant des données `ntext`, `text` ou `image` est envoyée au client, le pointeur de texte et l'horodateur de texte ne sont pas inclus.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_describe &#40;API de procédure stockée étendue&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  