---
title: "srv_rpcnumber (API de procédure stockée étendue) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_rpcnumber
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e4bd942eaf7bc53329bb8347262ca7ec02fd56c9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="srvrpcnumber-extended-stored-procedure-api"></a>srv_rpcnumber (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne le composant de numéro pour l'appel de procédure stockée distante actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
## <a name="returns"></a>Valeur renvoyée  
 Composant de numéro pour la procédure stockée distante actuelle. Si le client n'utilise pas de composant de numéro lors de l'exécution de la procédure stockée distante ou qu'il n'y a aucune procédure stockée distante en cours, il retourne - 1.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne uniquement le composant de numéro de la procédure stockée distante. Elle n'inclut pas les spécificateurs facultatifs pour le propriétaire, le nom de la procédure stockée distante et le nom de la base de données.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
