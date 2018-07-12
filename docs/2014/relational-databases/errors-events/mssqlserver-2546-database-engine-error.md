---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e9497598b38a7bb13b76e6e54d0b0696cb56990e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427078"
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
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [Réorganiser et reconstruire des index](../indexes/indexes.md)  
  
  
