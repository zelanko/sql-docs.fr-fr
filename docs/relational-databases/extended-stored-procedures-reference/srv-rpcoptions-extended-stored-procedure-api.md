---
title: "srv_rpcoptions (API de procédure stockée étendue) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_rpcoptions
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 151157986bee12807eccf4919248fbeb7dbcc29a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez plutôt l'intégration du CLR.  
  
 Retourne les options d'exécution pour la procédure stockée distante actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
## <a name="returns"></a>Valeur renvoyée  
 Bitmap qui contient les indicateurs d'exécution joints dans un OR logique pour la procédure stockée distante actuelle. En l'absence de procédure stockée distante actuelle, 0 est retourné et un message est généré.  
  
## <a name="remarks"></a>Notes   
 Le tableau ci-dessous décrit chaque indicateur d'exécution.  
  
|Indicateur d'exécution|Description|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Le client a demandé des résultats sans informations de métadonnées. Cet indicateur est utilisé uniquement quand le client communique avec une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une application de l'API de procédure stockée étendue ne peut pas omettre les informations de métadonnées.|  
|SRV_RECOMPILE|Le client a demandé de recompiler la procédure stockée distante avant de l'exécuter. Cet indicateur peut ne pas s'appliquer à une application de l'API de procédure stockée étendue.|  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
