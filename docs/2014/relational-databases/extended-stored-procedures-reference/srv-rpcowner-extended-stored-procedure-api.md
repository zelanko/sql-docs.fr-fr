---
title: srv_rpcowner (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcowner
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 68e5d0214a2bd14a466b7a0c40f792031d3fac5d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62745500"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a>srv_rpcowner (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Retourne le composant propriétaire de la procédure stockée distante actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *Len*  
 Pointeur vers une variable de type entier qui reçoit la longueur du nom du propriétaire. Le paramètre *len* peut être NULL ; dans ce cas, la longueur du composant propriétaire n’est pas retournée.  
  
## <a name="returns"></a>Retours  
 Un pointeur DBCHAR vers le composant propriétaire, terminé par le caractère NULL, de la procédure stockée distante actuelle. En l’absence de procédure stockée distante actuelle, NULL est retourné et *len* est défini sur -1.  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne uniquement le composant propriétaire de la procédure stockée distante. Elle n'inclut pas les spécificateurs facultatifs pour le nom, le nom de la procédure stockée distante et le numéro de la procédure stockée distante.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
