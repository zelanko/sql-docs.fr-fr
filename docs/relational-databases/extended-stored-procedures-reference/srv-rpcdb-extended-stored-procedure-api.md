---
title: "srv_rpcdb (API de procédure stockée étendue) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
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
- srv_rpcdb
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17798468b38998bea8ca06c2d2c73407bde37014
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="srvrpcdb-extended-stored-procedure-api"></a>srv_rpcdb (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez plutôt l'intégration du CLR.  
  
 Retourne le composant de nom de base de données pour la procédure stockée distante actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *len*  
 Pointeur vers une variable **int** qui reçoit la longueur du nom de la base de données. Si *len* a la valeur NULL, la longueur du nom de la base de données n’est pas retournée.  
  
## <a name="returns"></a>Valeur renvoyée  
 Pointeur DBCHAR vers la chaîne terminée par le caractère NULL pour la partie du nom de base de données de la procédure stockée distante actuelle. S’il n’y a pas de procédure stockée distante actuelle, NULL est retourné et le paramètre *len* prend la valeur -1.  
  
## <a name="remarks"></a>Notes   
 Cette fonction retourne uniquement le composant de base de données du nom d'objet de la procédure stockée distante. Elle n'inclut pas les spécificateurs facultatifs pour le propriétaire, le nom de procédure stockée distante et le numéro de procédure stockée distante.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
