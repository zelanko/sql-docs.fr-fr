---
title: SQLSTATEs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], sqlstates
- SQLSTATE [ODBC]
ms.assetid: f29fff2e-3d09-4a8c-a2f9-2059062cbebf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8213c08e6844003d880129dda4b441a5592bbc86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107343"
---
# <a name="sqlstates"></a>Codes SQLSTATE
SQLSTATEs fournit des informations détaillées sur la cause d’un avertissement ou d’une erreur. Les SQLSTATEs de ce manuel sont basées sur celles figurant dans la spécification de l’interface CLI ISO/IEF, bien que celles qui commencent par la messagerie instantanée soient spécifiques à ODBC.  
  
 Contrairement aux codes de retour, les SQLSTATEs de ce manuel sont des recommandations et les pilotes ne sont pas requis pour les retourner. Par conséquent, alors que les pilotes doivent retourner le SQLSTATE approprié pour toute erreur ou avertissement qu’ils sont en charge de détecter, les applications ne doivent pas compter sur ce qui se produit toujours. Les raisons de cette situation sont double :  
  
-   **Incomplet** Bien que ce manuel répertorie un grand nombre d’erreurs et d’avertissements et les causes possibles de ces erreurs et avertissements, il n’est pas complet et probablement jamais. les implémentations de pilotes font tout simplement trop de choses. Un pilote donné ne retournera probablement pas toutes les SQLSTATE listés dans ce manuel et peut renvoyer des SQLSTATE non listés dans ce manuel.  
  
-   **Complexité** Certains moteurs de base de données, en particulier les moteurs de base de données relationnelle, retournent littéralement des milliers d’erreurs et d’avertissements. Il est peu probable que les pilotes de ces moteurs mappent l’ensemble de ces erreurs et avertissements aux valeurs SQLSTATE en raison de l’effort impliqué, de l’inexactitude des mappages, de la taille importante du code résultant et de la faible valeur du code résultant, qui retourne souvent la programmation erreurs qui ne doivent jamais se produire au moment de l’exécution. Par conséquent, les pilotes doivent mapper autant d’erreurs et d’avertissements que cela semble raisonnable et s’assurer de mapper les erreurs et avertissements sur la logique d’application, tels que SQLSTATE 01004 (données tronquées).  
  
 Étant donné que les SQLSTATEs ne sont pas retournées de manière fiable, la plupart des applications les affichent simplement à l’utilisateur, ainsi que le message de diagnostic qui lui est associé, qui est souvent adapté à l’erreur ou à l’avertissement qui s’est produit, ainsi qu’au code d’erreur natif. Il n’y a rarement aucune perte de fonctionnalité dans ce cas, car les applications ne peuvent quand même pas baser la logique de programmation sur la plupart des SQLSTATEs. Par exemple, supposons que **SQLExecDirect** retourne SQLState 42000 (erreur de syntaxe ou violation d’accès). Si l’instruction SQL à l’origine de cette erreur est codée en dur ou générée par l’application, il s’agit d’une erreur de programmation et le code doit être corrigé. Si l’instruction SQL est entrée par l’utilisateur, il s’agit d’une erreur de l’utilisateur et l’application a effectué tout cela possible en informant l’utilisateur du problème.  
  
 Lorsque les applications effectuent la logique de programmation de base sur les SQLSTATEs, elles doivent être préparées pour que la valeur SQLSTATE ne soit pas retournée ou qu’une valeur SQLSTATE différente soit retournée. Les SQLSTATEs retournés de façon fiable peuvent être basés uniquement sur l’expérience avec de nombreux pilotes. Toutefois, il est généralement recommandé que les SQLSTATEs pour les erreurs qui se produisent dans le pilote ou le gestionnaire de pilotes, par opposition à la source de données, soient plus susceptibles d’être retournées de manière fiable. Par exemple, la plupart des pilotes retournent probablement SQLSTATE HYC00 (fonctionnalité facultative non implémentée), tandis que moins de pilotes retournent SQLSTATE 42021 (la colonne existe déjà).  
  
 Les valeurs SQLSTATE suivantes indiquent des erreurs d’exécution ou des avertissements et sont de bons candidats sur lesquels baser la logique de programmation. Toutefois, il n’y a aucune garantie que tous les pilotes les retournent.  
  
-   01004 (données tronquées)  
  
-   01S02 ne (valeur d’option modifiée)  
  
-   HY008 (opération annulée)  
  
-   HYC00 (fonctionnalité facultative non implémentée)  
  
-   HYT00 (délai d’expiration dépassé)  
  
 SQLSTATE HYC00 (fonctionnalité facultative non implémentée) est particulièrement importante, car il s’agit de la seule façon dont une application peut déterminer si un pilote prend en charge une instruction ou un attribut de connexion particulier.  
  
 Pour obtenir une liste complète des SQLSTATEs et des fonctions qui les retournent, consultez [annexe a : codes d’erreur ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Pour obtenir une explication détaillée des conditions dans lesquelles chaque fonction peut retourner une SQLSTATE particulière, consultez cette fonction.
