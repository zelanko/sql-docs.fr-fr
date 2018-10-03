---
title: '@@PACK_RECEIVED (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@PACK_RECEIVED_TSQL'
- '@@PACK_RECEIVED'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@PACK_RECEIVED function'
- number of packets read
- packets [SQL Server], number read
ms.assetid: 5c0b3d36-bfad-4f0b-abb8-e8f6391b32cd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1ac28510dbe464a1628746b34ecfc94a7c53edc1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752457"
---
# <a name="x40x40packreceived-transact-sql"></a>&#x40;&#x40;PACK_RECEIVED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le nombre de paquets entrants lus du réseau par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis son dernier démarrage.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@PACK_RECEIVED  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes   
 Pour afficher un rapport contenant plusieurs statistiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], notamment les paquets envoyés et reçus, exécutez **sp_monitor**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant illustre l’utilisation de `@@PACK_RECEIVED`.  
  
```  
SELECT @@PACK_RECEIVED AS 'Packets Received';   
```  
  
 Un exemple d'ensemble de résultats est présenté ci-dessous.  
  
```  
Packets Received  
----------------  
128  
```  
  
## <a name="see-also"></a> Voir aussi  
 [@@PACK_SENT](../../t-sql/functions/pack-sent-transact-sql.md)   
 [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Fonctions statistiques système](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
