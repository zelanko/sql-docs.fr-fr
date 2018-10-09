---
title: srv_setcoldata (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f56c16d1b497bffb55362eb63ed755456c6a6406
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152469"
---
# <a name="srvsetcoldata-extended-stored-procedure-api"></a>srv_setcoldata (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Spécifie l'adresse actuelle pour les données d'une colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *column*  
 Indique le numéro de la colonne pour laquelle l'adresse est spécifiée. Les colonnes sont numérotées, en commençant par 1.  
  
 *data*  
 Pointeur pour les données d'une colonne. La mémoire allouée pour *data* ne doit pas être libérée tant que les données de la colonne ne sont pas remplacées par un autre appel à **srv_setcoldata**ou tant que **srv_senddone** n'est pas appelé.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Chaque colonne de la ligne doit être au préalable définie avec **srv_describe**. Les adresses des données de colonne sont définies initialement avec **srv_describe**. En cas de modification de l'adresse des données de colonne, **srv_setcoldata** doit être appelé pour spécifier la nouvelle adresse des données et **srv_setcoldata** doit être appelé séparément pour chaque colonne modifiée.  
  
 Pour représenter des données Null, attribuez la valeur 0 à la longueur de la colonne avec **srv_setcollen**. L'adresse des données est alors ignorée.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_describe &#40;API de procédure stockée étendue&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
