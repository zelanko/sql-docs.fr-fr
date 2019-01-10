---
title: srv_paramnumber (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramnumber
ms.assetid: d7a6dbff-71d9-4297-8a4f-bfd2876fe204
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e957b4c775554869b04805f009d4daed4f1055a4
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53361561"
---
# <a name="srvparamnumber-extended-stored-procedure-api"></a>srv_paramnumber (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne le numéro d'un paramètre d'appel de procédure stockée distante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_paramnumber (  
SRV_PROC *  
srvproc  
,  
DBCHAR *  
name  
,   
int  
namelen   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui correspond au handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu l'appel de procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *nom*  
 Pointeur vers le paramètre *name*.  
  
 *namelen*  
 Longueur de *name*. Si *name* se termine par le caractère NULL, définissez *namelen* sur SRV_NULLTERM.  
  
## <a name="returns"></a>Valeur renvoyée  
 Numéro de paramètre du paramètre nommé. Le premier paramètre est 1. S’il n’existe aucun paramètre nommé *name* ou aucune procédure stockée distante, 0 est retourné et un message est généré.  
  
## <a name="remarks"></a>Notes  
 Quand un appel de procédure stockée distante est effectué avec des paramètres, ceux-ci peuvent être passés par nom ou par position (sans nom). Si l'appel de procédure stockée distante est effectué avec certains paramètres passés par nom et certains passés par position, une erreur se produit. Le gestionnaire SRV_RPC est tout de même appelé, mais il apparaît comme s’il n’y avait aucun paramètre et **srv_rpcparams** retourne 0.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_rpcparams &#40;API de procédure stockée étendue&#41;](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
