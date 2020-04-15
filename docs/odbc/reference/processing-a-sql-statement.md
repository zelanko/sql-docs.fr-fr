---
title: Traitement d’une déclaration SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349a62034d598c1bfb44b891b91359d5ff184b7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280519"
---
# <a name="processing-a-sql-statement"></a>Traitement d’une instruction SQL
Avant de discuter des techniques d’utilisation de SQL programmatiquement, il est nécessaire de discuter de la façon dont une déclaration SQL est traitée. Les étapes impliquées sont communes aux trois techniques, bien que chaque technique les exécute à des moments différents. L’illustration suivante montre les étapes du traitement d’une déclaration SQL, qui sont discutées tout au long du reste de cette section.  
  
 ![Étapes de traitement d'une instruction SQL](../../odbc/reference/media/pr01.gif "pr01 (pr01)")  
  
 Pour traiter une déclaration SQL, un DBMS effectue les cinq étapes suivantes :  
  
1.  Le DBMS analyse d’abord la déclaration SQL. Il décompose l’énoncé en mots individuels, appelés jetons, s’assure que la déclaration a un verbe valide et des clauses valides, et ainsi de suite. Des erreurs de syntaxe et des fautes d’orthographe peuvent être détectées dans cette étape.  
  
2.  Le DBMS valide l’énoncé. Il vérifie la déclaration contre le catalogue du système. Est-ce que tous les tableaux nommés dans la déclaration existent dans la base de données? Toutes les colonnes existent-elles et les noms de colonnes sont-ils sans ambiguïté ? L’utilisateur a-t-il les privilèges requis pour exécuter l’instruction ? Certaines erreurs sémantiques peuvent être détectées dans cette étape.  
  
3.  Le DBMS génère un plan d’accès pour l’énoncé. Le plan d’accès est une représentation binaire des étapes qui sont nécessaires pour effectuer la déclaration; c’est l’équivalent DBMS du code exécutable.  
  
4.  Le DBMS optimise le plan d’accès. Il explore diverses façons de mettre en œté le plan d’accès. Un index peut-il être utilisé pour accélérer une recherche ? Le DBMS devrait-il d’abord appliquer une condition de recherche au tableau A, puis l’adhérer au tableau B, ou devrait-il commencer par la jointure et utiliser l’état de recherche par la suite? Une recherche séquentielle à travers une table peut-elle être évitée ou réduite à un sous-ensemble de la table? Après avoir exploré les alternatives, le DBMS choisit l’un d’eux.  
  
5.  Le DBMS exécute l’énoncé en exécutant le plan d’accès.  
  
 Les étapes utilisées pour traiter une déclaration SQL varient en quantité d’accès à la base de données dont elles ont besoin et le temps qu’elles prennent. Le parsing d’une déclaration SQL ne nécessite pas l’accès à la base de données et peut être fait très rapidement. L’optimisation, d’autre part, est un processus très CPU-intensif et nécessite l’accès au catalogue du système. Pour une requête complexe et multitable, l’optimiseur peut explorer des milliers de façons différentes d’effectuer la même requête. Cependant, le coût de l’exécution de la requête de manière inefficace est généralement si élevé que le temps passé dans l’optimisation est plus que repris dans la vitesse d’exécution accrue de requête. Ceci est encore plus important si le même plan d’accès optimisé peut être utilisé encore et encore pour effectuer des requêtes répétitives.
