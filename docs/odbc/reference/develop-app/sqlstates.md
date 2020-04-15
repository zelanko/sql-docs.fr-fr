---
title: SQLSTATES - France Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be4bca929b8d48c301c6e71917503387004a6ec5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299726"
---
# <a name="sqlstates"></a>Codes SQLSTATE
Les SQLSTATEs fournissent des renseignements détaillés sur la cause d’un avertissement ou d’une erreur. Les SQLSTATEs de ce manuel sont basés sur ceux trouvés dans la spécification CLI ISO/IEF, bien que les SQLSTATes qui commencent par le GI sont spécifiques à ODBC.  
  
 Contrairement aux codes de retour, les SQLSTATes dans ce manuel sont des lignes directrices, et les conducteurs ne sont pas tenus de les retourner. Par conséquent, alors que les conducteurs doivent retourner le SQLSTATE approprié pour toute erreur ou avertissement qu’ils sont capables de détecter, les applications ne devraient pas compter sur ce qui se produit toujours. Les raisons de cette situation sont doubles :  
  
-   **Incomplétude** Bien que ce manuel énumère un grand nombre d’erreurs et d’avertissements et les causes possibles de ces erreurs et avertissements, il n’est pas complet et ne sera probablement jamais; les implémentations des pilotes varient tout simplement trop. Tout conducteur donné ne retournera probablement pas toutes les SQLSTATes énumérées dans ce manuel et pourrait retourner SQLSTATes non répertoriés dans ce manuel.  
  
-   **Complexité** Certains moteurs de base de données - en particulier les moteurs de base de données relationnels - renvoient littéralement des milliers d’erreurs et d’avertissements. Il est peu probable que les conducteurs de ces moteurs cartographient toutes ces erreurs et avertissements aux SQLSTATEs en raison de l’effort en cause, de l’inexactitude des cartes, de la grande taille du code résultant et de la faible valeur du code résultant, qui renvoie souvent des erreurs de programmation qui ne devraient jamais être rencontrées au moment de l’exécution. Par conséquent, les conducteurs doivent cartographier autant d’erreurs et d’avertissements que cela semble raisonnable et être sûr de cartographier les erreurs et les avertissements sur la logique d’application sur laquelle la logique d’application pourrait être basée, comme SQLSTATE 01004 (Données tronquées).  
  
 Étant donné que les SQLSTATEs ne sont pas retournés de façon fiable, la plupart des applications les affichent simplement à l’utilisateur avec leur message diagnostique associé, qui est souvent adapté à l’erreur ou à l’avertissement spécifique qui s’est produit, et au code d’erreur natif. Il ya rarement une perte de fonctionnalité dans ce faisant, parce que les applications ne peuvent pas base logique de programmation sur la plupart des SQLSTATes de toute façon. Supposons, par exemple, **que SQLExecDirect** retourne SQLSTATE 42000 (erreur syntaxe ou violation d’accès). Si la déclaration SQL qui a causé cette erreur est codée par code dur ou construite par l’application, il s’agit d’une erreur de programmation et le code doit être corrigé. Si la déclaration SQL est saisie par l’utilisateur, il s’agit d’une erreur de l’utilisateur et l’application a fait tout ce qui est possible en informant l’utilisateur du problème.  
  
 Lorsque les applications font la logique de programmation de base sur SQLSTATEs, ils doivent être préparés pour que le SQLSTATE ne soit pas retourné ou pour qu’un autre SQLSTATE soit retourné. Exactement quels SQLSTATEs sont retournés de façon fiable peuvent être basés uniquement sur l’expérience avec de nombreux conducteurs. Toutefois, une directive générale est que les SQLSTATEs pour les erreurs qui se produisent chez le conducteur ou le gestionnaire de conducteur, par opposition à la source de données, sont plus susceptibles d’être retournés de façon fiable. Par exemple, la plupart des conducteurs retournent probablement SQLSTATE HYC00 (fonction facultative non mise en œuvre), tandis que moins de conducteurs retournent probablement SQLSTATE 42021 (Colonne existe déjà).  
  
 Les SQLSTATEs suivants indiquent des erreurs ou des avertissements en temps de course et sont de bons candidats sur lesquels fonder la logique de programmation. Cependant, il n’y a aucune garantie que tous les conducteurs les retournent.  
  
-   01004 (Données tronquées)  
  
-   01S02 (Valeur d’option modifiée)  
  
-   HY008 (Opération annulée)  
  
-   HYC00 (fonction facultative non implémentée)  
  
-   HYT00 (Expiration du délai)  
  
 SQLSTATE HYC00 (fonction facultative non mise en œuvre) est particulièrement importante parce que c’est la seule façon pour une application de déterminer si un conducteur prend en charge un relevé ou un attribut de connexion particulier.  
  
 Pour une liste complète des SQLSTATEs et quelles fonctions les retournent, voir [Annexe A: ODBC Error Codes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Pour une explication détaillée des conditions dans lesquelles chaque fonction peut renvoyer un SQLSTATE particulier, voir cette fonction.
