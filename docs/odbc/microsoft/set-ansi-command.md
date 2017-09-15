---
title: Commande SET ANSI | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2095dc0b30fc2e16d4ce691cc097dcda1614d090
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="set-ansi-command"></a>Commande SET ANSI
Détermine la façon dont les comparaisons entre des chaînes de longueurs différentes sont effectuées avec l’opérateur dans les commandes Visual FoxPro SQL =.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 (Par défaut pour le pilote, la valeur par défaut pour Visual FoxPro est désactivé.) Remplit pour que la chaîne courte avec les valeurs vides nécessaires rend la longueur de chaîne égale à la plus. Les deux chaînes sont ensuite comparé caractère pour caractère pour leurs longueurs entières. Prenez en compte cette comparaison :  
  
```  
'Tommy' = 'Tom'  
```  
  
 Le résultat est False (. F.) si SET ANSI est activé, car lorsque complétées, « Thomas » devient « Tom » et les chaînes « Tom » et 'Tommy' ne correspondent pas pour caractère.  
  
 Le == opérateur utilise cette méthode pour les comparaisons de commandes Visual FoxPro SQL.  
  
 OFF  
 Spécifie que la chaîne courte ne soient ne pas complétés par des espaces. Les deux chaînes sont comparées caractère pour caractère jusqu'à la fin de la chaîne la plus courte. Prenez en compte cette comparaison :  
  
```  
'Tommy' = 'Tom'  
```  
  
 Le résultat est True (. T.) lorsque SET ANSI est désactivé, car la comparaison s’arrête après 'Tom'.  
  
## <a name="remarks"></a>Notes  
 SET ANSI détermine si le plus court des deux chaînes est complété avec des espaces lors d’une comparaison de chaînes SQL. SET ANSI n’a aucun effet le ==, opérateur ; Lorsque vous utilisez l’opérateur ==, la chaîne courte est toujours complétée par des espaces pour la comparaison.  
  
## <a name="string-order"></a>Ordre de la chaîne  
 Dans les commandes SQL, l’ordre de gauche à droite des deux chaînes dans une comparaison est irrelevantswitching une chaîne à partir d’un côté de l’opération = ou == opérateur à l’autre n’affecte pas le résultat de la comparaison.  
  
## <a name="see-also"></a>Voir aussi  
 [Sélectionnez - commande SQL](../../odbc/microsoft/select-sql-command.md)   
 [Commande exacte de jeu](../../odbc/microsoft/set-exact-command.md)
