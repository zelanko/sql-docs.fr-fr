---
title: "srv_pfieldex (API de procédure stockée étendue) | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_pfieldex
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11e0eeb19711c6070eeca4fdae23607d420289b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="srvpfieldex-extended-stored-procedure-api"></a>srv_pfieldex (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne un pointeur vers des données qui contiennent le champ SRV_PROC demandé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *field*  
 Spécifie le champ *srvproc* à retourner.  
  
|Champ| Description|Type renvoyé|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|LCID du message de la session active.|ULONG*|  
|SRV_INSTANCENAME|Nom de l'instance (si elle est nommée) ; sinon, retourne NULL.|WCHAR*|  
  
 *len*  
 Pointeur vers une variable **int** contenant la longueur de la valeur *field* retournée en octets. Si *len* a la valeur NULL, la longueur n’est pas retournée. Quand NULL est retourné **len* a la valeur 0.  
  
## <a name="returns"></a>Valeur renvoyée  
 Pointeur vers des données dont le type dépend de *field*. NULL est retourné quand *len* a la valeur 0 ou quand *srvproc* a la valeur NULL. Si *field* est inconnu, la valeur NULL est retournée. Quand NULL est retourné **len* a la valeur 0.  
  
> [!IMPORTANT]  
>  La mémoire tampon retournée à partir du serveur doit être en lecture seule. Dans le cas contraire, l'état du serveur peut être endommagé.  
  
## <a name="remarks"></a>Notes  
 **Remarque relative à la sécurité** Il est recommandé de revoir en détail le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
