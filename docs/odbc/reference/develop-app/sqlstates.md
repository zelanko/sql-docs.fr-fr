---
title: SQLSTATE | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 3ad31d9fd07e0b9f7bdf633f8ed546331880787c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527730"
---
# <a name="sqlstates"></a>Codes SQLSTATE
SQLSTATE fournit des informations détaillées sur la cause d’un avertissement ou d’erreur. Le SQLSTATE dans ce manuel est basées sur celles que l'on trouve dans la spécification ISO/IEF CLI, bien que ces SQLSTATE qui commencent par messagerie instantanée est spécifiques à ODBC.  
  
 Contrairement aux codes de retour, le SQLSTATE dans ce manuel est des recommandations et pilotes n’êtes pas obligées de les retourner. Par conséquent, tandis que les pilotes doivent retourner la valeur SQLSTATE appropriée pour toute erreur ou avertissement qu’ils sont capables de détecter, les applications ne doivent pas compter sur cette toujours en cours. Les raisons de cette situation sont deux raisons :  
  
-   **Non-exhaustivité** bien que ce manuel répertorie un grand nombre d’erreurs et avertissements et les causes possibles pour ces erreurs et les avertissements, il n’est pas terminée et que vous sera probablement jamais ; les implémentations de pilote simplement varient trop. N’importe quel pilote donné ne renvoie tous les SQLSTATE répertoriées dans ce manuel et peuvent retourner SQLSTATE non répertoriés dans ce manuel.  
  
-   **Complexité** certains moteurs de base de données - moteurs de base de données relationnelle particulièrement - retournent littéralement des milliers d’erreurs et avertissements. Les pilotes de ces moteurs sont peu susceptibles de mapper l’ensemble de ces erreurs et avertissements à SQLSTATE en raison de l’effort impliqué, l’inexactness des mappages, la grande taille du code qui en résulte et la valeur faible du code qui en résulte, qui renvoie souvent de programmation erreurs qui ne doivent jamais se produire au moment de l’exécution. Par conséquent, les pilotes doivent être mappés autant d’erreurs et avertissements comme semble raisonnable et veillez à mapper ces erreurs et des avertissements dans la logique d’application peuvent être basées, par exemple SQLSTATE 01004 (données tronquées).  
  
 Étant donné que SQLSTATE n’est pas retournés fiable, la plupart des applications affiche simplement les à l’utilisateur, ainsi que leur message de diagnostic associé, qui est souvent adaptée à l’erreur spécifique ou d’avertissement qui s’est produite et le code d’erreur natif. Il est rarement aucune perte de fonctionnalité à effectuer, étant donné que les applications ne peuvent pas de base logique de programmation sur la plupart des SQLSTATE quand même. Par exemple, supposons que **SQLExecDirect** retourne SQLSTATE 42000 (syntaxe ou violation d’accès). Si l’instruction SQL qui a provoqué cette erreur est codé en dur ou générée par l’application, il s’agit d’une erreur de programmation et le code doit être corrigé. Si l’instruction SQL est entrée par l’utilisateur, il s’agit d’une erreur de l’utilisateur et l’application a fait tout ce qui est possible en informant l’utilisateur du problème.  
  
 Lorsque les applications sans se baser logique de programmation sur SQLSTATE, ils devraient être préparées pour la variable SQLSTATE ne pas à retourner ou pour une valeur SQLSTATE sous différents à retourner. Qui SQLSTATE est retournés de façon fiable peuvent reposer uniquement sur l’expérience avec nombreux pilotes. Toutefois, la règle générale est que SQLSTATE pour les erreurs qui se produisent dans le pilote ou le Gestionnaire de pilotes, par opposition à la source de données est plus susceptibles d’être renvoyé de manière fiable. Par exemple, la plupart des pilotes retournent probablement SQLSTATE HYC00 (fonctionnalité facultative non implémentée), tandis que les pilotes moins retournent probablement SQLSTATE 42021 (colonne existe déjà).  
  
 Le SQLSTATE suivants indique les erreurs d’exécution ou des avertissements et est de bons candidats sur lequel baser la logique de programmation. Toutefois, il n’existe aucune garantie que tous les pilotes pour les retournent.  
  
-   01004 (données tronquées)  
  
-   01 s 02 (valeur d’Option modifiée)  
  
-   HY008 (opération annulée)  
  
-   HYC00 (fonctionnalité facultative non implémentée)  
  
-   HYT00 (délai d’attente expiré)  
  
 SQLSTATE HYC00 (fonctionnalité facultative non implémentée) est particulièrement importante, car c’est le seul moyen dans lequel une application peut déterminer si un pilote prend en charge un attribut d’instruction ou de connexion particulier.  
  
 Pour obtenir une liste complète de SQLSTATE et les fonctions retournent les, consultez [annexe a : Codes d’erreur ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Pour obtenir une explication détaillée des conditions dans lesquelles chaque fonction peut retourner un SQLSTATE particulier, consultez cette fonction.
