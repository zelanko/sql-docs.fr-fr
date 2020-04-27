---
title: Rechercher des documents similaires ou connexes avec la recherche sémantique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b2e30534fb5e0232ff2046e30e2e14075dfb807
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011318"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>Rechercher des documents similaires ou connexes avec la recherche sémantique
  Explique comment rechercher des valeurs textuelles ou des documents similaires ou connexes et donne des informations sur leur similitude, dans des colonnes configurées pour l'indexation sémantique statistique.  
  
##  <a name="finding-similar-or-related-documents"></a><a name="BasicsQuerySimilar"></a>Recherche de documents similaires ou connexes  
  
###  <a name="how-to-find-similar-or-related-documents-with-semanticsimilaritytable"></a><a name="HowToQuerySimilar"></a>Comment : Rechercher des documents similaires ou connexes avec SEMANTICSIMILARITYTABLE  
 Pour identifier des documents similaires ou connexes dans une colonne spécifique, interrogez la fonction [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
 **SEMANTICSIMILARITYTABLE** retourne une table de zéro, une ou plusieurs lignes pour les colonnes dont le contenu dans la colonne spécifiée est sémantiquement similaire au document spécifié. Cette fonction d'ensemble de lignes peut être référencée dans la clause FROM d'une instruction SELECT comme un nom de table classique.  
  
 Vous ne pouvez pas rechercher des documents similaires dans plusieurs colonnes. La fonction **SEMANTICSIMILARITYTABLE** récupère uniquement des résultats provenant de la même colonne que la colonne source, qui est identifiée par l’argument **source_key** .  
  
 Pour plus d’informations sur les paramètres requis par la fonction **SEMANTICSIMILARITYTABLE** et sur la table de résultats qu’elle retourne, consultez [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
> [!IMPORTANT]  
>  L'indexation sémantique et de texte intégral doit être activée pour les colonnes que vous ciblez.  
  
###  <a name="example-find-the-top-documents-that-are-similar-to-another-document"></a><a name="HowToIdentifySimilar"></a>Exemple : Rechercher les documents de niveau supérieur qui sont similaires à un autre document  
 L’exemple suivant récupère les 10 premiers candidats similaires au candidat spécifié par *@CandidateID* dans la table HumanResources. JobCandidate de l’exemple de base de données AdventureWorks2012.  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="finding-information-about-how-documents-are-similar-or-related"></a><a name="BasicsQuerySimilarity"></a>Recherche d’informations sur la façon dont les documents sont similaires ou connexes  
  
###  <a name="how-to-find-information-about-how-documents-are-similar-or-related-with-semanticsimilaritydetailstable"></a><a name="HowToQuerySimilarity"></a>Comment : Rechercher des informations sur la façon dont les documents sont similaires ou connexes avec SEMANTICSIMILARITYDETAILSTABLE  
 Pour obtenir des informations sur les expressions clés qui rendent des documents similaires ou connexes, vous pouvez interroger la fonction [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
 **SEMANTICSIMILARITYDETAILSTABLE** retourne une table de zéro, une ou plusieurs lignes d’expressions clés communes dans deux documents (un document source et un document mis en correspondance) dont le contenu est similaire sémantiquement. Cette fonction d'ensemble de lignes peut être référencée dans la clause FROM d'une instruction SELECT comme un nom de table classique.  
  
 Pour plus d’informations sur les paramètres requis par la fonction **SEMANTICSIMILARITYDETAILSTABLE**, ainsi que sur la table de résultats qu’elle retourne, consultez [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
> [!IMPORTANT]  
>  L'indexation sémantique et de texte intégral doit être activée pour les colonnes que vous ciblez.  
  
###  <a name="example-find-the-top-key-phrases-that-are-similar-between-documents"></a><a name="HowToSimilarPhrases"></a>Exemple : Rechercher les expressions clés de niveau supérieur qui sont similaires entre les documents  
 L'exemple suivant récupère les 5 expressions clés qui ont le score de similarité le plus élevé parmi les candidats spécifiés dans la table **HumanResources.JobCandidate** de l'exemple de base de données AdventureWorks2012.  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
