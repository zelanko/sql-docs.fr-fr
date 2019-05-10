---
title: Recherche en texte intégral et les fonctions de recherche sémantique (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- semantic search [SQL Server], system functions
ms.assetid: a61a3694-7604-4583-962e-fc30f771c6fa
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1d8cccc6f36996808693e007e87ff1de7edfdd4a
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105102"
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>Fonctions de recherche en texte intégral et de recherche sémantique (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette section décrit les fonctions système relatives à la recherche en texte intégral et à la recherche sémantique.  
  
## <a name="full-text-search-functions"></a>Fonctions de recherche en texte intégral  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)  
 Retourne une table composée de zéros, d'une ou de plusieurs ligne(s) pour les colonnes contenant des correspondances exactes ou floues (moins précises) pour des mots simples ou des expressions, la proximité de mots à une certaine distance les uns des autres ou des correspondances pondérées.  
  
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 Retourne une table de zéro, une ou plusieurs lignes pour les colonnes contenant des valeurs qui correspondent à la signification et pas seulement aux mots exacts, du texte spécifié *freetext_string*.  
  
## <a name="semantic-search-functions"></a>Fonctions de recherche sémantique  
 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 Retourne une table de zéro, une ou plusieurs lignes pour les expressions clés associées aux colonnes de la table spécifiée.  
  
 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 Retourne une table de zéro, une ou plusieurs lignes d'expressions clés communes à deux documents (document source et document mis en correspondance) dont le contenu est similaire d'un point de vue sémantique.  
  
 [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 Retourne une table de zéro, une ou plusieurs lignes pour les colonnes dont le contenu est sémantiquement similaire à un document spécifié.  
  
  
