---
title: srv_senddone (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6a7ed324a068b81c2226a0b520d403f688a6ede7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044228"
---
# <a name="srvsenddone-extended-stored-procedure-api"></a>srv_senddone (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Envoie un message d'achèvement de résultat au client.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la demande de langue). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *status*  
 Champ de deux octets pour différents indicateurs *status* . Vous pouvez définir plusieurs indicateurs à l'aide des opérateurs logiques AND et OR avec des valeurs d'indicateur *status* . Le tableau suivant répertorie les indicateurs *status* possibles.  
  
|Indicateur d'état|Description|  
|-----------------|-----------------|  
|SRV_DONE_COUNT|Le paramètre *count* contient un nombre valide.|  
|SRV_DONE_ERROR|La commande cliente actuelle a reçu une erreur.|  
  
 *info*  
 Champ réservé de deux octets. Attribuez à ce champ la valeur 0.  
  
 *nombre*  
 Champ de quatre octets utilisé pour indiquer un nombre pour le jeu de résultats actuel. Si l'indicateur SRV_DONE_COUNT est défini dans le champ *status* , *count* contient un nombre valide.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL  
  
## <a name="remarks"></a>Notes  
 Une requête du client peut faire en sorte que le serveur exécute plusieurs commandes et retourne plusieurs jeux de résultats. Pour chaque jeu de résultats, **srv_senddone** doit retourner un message d'achèvement de résultat au client.  
  
 Le champ *count* indique le nombre de lignes affectées par une commande. Si le champ *count* contient un nombre, l'indicateur SRV_DONE_COUNT doit être défini dans le champ *status* . Ce paramètre permet au client d'effectuer la distinction entre une valeur *count* de 0 et un champ *count* inutilisé.  
  
 N'appelez pas **srv_senddone** à partir du gestionnaire SRV_CONNECT.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  