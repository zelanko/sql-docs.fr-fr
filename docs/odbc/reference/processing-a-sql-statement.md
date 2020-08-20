---
description: Traitement d’une instruction SQL
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4ce614f6dcf4c1fe0ab1e1c806b966b4267e7fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476216"
---
# <a name="processing-a-sql-statement"></a>Traitement d’une instruction SQL
Avant d’aborder les techniques d’utilisation de SQL par programme, il est nécessaire d’aborder la façon dont une instruction SQL est traitée. Les étapes impliquées sont communes aux trois techniques, bien que chaque technique les exécute à des moments différents. L’illustration suivante montre les étapes impliquées dans le traitement d’une instruction SQL, qui sont décrites dans le reste de cette section.  
  
 ![Étapes de traitement d'une instruction SQL](../../odbc/reference/media/pr01.gif "pr01")  
  
 Pour traiter une instruction SQL, un SGBD effectue les cinq étapes suivantes :  
  
1.  Le SGBD analyse d’abord l’instruction SQL. Elle décompose l’instruction en mots individuels, appelés jetons, s’assure que l’instruction possède un verbe valide et des clauses valides, et ainsi de suite. Les erreurs de syntaxe et les fautes d’orthographe peuvent être détectées au cours de cette étape.  
  
2.  Le SGBD valide l’instruction. Il vérifie l’instruction par rapport au catalogue système. Toutes les tables nommées dans l’instruction existent-elles dans la base de données ? Toutes les colonnes existent-elles et les noms de colonnes ne sont-ils pas ambigus ? L’utilisateur dispose-t-il des privilèges requis pour exécuter l’instruction ? Certaines erreurs sémantiques peuvent être détectées lors de cette étape.  
  
3.  Le SGBD génère un plan d’accès pour l’instruction. Le plan d’accès est une représentation binaire des étapes requises pour exécuter l’instruction. Il s’agit de l’équivalent SGBD du code exécutable.  
  
4.  Le SGBD optimise le plan d’accès. Il explore les différentes façons d’effectuer le plan d’accès. Un index peut-il être utilisé pour accélérer une recherche ? Le SGBD doit-il d’abord appliquer une condition de recherche à la table A, puis la joindre à la table B, ou doit-il commencer par la jointure et utiliser la condition de recherche par la suite ? Une recherche séquentielle peut-elle être évitée ou réduite dans un sous-ensemble de la table ? Après avoir exploré les alternatives, le SGBD en choisit un.  
  
5.  Le SGBD exécute l’instruction en exécutant le plan d’accès.  
  
 Les étapes utilisées pour traiter une instruction SQL varient en fonction de la quantité d’accès à la base de données dont elle a besoin et de la durée nécessaire. L’analyse d’une instruction SQL ne requiert pas l’accès à la base de données et peut être effectuée très rapidement. L’optimisation, en revanche, est un processus très gourmand en ressources processeur et nécessitant l’accès au catalogue système. Pour une requête complexe, multitable, l’optimiseur peut explorer des milliers de différentes façons d’effectuer la même requête. Toutefois, le coût de l’exécution de la requête de manière inefficace est généralement élevé que le temps passé dans l’optimisation est plus important que dans l’augmentation de la vitesse d’exécution des requêtes. Cela est encore plus important si le même plan d’accès optimisé peut être utilisé de façon répétée pour exécuter des requêtes répétitives.
