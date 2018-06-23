---
title: srv_got_attention (API de procédure stockée étendue) | Microsoft Docs
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
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9553592c01e318de3e090900d2f6b4260301146f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144514"
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Vérifie si la connexion ou la tâche en cours a besoin d'être annulée et retourne TRUE si la connexion est arrêtée ou le lot supprimé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
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
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  