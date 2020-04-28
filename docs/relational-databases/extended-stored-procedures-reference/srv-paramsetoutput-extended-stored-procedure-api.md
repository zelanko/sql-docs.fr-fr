---
title: srv_paramsetoutput (API de procédure stockée étendue)
ms.custom: seo-dt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramsetoutput
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
ms.openlocfilehash: 9695f087557abe6c86369e2fddbd5bbd55cf7be5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74119384"
---
# <a name="srv_paramsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
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
  
## <a name="returns"></a>Retours  
 Si les informations de paramètre ont été définies avec succès, la valeur SUCCEED est retournée ; sinon, la valeur FAIL est retournée. La valeur FAIL est retournée dans les cas suivants :  
  
-   le paramètre n'est pas un paramètre de retour, ou  
  
-   l’argument *cbLen* n’est pas valide.  
  
## <a name="remarks"></a>Notes  
 **Remarque relative à la sécurité** Il est recommandé de revoir en détail le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
