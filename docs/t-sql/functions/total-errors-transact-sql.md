---
title: '@@TOTAL_ERRORS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_ERRORS'
- '@@TOTAL_ERRORS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@TOTAL_ERRORS function'
- total errors [SQL Server]
- errors [SQL Server], read/write
- number of disk read/write errors
- disks [SQL Server], errors
- write errors [SQL Server]
- read/write errors
ms.assetid: 09e62428-ee0e-4ef5-b969-da9d255f1199
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a07518edbdfce618fa8bfcff15a49df70f029ee3
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68098962"
---
# <a name="x40x40total_errors-transact-sql"></a>&#x40;&#x40;TOTAL_ERRORS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le nombre d’erreurs d’écriture sur le disque rencontrées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis le dernier démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@TOTAL_ERRORS  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes  
 Cette fonction ne comptabilise pas toutes les erreurs d'écriture rencontrées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les erreurs d'écriture récupérables et occasionnelles sont gérées par le serveur lui-même et ne sont pas considérées comme des erreurs. Pour afficher un rapport contenant plusieurs statistiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], notamment le nombre total d’erreurs, exécutez **sp_monitor**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple affiche le nombre d'erreurs rencontrées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la date et à l'heure du jour.  
  
```  
SELECT @@TOTAL_ERRORS AS 'Errors', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Errors      As of                   
----------- ----------------------  
0           3/28/2003 12:32:11 PM   
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Fonctions statistiques système &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
