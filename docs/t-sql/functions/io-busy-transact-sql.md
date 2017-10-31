---
title: '@@IO_BUSY (Transact-SQL) | Documents Microsoft'
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
- '@@IO_BUSY'
- '@@IO_BUSY_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- I/O [SQL Server], time spent performing operations
- '@@IO_BUSY function'
- output operations [SQL Server]
- input operations [SQL Server]
- time [SQL Server], I/O operations
ms.assetid: 3c26770c-41ae-4e34-8c82-7bef920ffbca
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 48e1bcd5a80825715ad6aed8649dad843e92c1ea
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40iobusy-transact-sql"></a>& #x 40 ; & #x 40 ; IO_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le temps que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a consacré aux opérations d'entrée et de sortie depuis le dernier démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les résultats sont exprimés en incréments de temps processeur (« cycles ») et cumulés pour tous les processeurs, aussi peuvent-ils dépasser le temps réel écoulé. Multiplier par@TIMETICKS à convertir en microsecondes.  
  
> [!NOTE]  
>  Si l’heure est renvoyée dans@CPU_BUSY, ou @@IO_BUSY excède approximativement 49 jours de temps processeur cumulé, vous recevez un avertissement de dépassement de capacité arithmétique. Dans ce cas, la valeur de @@CPU_BUSY, @@IO_BUSY et @@IDLE variables ne sont pas exactes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@IO_BUSY  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes  
 Pour afficher un état contenant plusieurs statistiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez sp_monitor.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le nombre de millisecondes pendant lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a effectué des opérations d'entrée/sortie entre l'heure de début et l'heure actuelle. Pour éviter un dépassement arithmétique lors de la conversion de la valeur en microsecondes, l’exemple convertit une des valeurs pour le **float** type de données.  
  
```  
SELECT @@IO_BUSY*@@TIMETICKS AS 'IO microseconds',   
   GETDATE() AS 'as of';  
```  
  
 Jeu de résultats généralement obtenu :  
  
```  
  
IO microseconds as of                   
--------------- ----------------------  
4552312500      12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.dm_os_sys_info &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Fonctions statistiques système &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

