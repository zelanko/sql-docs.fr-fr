---
title: srv_paramsetoutput (API de procédure stockée étendue) | Microsoft Docs
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
- srv_paramsetoutput
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3d1ea832995c65a0b0b07fc4f666523fbdf07b31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190419"
---
# <a name="srvparamsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Définit la valeur d'un paramètre de retour. Cette fonction remplace la fonction **srv_paramset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Handle d’une connexion cliente.  
  
 *n*  
 Est le nombre ordinal du paramètre à définir. Le premier paramètre est 1.  
  
 *pbData*  
 Pointeur vers la valeur de données à renvoyer au client en tant que paramètre de retour de procédure.  
  
 *cbLen*  
 Est la longueur réelle des données à retourner. Si le type de données du paramètre spécifie des valeurs de longueur constante et qu’il n’autorise pas les valeurs NULL (par exemple, *srvbit* ou *srvint1*), *cbLen* est ignoré. La valeur 0 indique des données de longueur nulle si *fNull* a la valeur FALSE.  
  
 *fNull*  
 Indicateur spécifiant si la valeur du paramètre de retour est NULL. Attribuez la valeur TRUE à cet indicateur si le paramètre doit avoir la valeur NULL. La valeur par défaut est FALSE. Si *fNull* a la valeur TRUE, *cbLen* doit avoir la valeur 0, sinon la fonction échoue.  
  
## <a name="returns"></a>Valeur renvoyée  
 Si les informations de paramètre ont été définies avec succès, la valeur SUCCEED est retournée ; sinon, la valeur FAIL est retournée. La valeur FAIL est retournée dans les cas suivants :  
  
-   le paramètre n'est pas un paramètre de retour, ou  
  
-   l’argument *cbLen* n’est pas valide.  
  
## <a name="remarks"></a>Notes  
 **Remarque relative à la sécurité** Il est recommandé de revoir en détail le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
