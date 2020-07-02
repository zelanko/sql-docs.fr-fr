---
title: srv_rpcnumber (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcnumber
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
author: rothja
ms.author: jroth
ms.openlocfilehash: d828ad55c93f5341370e9daa98ead6ece0997f02
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755890"
---
# <a name="srv_rpcnumber-extended-stored-procedure-api"></a>srv_rpcnumber (API de procédure stockée étendue)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
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
  
## <a name="returns"></a>Retours  
 Composant de numéro pour la procédure stockée distante actuelle. Si le client n'utilise pas de composant de numéro lors de l'exécution de la procédure stockée distante ou qu'il n'y a aucune procédure stockée distante en cours, il retourne - 1.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction retourne uniquement le composant de numéro de la procédure stockée distante. Elle n'inclut pas les spécificateurs facultatifs pour le propriétaire, le nom de la procédure stockée distante et le nom de la base de données.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
