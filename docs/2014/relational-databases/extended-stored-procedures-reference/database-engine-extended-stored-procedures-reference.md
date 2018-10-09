---
title: Guide de référence du programmeur sur les procédures stockées étendues | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b86bc1d1aefc0a1e69beb45451448d7b8a31666a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090219"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a>Étendue des procédures stockées programmeur&#39;s référence
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 L’API de procédure stockée étendue [!INCLUDE[msCoName](../../includes/msconame-md.md)], qui faisait partie des services ODS (Open Data Services), fournit une interface de programmation d’applications serveur pour étendre les fonctionnalités de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'API comprend des fonctions et des macros C et C++ utilisées pour créer des applications.  
  
 Avec l'apparition de nouvelles technologies plus puissantes telles que l'intégration du CLR, les besoins en termes de procédures stockées étendues ont été en grande partie éliminés.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|||  
|-|-|  
|[Types de données](srv-pfield-extended-stored-procedure-api.md)|  
|[srv_alloc](srv-alloc-extended-stored-procedure-api.md)||  
|[srv_convert](srv-pfieldex-extended-stored-procedure-api.md)|  
|[srv_describe](srv-rpcdb-extended-stored-procedure-api.md)|  
|[srv_getbindtoken](srv-rpcname-extended-stored-procedure-api.md)|  
|[srv_got_attention](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[srv_rpcoptions](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[srv_message_handler](srv-rpcowner-extended-stored-procedure-api.md)|  
|[srv_paramdata](srv-rpcparams-extended-stored-procedure-api.md)|  
|[srv_paraminfo](srv-senddone-extended-stored-procedure-api.md)|  
|[srv_paramlen](srv-sendmsg-extended-stored-procedure-api.md)|  
|[srv_parammaxlen](srv-sendrow-extended-stored-procedure-api.md)|  
|[srv_paramname](srv-setcoldata-extended-stored-procedure-api.md)|  
|[srv_paramnumber](srv-setcollen-extended-stored-procedure-api.md)|  
|[srv_paramset](srv-setutype-extended-stored-procedure-api.md)|  
|[srv_paramsetoutput](srv-willconvert-extended-stored-procedure-api.md)|  
|[srv_paramstatus](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
