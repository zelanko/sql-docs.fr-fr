---
description: Rechercher des expressions clés dans les documents avec la recherche sémantique
title: Rechercher des expressions clés dans les documents avec la recherche sémantique
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.custom: seo-lt-2019
ms.openlocfilehash: 62a0ba559733c42ddf25b5d40896c4e53bdcf7b7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490546"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>Rechercher des expressions clés dans les documents avec la recherche sémantique
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Explique comment rechercher des expressions clés dans des documents ou des colonnes de texte configurés pour l'indexation sémantique statistique.  

##  <a name="find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a> Rechercher des expressions clés dans des documents avec SEMANTICKEYPHRASETABLE  
 Pour identifier les expressions clés dans des documents spécifiques, ou pour identifier des documents qui contiennent des expressions clés spécifiques, vous pouvez interroger la fonction [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
 SEMANTICKEYPHRASETABLE retourne une table avec zéro, une ou plusieurs lignes pour les expressions clés associées aux colonnes de la table spécifiée. Cette fonction d'ensemble de lignes peut uniquement être référencée dans la clause FROM d'une instruction SELECT comme tout nom de table standard.  
  
> [!NOTE]  
>  Dans cette version, seuls les mots isolés sont indexés pour la recherche sémantique ; les expressions constituées de plusieurs mots (ngrams) ne sont pas indexées. En outre, des formes différentes du même mot sont indexées séparément ; par exemple, « ordinateur » et « ordinateurs » sont indexés séparément.  
  
 Pour plus d’informations sur les paramètres requis par la fonction SEMANTICKEYPHRASETABLE, ainsi que sur la table de résultats qu’elle renvoie, consultez [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
> [!IMPORTANT]  
>  L'indexation sémantique et de texte intégral doit être activée pour les colonnes que vous ciblez.  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a> Exemple 1 : Rechercher les principales expressions clés dans un document spécifique  
 L’exemple suivant extrait les 10 expressions clés de niveau supérieur du document spécifié par la variable @DocumentId dans la colonne Document de la table Production.Document de l’exemple de base de données AdventureWorks. La variable @DocumentId représente une valeur de la colonne clé de l’index de recherche en texte intégral.  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 La fonction **SEMANTICKEYPHRASETABLE** récupère efficacement ces résultats en utilisant une recherche d'index au lieu d'une analyse de table.  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a> Exemple 2 : Rechercher les principaux documents qui contiennent une expression clé spécifique  
 L’exemple suivant récupère les 25 premiers documents qui contiennent l’expression clé « bracket » dans la colonne Document de la table Production.Document de l’exemple de base de données AdventureWorks.  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
