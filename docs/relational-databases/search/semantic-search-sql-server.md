---
title: "Recherche sémantique (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca60c4ada6bd908d5401784db74a9b8b0c93396b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="semantic-search-sql-server"></a>Recherche sémantique (SQL Server)
La recherche sémantique statistique donne un éclairage sur des documents non structurés stockés dans des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en extrayant et en indexant des *expressions clés*statistiquement pertinentes. Elle utilise ensuite ces expressions clés pour identifier et indexer des *documents similaires ou connexes*.  
  
##  <a name="whatcanido"></a> À quoi sert une recherche sémantique ?  
 La recherche sémantique s'appuie sur la fonctionnalité de recherche en texte intégral existante dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais permet de nouveaux scénarios qui vont au-delà des recherches par mot clé. Tandis que la recherche en texte intégral vous permet d’interroger des *mots* dans un document, la recherche sémantique porte sur la *signification* du document. Les solutions désormais possibles incluent l'extraction automatique de balises, la découverte de contenu connexe et la navigation hiérarchique à travers du contenu similaire. Par exemple, vous pouvez interroger l'index d'expressions clés afin de générer la taxonomie d'une organisation ou d'un corpus de documents. Ou encore interroger l'index de ressemblance de document pour identifier des curriculum vitae qui correspondent à une description de poste.  
  
 Les exemples qui suivent illustrent les fonctions de la recherche sémantique. En même temps, ces exemples illustrent les trois fonctions d’ensemble de lignes Transact-SQL que vous utilisez pour interroger l’index sémantiques et récupérer les résultats sous forme de données structurées.  
  
###  <a name="find1"></a> Find the key phrases in a document  
 La requête suivante obtient les expressions clés qui ont été identifiées dans le document témoin. Elle présente les résultats par ordre décroissant du score qui indique l'importance statistique de chaque expression clé.
 
 Cette requête appelle la fonction [semantickeyphrasetable](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
```tsql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
###  <a name="find2"></a> Find similar or related documents  
 La requête suivante obtient les documents qui ont été identifiés comme similaires ou en rapport avec le document témoin. Elle présente les résultats par ordre décroissant du score qui indique la similarité des deux documents.
 
 Cette requête appelle la fonction [semanticsimilaritytable](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
###  <a name="find3"></a> Rechercher les expressions clés qui rendent des documents similaires ou connexes  
 La requête suivante obtient les expressions clés qui rendent les deux exemples de documents similaires ou liés l’un à l’autre. Elle présente les résultats par ordre décroissant du score qui indique le poids de chaque expression clé.
 
 Cette requête appelle la fonction [semanticsimilaritydetailstable](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
```tsql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
##  <a name="store"></a> Stocker vos documents dans SQL Server  
 Avant de pouvoir indexer les documents avec la recherche sémantique, vous devez les stocker dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La fonctionnalité FileTable dans SQL Server fait des documents et des fichiers non structurés des éléments de premier ordre de la base de données relationnelle. Par conséquent, les développeurs de base de données peuvent manipuler des documents avec des données structurées dans les opérations reposant sur des ensembles Transact-SQL.  
  
 Pour plus d’informations sur la fonctionnalité FileTable, consultez [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md). Pour plus d’informations sur la fonctionnalité FILESTREAM, qui est une autre option pour stocker des documents dans la base de données, consultez [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
##  <a name="reltasks"></a> Related tasks  
 [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)  
 Décrit les conditions préalables à une recherche sémantique statistique, ainsi que la procédure d'installation ou de vérification de ces conditions.  
  
 [Activer la recherche sémantique sur les tables et les colonnes](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)  
 Décrit la procédure d'activation ou de désactivation de l'indexation sémantique statistique sur des colonnes sélectionnées qui contiennent des documents ou du texte.  
  
 [Rechercher des expressions clés dans les documents avec la recherche sémantique](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)  
 Explique comment rechercher des expressions clés dans des documents ou des colonnes de texte configurés pour l'indexation sémantique statistique.  
  
 [Rechercher des documents similaires ou connexes avec la recherche sémantique](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)  
 Explique comment rechercher des valeurs textuelles ou des documents similaires ou connexes et donne des informations sur leur similitude, dans des colonnes configurées pour l'indexation sémantique statistique.  
  
 [Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
 Décrit le processus d'indexation sémantique et les tâches associées à l'analyse et à la gestion des index.  
  
##  <a name="relcontent"></a> Related content  
 [DDL, fonctions, procédures stockées et vues de recherche sémantique](../../relational-databases/search/semantic-search-ddl-functions-stored-procedures-and-views.md)  
 Répertorie les instructions Transact-SQL et les objets de base de données SQL Server ajoutés ou modifiés pour prendre en charge la recherche sémantique statistique.  
  
  

