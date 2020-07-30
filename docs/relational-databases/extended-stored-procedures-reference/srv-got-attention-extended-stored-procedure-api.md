---
title: srv_got_attention (API de procédure stockée étendue) | Microsoft Docs
description: Découvrez comment srv_got_attention vérifie si la connexion ou la tâche en cours doit être abandonnée et renvoie la valeur TRUE si la connexion est arrêtée ou si le lot est abandonné.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b5ba738ddd220d83cffe2c28b5629ee491d293f
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248447"
---
# <a name="srv_got_attention-extended-stored-procedure-api"></a>srv_got_attention (API de procédure stockée étendue)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
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
  
## <a name="return-value"></a>Valeur de retour  
 TRUE si la connexion est arrêtée ou le lot supprimé. FALSE si la connexion ou le lot est actif.  
  
## <a name="remarks"></a>Notes  
 Une procédure stockée étendue dont l’exécution est longue doit contrôler l’attention du serveur en appelant périodiquement **srv_got_attention** afin que la procédure puisse se terminer si la connexion est arrêtée ou que le lot est abandonné.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
