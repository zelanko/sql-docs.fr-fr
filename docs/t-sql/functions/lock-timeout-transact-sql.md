---
title: '@@LOCK_TIMEOUT (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LOCK_TIMEOUT'
- '@@LOCK_TIMEOUT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- '@@LOCK_TIMEOUT function'
- current lock time-out setting
- locking [SQL Server], time-outs
ms.assetid: 6bf8bf97-60b8-40c1-b89d-8f5a00bcae2e
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15ee9c5789ea6f1c7bbad6fc8caeabab14f3df4f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="locktimeout-transact-sql"></a>@@LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie le paramètre de délai d'attente de verrouillage en cours, en millisecondes, pour la session actuelle.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
@@LOCK_TIMEOUT  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes  
 SET LOCK_TIMEOUT permet à une application de définir le délai maximal pendant lequel une instruction doit attendre une ressource bloquée. Si l'attente d'une instruction dépasse la valeur du paramètre LOCK_TIMEOUT, l'instruction bloquée est automatiquement annulée, et un message d'erreur est renvoyé à l'application.  
  
 @@LOCK_TIMEOUT renvoie la valeur -1 si SET LOCK_TIMEOUT n’a pas encore été exécuté dans la session active.  
  
## <a name="examples"></a>Exemples  
 Cet exemple affiche l'ensemble de résultats lorsqu'une valeur LOCK_TIMEOUT n'a pas été définie.  
  
```  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
Lock Timeout  
------------  
-1  
```  
  
 Cet exemple fixe LOCK_TIMEOUT à 1 800 millisecondes, puis appelle@LOCK_TIMEOUT.  
  
```  
SET LOCK_TIMEOUT 1800;  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
Lock Timeout  
------------  
1800          
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de configuration &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LOCK_TIMEOUT &#40; Transact-SQL &#41;](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  
