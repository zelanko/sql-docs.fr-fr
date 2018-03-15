---
title: NULL et UNKNOWN (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c26004fdfa5f2607235ffe7dddb7826a77f38b31
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="null-and-unknown-transact-sql"></a>NULL et UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL indique que la valeur est inconnue. Une valeur NULL est différente d’une valeur vide ou égale à zéro. Deux valeurs NULL ne sont pas égales. Les comparaisons de deux valeurs NULL, ou d’une valeur NULL et d’une autre valeur, renvoient le message « inconnu » car la valeur de chaque NULL est inconnue.  
  
 Les valeurs NULL indiquent généralement des données inconnues, non applicables ou à ajouter ultérieurement. Le montant moyen, par exemple, ne peut pas être connu à l'instant où le client effectue une commande.  
  
 Notez les points suivants sur les valeurs Null :  
  
-   Pour tester des valeurs NULL dans une requête, utilisez IS NULL ou IS NOT NULL dans la clause WHERE.  
  
-   Les valeurs Null peuvent être insérées dans une colonne en spécifiant explicitement NULL dans une instruction INSERT ou UPDATE ou en laissant une colonne en dehors d’une instruction INSERT.  
  
-   Les valeurs Null ne peuvent pas servir d’informations permettant de distinguer entre les lignes dans une table, comme des clés primaires, ni d’informations permettant de distribuer des lignes, comme des clés de distribution.  
  
 Lorsque des valeurs NULL sont présentes dans les données, les opérateurs logiques et les opérateurs de comparaison peuvent renvoyer la valeur UNKNOWN au lieu de TRUE ou de FALSE. Cette logique tri-valuée nécessaire est source de nombreuses erreurs dans les applications. Les opérateurs logiques dans une expression booléenne qui inclut des valeurs UNKNOWN renvoient UNKNOWN sauf si le résultat de l’opérateur ne dépend pas de l’expression UNKNOWN. Ces tableaux donnent des exemples de ce comportement.  
  
 Le tableau suivant présente les résultats de l’application d’un opérateur AND à deux expressions booléennes quand une seule expression retourne UNKNOWN.  
  
|Expression 1|Expression 2|Résultats|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 Le tableau suivant présente les résultats de l’application d’un opérateur OR à deux expressions booléennes quand une seule expression retourne UNKNOWN.  
  
|Expression 1|Expression 2|Résultats|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a> Voir aussi  
 [AND &#40;Transact-SQL&#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [OR &#40;Transact-SQL&#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [NOT &#40;Transact-SQL&#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [IS NULL &#40;Transact-SQL&#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
