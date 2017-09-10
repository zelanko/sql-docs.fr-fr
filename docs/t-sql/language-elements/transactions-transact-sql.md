---
title: Transactions (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8660d0ac8d6205a94fdab24f41e41bac40a8671e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-transact-sql"></a>Transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Une transaction est une unité de travail. Lorsqu'une transaction aboutit, toutes les modifications de données apportées lors de la transaction sont validées et intégrées de façon permanente à la base de données. Si une transaction rencontre des erreurs et doit être annulée ou restaurée, toutes les modifications de données sont supprimées.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les modes de transaction disponibles sont les suivants.  
  
 Transactions en mode de validation automatique  
 Chaque instruction individuelle est une transaction.  
  
 Transactions explicites  
 Chaque transaction est explicitement lancée par l'instruction BEGIN TRANSACTION et explicitement terminée par une instruction COMMIT ou ROLLBACK.  
  
 Transactions implicites  
 Une nouvelle transaction est implicitement lancée lorsque la transaction précédente est terminée, mais chaque transaction est explicitement terminée par une instruction COMMIT ou ROLLBACK.  
  
 Transaction dont l'étendue est définie par lot  
 Uniquement applicable aux ensembles de résultats MARS (Multiple Active Result Sets), une transaction [!INCLUDE[tsql](../../includes/tsql-md.md)] explicite ou implicite qui démarre sous une session MARS devient une transaction dont l'étendue est définie par traitement. Une transaction dont l'étendue est définie par traitement qui n'est pas validée ou restaurée à la fin du traitement est automatiquement restaurée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre les instructions de transaction suivantes.  
  
|||  
|-|-|  
|[BEGIN DISTRIBUTED TRANSACTION](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[DÉBUT DE LA TRANSACTION](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[TRAVAIL DE RESTAURATION](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[VALIDATION DE TRANSACTION](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[ENREGISTRER DES TRANSACTIONS](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[VALIDEZ LE TRAVAIL](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
