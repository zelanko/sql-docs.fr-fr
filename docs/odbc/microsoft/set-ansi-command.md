---
title: Set ANSI Commande Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97269642b4147b966fdd71003f5f81ebe7905282
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300909"
---
# <a name="set-ansi-command"></a>SET ANSI, commande
Détermine comment les comparaisons entre les chaînes de différentes longueurs sont faites avec l’opérateur de Visual FoxPro SQL commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 (Par défaut pour le pilote; la valeur par défaut pour Visual FoxPro est OFF.) Pads la chaîne plus courte avec les blancs nécessaires pour le rendre égal à la longueur de la plus longue chaîne. Les deux cordes sont ensuite comparées caractère pour le caractère pour leurs longueurs entières. Considérez cette comparaison :  
  
```  
'Tommy' = 'Tom'  
```  
  
 Le résultat est faux (. F.) si SET ANSI est sur, parce que lorsqu’il est rembourré, «Tom» devient «Tom» et les cordes «Tom» et «Tommy» ne correspondent pas au caractère pour le caractère.  
  
 L’opérateur utilise cette méthode pour des comparaisons dans visual FoxPro SQL commandes.  
  
 OFF  
 Précise que la ficelle plus courte ne doit pas être rembourrée avec des blancs. Les deux cordes sont comparées caractère pour le caractère jusqu’à ce que la fin de la chaîne plus courte est atteint. Considérez cette comparaison :  
  
```  
'Tommy' = 'Tom'  
```  
  
 Le résultat est vrai (. T.) quand SET ANSI est éteint, parce que la comparaison s’arrête après 'Tom'.  
  
## <a name="remarks"></a>Notes  
 SET ANSI détermine si le plus court des deux cordes est rembourré avec des blancs quand une comparaison de chaîne SQL est faite. SET ANSI n’a aucun effet sur l’opérateur de l’OPÉRATEUR; lorsque vous utilisez l’opérateur, la chaîne plus courte est toujours rembourrée avec des blancs pour la comparaison.  
  
## <a name="string-order"></a>Ordre de cordes  
 Dans les commandes SQL, l’ordre de gauche à droite des deux cordes dans une comparaison n’est pas pertinentwitching une chaîne d’un côté de l’opérateur ou de l’autre n’affecte pas le résultat de la comparaison.  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT - Commandement SQL](../../odbc/microsoft/select-sql-command.md)   
 [SET EXACT, commande](../../odbc/microsoft/set-exact-command.md)
