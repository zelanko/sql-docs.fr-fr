---
description: Écriture d’une application interopérable
title: Écriture d’une application interopérable | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: 8b42b8ae-7862-4b63-a0b3-2a204e0c43a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d8bff1848e20705ab64b8284ed42331c80fb23a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421363"
---
# <a name="writing-an-interoperable-application"></a>Écriture d’une application interopérable
Chaque fois qu’une application utilise le même code sur plusieurs pilotes, ce code doit être interopérable entre ces pilotes. Dans la plupart des cas, il s’agit d’une tâche facile. Par exemple, le code permettant d’extraire des lignes avec un curseur avant uniquement est le même pour tous les pilotes. Dans certains cas, cela peut être plus difficile. Par exemple, le code permettant de construire des identificateurs pour une utilisation dans des instructions SQL doit prendre en compte les conventions d’affectation de noms, de guillemets et d’une partie, en deux parties et en trois parties.  
  
 En général, le code interopérable doit faire face aux problèmes liés à la prise en charge des fonctionnalités et à la variabilité des fonctionnalités. La *prise en charge des fonctionnalités* fait référence à la prise en charge d’une fonctionnalité particulière. Par exemple, tous les SGBD ne prennent pas en charge les transactions et le code interopérable doit fonctionner correctement indépendamment de la prise en charge des transactions. La *variabilité des fonctionnalités* fait référence à la variation de la façon dont une fonctionnalité particulière est prise en charge. Par exemple, les noms de catalogue sont placés au début des identificateurs dans certains SGBD et à la fin des identificateurs dans d’autres.  
  
 Les applications peuvent gérer la prise en charge des fonctionnalités et la variabilité des fonctionnalités au moment du design ou au moment de l’exécution. Pour gérer la prise en charge des fonctionnalités et la variabilité au moment du design, un développeur examine les SGBD et les pilotes cibles et s’assure que le même code peut être interopérable entre eux. Il s’agit généralement de la façon dont les applications avec une interopérabilité faible ou limitée traitent de ces problèmes.  
  
 Par exemple, si le développeur garantit qu’une application verticale fonctionne uniquement avec quatre SGBD particuliers et si chacun de ces SGBD prend en charge les transactions, l’application n’a pas besoin de code pour vérifier la prise en charge des transactions au moment de l’exécution. Il peut toujours supposer que les transactions sont disponibles en raison de la décision au moment du design d’utiliser uniquement quatre SGBD, chacun prenant en charge les transactions.  
  
 Pour gérer la prise en charge des fonctionnalités et la variabilité au moment de l’exécution, l’application doit tester des fonctionnalités différentes au moment de l’exécution et agir en conséquence. Il s’agit généralement de la façon dont les applications hautement interopérables traitent ces problèmes. Pour les problèmes de prise en charge des fonctionnalités, cela signifie écrire du code qui rend la fonctionnalité facultative ou écrire du code qui émule la fonctionnalité lorsqu’elle n’est pas disponible. Pour les problèmes de variabilité des fonctionnalités, cela signifie écrire du code qui prend en charge toutes les variations possibles.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Vérification de la prise en charge et de la variabilité des fonctionnalités](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Fonctionnalités à considérer avec attention](../../../odbc/reference/develop-app/features-to-watch-for.md)
