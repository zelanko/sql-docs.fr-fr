---
title: srv_setcollen (API de procédure stockée étendue) | Microsoft Docs
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
- srv_setcollen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cc059a5cc2b27213915491cebc87f9d16b549a0f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141293"
---
# <a name="srvsetcollen-extended-stored-procedure-api"></a>srv_setcollen (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Spécifie la longueur de données actuelle, en octets, d'une colonne de longueur variable ou d'une colonne qui autorise des valeurs NULL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *column*  
 Indique le numéro de la colonne pour laquelle la longueur des données est spécifiée. Les colonnes sont numérotées, en commençant par 1.  
  
 *len*  
 Indique la longueur, en octets, des données de la colonne. Une longueur de 0 signifie que les données de la colonne sont Null.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Chaque colonne de la ligne doit être au préalable définie avec **srv_describe**. La longueur des données de la colonne est définie par le dernier appel à **srv_describe** ou **srv_setcollen**. En cas de modification des données de longueur variable (données se terminant par le caractère Null) pour une ligne, vous devez utiliser **srv_setcollen** pour définir la nouvelle longueur avant d’appeler **srv_sendrow**. Pour une colonne qui autorise des valeurs Null, **srv_describe** doit être appelé avec un type de données qui autorise des valeurs Null attribué à *desttype* (comme SRVINTN) et des données Null sont spécifiées en appelant **srv_setcollen** avec la valeur 0 attribuée à *len*. Les données de longueur nulle ne peuvent pas être spécifiées à l'aide de l'API de procédure stockée étendue.  
  
 Notez que quand le type de données de la colonne est de longueur variable, *len* n’est pas vérifié. Cette fonction retourne FAIL si elle est appelée pour une colonne de longueur fixe.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_describe &#40;API de procédure stockée étendue&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  