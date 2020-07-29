---
title: '@@PACK_SENT (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@PACK_SENT'
- '@@PACK_SENT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- number of output packets written
- '@@PACK_SENT function'
- packets [SQL Server], output
- networking [SQL Server], output packets
- connections [SQL Server], packets
- output packets written to network [SQL Server]
ms.assetid: 8a322162-24c9-48e9-bfa4-c060e4e11dba
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: da77f0255a67c175537dd6ba5ea6030555f31c68
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87110857"
---
# <a name="x40x40pack_sent-transact-sql"></a>&#x40;&#x40;PACK_SENT (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne le nombre de paquets en sortie écrits sur le réseau par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis son dernier démarrage.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql
@@PACK_SENT  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 **entier**  
  
## <a name="remarks"></a>Notes  
 Pour afficher un rapport contenant plusieurs statistiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], notamment les paquets envoyés et reçus, exécutez **sp_monitor**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant illustre l’utilisation de `@@PACK_SENT`.  
  
```sql
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
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Fonctions statistiques système &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
