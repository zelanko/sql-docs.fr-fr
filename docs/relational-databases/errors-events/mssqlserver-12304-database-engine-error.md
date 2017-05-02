---
title: MSSQLSERVER_12304 | Microsoft Docs
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
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
caps.latest.revision: 4
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 900d97ae3bfb1766884f0201044a9fd4fc255860
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver12304"></a>MSSQLSERVER_12304
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|12304|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|Texte du message|L'utilisation d'un type de table optimisée en mémoire utilisant la propriété IDENTITY avec l'une de ses colonnes n'est pas prise en charge lors de l'utilisation du type hors du contexte de la procédure stockée compilée en mode natif.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
N'utilisez pas un type de table optimisée en mémoire qui utilise la propriété d'identité avec l'une de ses colonnes.  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

