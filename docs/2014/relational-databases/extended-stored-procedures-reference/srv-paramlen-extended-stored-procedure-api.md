---
title: srv_paramlen (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2c858d0fa8579aff288efd7026ab4b65035bad8d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63127194"
---
# <a name="srv_paramlen-extended-stored-procedure-api"></a>srv_paramlen (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Retourne la longueur de données d'un paramètre d'appel de procédure stockée distante. Cette fonction a été remplacée par la fonction **srv_paraminfo**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui correspond au handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu l'appel de procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *n*  
 Indique le numéro du paramètre. Le premier paramètre est 1.  
  
## <a name="returns"></a>Retours  
 Longueur réelle, en octets, des données de paramètre. En l’absence de *n*ième paramètre ou de procédure stockée distante, la valeur -1 est retournée. Si le *n*ième paramètre est NULL, la valeur retournée est 0.  
  
 Cette fonction retourne les valeurs suivantes, si le paramètre est l’un des types [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] de données système suivants.  
  
|Nouveaux types de données|Longueur de données d'entrée|  
|--------------------|-----------------------|  
|`BITN`|**Null :** 1<br /><br /> **Zéro :** 1<br /><br /> **>= 255 :** NON APPLICABLE<br /><br /> **<255 :** NON APPLICABLE|  
|`BIGVARCHAR`|**Null :** 0<br /><br /> **Zéro :** 1<br /><br /> **>= 255 :** 255<br /><br /> **<255 :** *longueur* réelle|  
|`BIGCHAR`|**Null :** 0<br /><br /> **Zéro :** 255<br /><br /> **>= 255 :** 255<br /><br /> **<255 :** 255|  
|`BIGBINARY`|**Null :** 0<br /><br /> **Zéro :** 255<br /><br /> **>= 255 :** 255<br /><br /> **<255 :** 255|  
|`BIGVARBINARY`|**Null :** 0<br /><br /> **Zéro :** 1<br /><br /> **>= 255 :** 255<br /><br /> **<255 :** *longueur* réelle|  
|`NCHAR`|**Null :** 0<br /><br /> **Zéro :** 255<br /><br /> **>= 255 :** 255<br /><br /> **<255 :** 255|  
|`NVARCHAR`|**Null :** 0<br /><br /> **Zéro :** 1<br /><br /> **>= 255 :** 255<br /><br /> **<255 :** *longueur* réelle|  
|`NTEXT`|**Null :** -1<br /><br /> **Zéro :** -1<br /><br /> **>= 255 :** -1<br /><br /> **<255 :** -1|  
  
 \**Len* réel = longueur de la chaîne de caractères multioctets (CCH)  
  
## <a name="remarks"></a>Notes  
 Chaque paramètre de procédure stockée distante possède une longueur de données réelle et une longueur de données maximale. Pour les types de données de longueur fixe standard qui n'autorisent pas les valeurs NULL, les longueurs réelle et maximale sont les mêmes. Pour les types de données de longueur variable, les longueurs peuvent varier. Par exemple, un paramètre déclaré comme `varchar(30)` peut posséder des données longues de 10 octets seulement. La longueur réelle du paramètre est 10 et sa longueur maximale est 30. La fonction **srv_paramlen** obtient la longueur de données réelle, en octets, d’une procédure stockée distante. Pour obtenir la longueur de données maximale d’un paramètre, utilisez **srv_parammaxlen**.  
  
 Quand un appel de procédure stockée distante est effectué avec des paramètres, ceux-ci peuvent être passés par nom ou par position (sans nom). Si l'appel de procédure stockée distante est effectué avec certains paramètres passés par nom et certains passés par position, une erreur se produit. Le gestionnaire SRV_RPC est tout de même appelé, mais il apparaît comme s’il n’y avait aucun paramètre et **srv_rpcparams** retourne 0.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_paraminfo &#40;API de procédure stockée étendue&#41;](srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams &#40;API de procédure stockée étendue&#41;](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
