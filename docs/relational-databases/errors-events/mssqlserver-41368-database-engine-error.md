---
description: MSSQLSERVER_41368
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
robots: noindex,nofollow
ms.openlocfilehash: b3137e68acc9878af795a36015f6f6fe794a2156
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476017"
---
# <a name="mssqlserver_41368"></a>MSSQLSERVER_41368
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41368|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Texte du message|L'accès aux tables optimisées en mémoire selon le niveau d'isolement READ COMMITTED est pris en charge uniquement pour les transactions validées automatiquement. Cela n'est pas pris en charge pour les transactions explicites ou implicites. Spécifiez un niveau d'isolement pris en charge pour la table optimisée en mémoire à l'aide d'un indicateur de table, comme WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Explication  
L'accès aux tables optimisées en mémoire selon le niveau d'isolement READ COMMITTED est pris en charge uniquement pour les transactions validées automatiquement. Pour plus d’informations, consultez [Transactions avec des tables et des procédures en mémoire](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md).  
  
Lors de l'accès à une table optimisée en mémoire à partir d'une transaction explicite démarrée par BEGIN TRANSACTION, ou à partir d'une transaction implicite, si IMPLICIT_TRANSACTIONS a la valeur ON, le niveau d'isolement READ COMMITTED n'est pas pris en charge.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Lors de l'accès à une table optimisée en mémoire à partir d'une transaction READ COMMITTED implicite ou explicite, utilisez SNAPSHOT pour accéder à la table. Pour cela, utilisez l’indicateur de table WITH (SNAPSHOT) (pour plus d’informations, consultez [Transactions avec des tables et des procédures en mémoire](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)) ou affectez la valeur ON à l’option de base de données MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT (pour plus d’informations, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql.md)).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
