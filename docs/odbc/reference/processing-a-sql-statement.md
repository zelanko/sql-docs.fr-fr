---
title: Traitement d’une instruction SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], processing
- SQL [ODBC], processing statements
- statement processing [ODBC]
- SQL statements [ODBC]
- ODBC [ODBC], SQL
ms.assetid: 96270c4f-2efd-4dc1-a985-ed7fd5658db2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: edf912bf3b8073a05dd900cd00511715020ee0c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045498"
---
# <a name="processing-a-sql-statement"></a>Traitement d’une instruction SQL
Avant d’aborder les techniques pour l’utilisation de SQL par programme, il est nécessaire pour examiner la manière dont est traitée une instruction SQL. Les étapes sont communes à tous les trois techniques, bien que chaque technique leur exécution à des moments différents. L’illustration suivante montre les étapes impliquées dans le traitement d’une instruction SQL, qui sont décrites dans le reste de cette section.  
  
 ![Étapes de traitement d’une instruction SQL](../../odbc/reference/media/pr01.gif "pr01")  
  
 Pour traiter une instruction SQL, un SGBD effectue les cinq étapes suivantes :  
  
1.  Tout d’abord, le SGBD analyse l’instruction SQL. Elle décompose l’instruction en mots individuels, appelés jetons, permet de s’assurer que l’instruction a un verbe valid et clauses valides et ainsi de suite. Les erreurs de syntaxe et les fautes d’orthographe peuvent être détectés dans cette étape.  
  
2.  Le SGBD valide de l’instruction. Il vérifie l’instruction sur le catalogue système. Toutes les tables nommées dans l’instruction existent dans la base de données ? Toutes les colonnes existent et que les noms de colonnes ne sont pas ambigus ? L’utilisateur dispose des privilèges requis pour exécuter l’instruction ? Certaines erreurs sémantiques peuvent être détectés dans cette étape.  
  
3.  Le SGBD génère un plan d’accès pour l’instruction. Le plan d’accès est une représentation binaire des étapes qui sont requises pour exécuter l’instruction ; Il est l’équivalent du SGBD de code exécutable.  
  
4.  Le SGBD optimise le plan d’accès. Il explore les différentes manières d’exécuter le plan d’accès. Un index peut être utilisé pour accélérer une recherche ? Doit le SGBD tout d’abord appliquer une condition de recherche à la Table A et puis joignez-la à la Table B, ou il doit commencer par la jointure et utiliser la condition de recherche par la suite ? Une recherche séquentielle dans une table peut être évitée ou réduite à un sous-ensemble de la table ? Après avoir exploré les alternatives, le SGBD choisit un d’eux.  
  
5.  Le SGBD exécute l’instruction en exécutant le plan d’accès.  
  
 Les étapes qui permettent de traiter une instruction SQL varient quantité d’accès de base de données que dont ils ont besoin et le temps qu’ils prennent. L’analyse d’une instruction SQL ne nécessite pas d’accès à la base de données et peut être très rapide. L’optimisation, est en revanche, un processeur beaucoup de traiter et nécessite un accès pour le catalogue système. Pour une requête complexe, contenant plusieurs tables, l’optimiseur peut Explorer des milliers de différentes façons de procéder à la même requête. Toutefois, le coût de l’exécution de la requête inefficace est généralement très élevé que le temps passé dans l’optimisation est plus de reprendre dans la vitesse d’exécution accrue des requêtes. C’est encore plus important si le même plan d’accès optimisé peut être utilisé plusieurs fois pour effectuer des requêtes répétitives.
