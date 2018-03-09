---
title: "srv_paraminfo (API de procédure stockée étendue) | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
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
- srv_paraminfo
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 16ca2d41922461768b8edba1e12724e4bc852b15
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="srvparaminfo-extended-stored-procedure-api"></a>srv_paraminfo (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez plutôt l'intégration du CLR.  
  
 Retourne des informations sur un paramètre. Cette fonction remplace les fonctions suivantes : [srv_paramtype](../../relational-databases/extended-stored-procedures-reference/srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](../../relational-databases/extended-stored-procedures-reference/srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](../../relational-databases/extended-stored-procedures-reference/srv-parammaxlen-extended-stored-procedure-api.md) et [srv_paramdata](../../relational-databases/extended-stored-procedures-reference/srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** prend en charge les types de données dans [Data Types](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md) et les données de longueur nulle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Handle d'une connexion cliente.  
  
 *n*  
 Nombre ordinal du paramètre à définir. Le premier paramètre est 1.  
  
 *pbType*  
 Type de données du paramètre.  
  
 *pcbMaxLen*  
 Pointeur vers la longueur maximale du paramètre.  
  
 *pcbActualLen*  
 Pointeur vers la longueur réelle du paramètre. La valeur 0 (\**pcbActualLen* == 0) indique des données de longueur nulle si **pfNull* a la valeur FALSE.  
  
 *pbData*  
 Pointeur vers la mémoire tampon des données de paramètre. Si *pbData* n’est pas NULL, l’API de procédure stockée étendue écrit \**pcbActualLen* octets de données dans \**pbData*. Si *pbData* est NULL, aucune donnée n’est écrite dans \**pbData*, mais la fonction retourne \**pbType*, \**pcbMaxLen*, \**pcbActualLen* et **pfNull*. Cette mémoire tampon doit être gérée par l'application.  
  
 *pfNull*  
 Pointeur vers un indicateur null. **pfNull* a la valeur TRUE si la valeur du paramètre est NULL.  
  
## <a name="returns"></a>Valeur renvoyée  
 Si les informations sur le paramètre ont été obtenues avec succès, la valeur SUCCEED est retournée ; sinon, FAIL. La valeur FAIL est retournée en l’absence de procédure stockée distante active et en l’absence d’un *n*ième paramètre de procédure stockée.  
  
## <a name="remarks"></a>Notes   
 **Remarque relative à la sécurité** Il est recommandé de revoir en détail le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a> Voir aussi  
 [Guide de référence du programmeur sur les procédures stockées étendues](../../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
  
  
