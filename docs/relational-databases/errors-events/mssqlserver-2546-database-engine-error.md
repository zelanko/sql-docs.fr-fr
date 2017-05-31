---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 55278a84ecc717b9668af1b99bd2cf8ec3d5de16
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2546|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_INDEX_MARKED_DISABLED|  
|Texte du message|L'index 'INDEX_NAME' de la table 'OBJECT_NAME' est marqué comme étant désactivé. Reconstruisez l'index pour qu'il soit en ligne.|  
  
## <a name="explanation"></a>Explication  
L'index spécifié est marqué comme étant hors connexion ou il est désactivé. Cet index ne peut donc pas être vérifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Reconstruisez l'index en utilisant ALTER INDEX.  
  
## <a name="see-also"></a>Voir aussi  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[Réorganiser et reconstruire des index](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  

