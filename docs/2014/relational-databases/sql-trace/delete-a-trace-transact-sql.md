---
title: Supprimer une trace (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 57d80824ab0dde301a0b96239636cf0f79ca032c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62714737"
---
# <a name="delete-a-trace-transact-sql"></a>Supprimer une trace (Transact-SQL)
  Cette rubrique explique comment utiliser des procédures stockées pour supprimer une trace.  
  
 Pour obtenir un exemple d’utilisation de procédures stockées de trace, consultez [Créer une trace &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md).  
  
### <a name="to-delete-a-trace"></a>Pour supprimer une trace  
  
1.  Exécutez **sp_trace_setstatus** en spécifiant **@status= 0** pour arrêter la trace.  
  
2.  Exécutez **sp_trace_setstatus** en spécifiant **@status= 2** pour fermer la trace et supprimer du serveur les informations la concernant.  
  
> [!NOTE]  
>  Une trace doit d'abord être arrêtée avant d'être fermée.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Procédures stockées système &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Procédures stockées de SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
