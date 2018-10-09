---
title: srv_message_handler (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f671168cdebe2d9dffb738a7f7742a47719e4f16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050447"
---
# <a name="srvmessagehandler-extended-stored-procedure-api"></a>srv_message_handler (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Appelle le gestionnaire de messages de l'API de procédure stockée étendue installée. Cette fonction est habituellement utilisée pour appeler [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’une procédure stockée étendue pour journaliser une erreur (définie par la procédure stockée étendue) dans le fichier du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. Le paramètre *srvproc* contient des informations utilisées pour gérer les communications et les données entre l’application et le client.  
  
 *errornum*  
 Numéro d'erreur défini par la procédure stockée étendue. Ce nombre doit être compris entre 50 001 et 2 147 483 647.  
  
 *severity*  
 Valeur de gravité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standard pour l'erreur. Ce nombre doit être compris entre 0 et 24.  
  
 *state*  
 Valeur d'état [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l'erreur.  
  
 *oserrnum*  
 Numéro d'erreur du système d'exploitation. Cet argument est ignoré.  
  
 *errtext*  
 Description de l’erreur de la procédure stockée étendue *errornum*.  
  
 *errtextlen*  
 Longueur de la chaîne d’erreur de la procédure stockée étendue *errtext*.  
  
 *oserrtext*  
 Description de l’erreur du système d’exploitation *oserrnum*. Cet argument est ignoré.  
  
 *oserrtextlen*  
 Longueur de la chaîne d’erreur du système d’exploitation *oserrtext*.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **srv_message_handler** permet l’intégration d’une procédure stockée étendue aux fonctionnalités centralisées de journalisation des erreurs et de création de rapports de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez établir des alertes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les événements de procédures stockées étendues, et SQL Server Agent surveillera ces conditions d’alerte.  
  
 Si le message d'erreur est plus long, il est tronqué à 412 octets.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
