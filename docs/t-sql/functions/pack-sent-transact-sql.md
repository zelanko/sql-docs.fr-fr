---
title: '@@PACK_SENT (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@PACK_SENT'
- '@@PACK_SENT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- number of output packets written
- '@@PACK_SENT function'
- packets [SQL Server], ouput
- networking [SQL Server], output packets
- connections [SQL Server], packets
- output packets written to network [SQL Server]
ms.assetid: 8a322162-24c9-48e9-bfa4-c060e4e11dba
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 212f5ad5bbe56ab994ee50baba81b8a650bf0a93
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40packsent-transact-sql"></a>& #x 40 ; & #x 40 ; PACK_SENT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le nombre de paquets en sortie écrits sur le réseau par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis son dernier démarrage.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@PACK_SENT  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes  
 Pour afficher un rapport contenant plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des statistiques, notamment les paquets envoyés et reçus, exécutez **sp_monitor**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant illustre l’utilisation de `@@PACK_SENT`.  
  
```  
SELECT @@PACK_SENT AS 'Pack Sent';  
```  
  
 Un exemple d'ensemble de résultats est présenté ci-dessous.  
  
```  
Pack Sent  
-----------  
291  
```  
  
## <a name="see-also"></a>Voir aussi  
 [@@PACK_RECEIVED &#40;Transact-SQL&#41;](../../t-sql/functions/pack-received-transact-sql.md)   
 [sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Fonctions statistiques système &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

