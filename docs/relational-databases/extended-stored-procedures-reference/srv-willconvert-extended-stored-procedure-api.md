---
title: srv_willconvert (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_willconvert
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e8690ea8ea86417bcf32a3688d38b7eaaa23cf34
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51031616"
---
# <a name="srvwillconvert-extended-stored-procedure-api"></a>srv_willconvert (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Détermine si une conversion de type de données spécifique est disponible au sein de la bibliothèque ODS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srctype*  
 Indique le type de données des données à convertir. Ce paramètre peut être n'importe lequel des types de données des API de procédure stockée étendue.  
  
 *desttype*  
 Indique le type de données vers lequel les données sources sont converties. Ce paramètre peut être n'importe lequel des types de données des API de procédure stockée étendue.  
  
## <a name="returns"></a>Valeur renvoyée  
 TRUE si la conversion de type de données est prise en charge ; FALSE, dans le cas contraire.  
  
## <a name="remarks"></a>Notes   
 Pour obtenir une description de chaque type de données, consultez [Types de données &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a> Voir aussi  
 [srv_convert &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-convert-extended-stored-procedure-api.md)  
  
  
