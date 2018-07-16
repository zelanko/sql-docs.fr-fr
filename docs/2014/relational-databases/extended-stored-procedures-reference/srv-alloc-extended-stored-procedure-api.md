---
title: srv_alloc (API de procédure stockée étendue) | Microsoft Docs
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
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a5cc264f27814ed5d577dddfae5bc0d2cb81cc34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236779"
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Alloue la mémoire dynamiquement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *size*  
 Spécifie le nombre d'octets à allouer.  
  
## <a name="returns"></a>Valeur renvoyée  
 Un pointeur vers l'espace qui vient d'être alloué. Si *size* octets ne peuvent pas être alloués, un pointeur Null est retourné.  
  
## <a name="remarks"></a>Notes  
 La fonction **srv_alloc** est équivalente à la fonction API [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **GlobalAlloc**. Les fonctions ordinaires de gestion de la mémoire du runtime C de l'API Windows peuvent être utilisées dans une application API de procédure stockée étendue.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
