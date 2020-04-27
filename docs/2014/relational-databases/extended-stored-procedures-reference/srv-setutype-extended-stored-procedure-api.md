---
title: srv_setutype (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2439b19c4550d07b8d50a0bed6d72b603b1601a8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62745788"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a>srv_setutype (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Définit le type de données défini par l'utilisateur pour la colonne d'une ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *chronique*  
 Indique quelle est la colonne à définir. Les colonnes sont numérotées, en commençant par 1.  
  
 *user_type*  
 Spécifie le code de type de données défini par l'utilisateur.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL. Retourne FAIL si la colonne n'existe pas.  
  
## <a name="remarks"></a>Notes  
 Une colonne a deux types de données : son type de données réel et son type de données défini par l'utilisateur. Le type de données défini par l’utilisateur est [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé par pour stocker le type de données défini par l’utilisateur réel de la colonne, le cas échéant, et les informations de description de la colonne, telles que la possibilité de valeur null et la possibilité de mise à jour, pour la colonne.  
  
 La fonction **srv_setutype** peut être appelée chaque fois que *column* a été défini avec **srv_describe** et avant que la dernière ligne n’ait été envoyée.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_describe &#40;API de procédure stockée étendue&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
