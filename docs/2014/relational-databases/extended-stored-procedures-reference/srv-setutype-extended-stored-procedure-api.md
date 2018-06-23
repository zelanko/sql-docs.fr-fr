---
title: srv_setutype (API de procédure stockée étendue) | Microsoft Docs
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
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47b545b7000dcd0ba500ef56cc844dc32e50f888
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039502"
---
# <a name="srvsetutype-extended-stored-procedure-api"></a>srv_setutype (API de procédure stockée étendue)
    
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
  
 *column*  
 Indique quelle est la colonne à définir. Les colonnes sont numérotées, en commençant par 1.  
  
 *user_type*  
 Spécifie le code de type de données défini par l'utilisateur.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL. Retourne FAIL si la colonne n'existe pas.  
  
## <a name="remarks"></a>Notes  
 Une colonne a deux types de données : son type de données réel et son type de données défini par l'utilisateur. Le type de données défini par l’utilisateur est utilisé par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour stocker le type de données de la colonne défini par l’utilisateur (le cas échéant) et les informations de description de la colonne, telles que la possibilité de valeur NULL et la possibilité de mise à jour pour la colonne.  
  
 La fonction **srv_setutype** peut être appelée chaque fois que *column* a été défini avec **srv_describe** et avant que la dernière ligne n’ait été envoyée.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_describe &#40;API de procédure stockée étendue&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  