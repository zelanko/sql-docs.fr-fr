---
title: srv_got_attention (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_got_attention
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 88919fa49417b574d8af06619f6d362aebf86e85
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Vérifie si la connexion ou la tâche en cours a besoin d'être annulée et retourne TRUE si la connexion est arrêtée ou le lot supprimé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *srvproc*  
 Pointeur identifiant une connexion de base de données.  
  
## <a name="return-value"></a>Valeur retournée  
 TRUE si la connexion est arrêtée ou le lot supprimé. FALSE si la connexion ou le lot est actif.  
  
## <a name="remarks"></a>Notes  
 Une procédure stockée étendue dont l’exécution est longue doit contrôler l’attention du serveur en appelant périodiquement **srv_got_attention** afin que la procédure puisse se terminer si la connexion est arrêtée ou que le lot est abandonné.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
