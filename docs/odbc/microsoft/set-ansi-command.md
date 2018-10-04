---
title: SET ANSI, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5af98bd8f16d7278b932ad89f1c81c58ddb1fb54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612204"
---
# <a name="set-ansi-command"></a>SET ANSI, commande
Détermine comment les comparaisons entre chaînes de longueurs différentes sont effectuées avec l’opérateur dans les commandes de Visual FoxPro SQL =.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 (Par défaut pour le pilote ; la valeur par défaut pour Visual FoxPro est désactivée (OFF).) Remplit pour que la chaîne courte avec les champs vides nécessaires rend la longueur d’une chaîne égale à plus. Les deux chaînes sont ensuite comparé caractère pour caractère pour leurs longueurs entières. Prenez en compte cette comparaison :  
  
```  
'Tommy' = 'Tom'  
```  
  
 Le résultat est False (. F.) si SET ANSI est activé, car lorsque complétée, « Tom » devient 'Tom' et les chaînes « Tom » et 'Tommy' ne correspondent pas caractère pour caractère.  
  
 Le == opérateur utilise cette méthode pour les comparaisons dans les commandes de Visual FoxPro SQL.  
  
 OFF  
 Spécifie que la chaîne plus courte ne soient ne pas complétés par des espaces. Les deux chaînes sont comparées caractère pour caractère jusqu'à la fin de la chaîne plus courte. Prenez en compte cette comparaison :  
  
```  
'Tommy' = 'Tom'  
```  
  
 Le résultat est True (. T.) lorsque SET ANSI est désactivé, car la comparaison s’arrête après 'Tom'.  
  
## <a name="remarks"></a>Notes  
 SET ANSI détermine si la plus courte des deux chaînes est remplie avec des espaces lorsqu’une comparaison de chaînes SQL est effectuée. SET ANSI n’a aucun effet le ==, opérateur ; Lorsque vous utilisez l’opérateur ==, la chaîne plus courte est toujours complétée par des espaces pour la comparaison.  
  
## <a name="string-order"></a>Ordre de la chaîne  
 Dans les commandes SQL, l’ordre de gauche à droite des deux chaînes dans une comparaison est irrelevantswitching une chaîne à partir d’un côté de la = ou == opérateur à l’autre n’affecte pas le résultat de la comparaison.  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT, commande SQL](../../odbc/microsoft/select-sql-command.md)   
 [SET EXACT, commande](../../odbc/microsoft/set-exact-command.md)
