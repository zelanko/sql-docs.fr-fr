---
title: Écrivez une Application interopérable | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e559eab5787a64b6bdf0850147d7d9128fc435c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208577"
---
# <a name="writing-an-interoperable-application"></a>Écriture d’une application interopérable
Chaque fois qu’une application utilise le même code sur plus d’un pilote, ce code doit être interopérable entre ces pilotes. Dans la plupart des cas, il s’agit d’une tâche facile. Par exemple, le code pour extraire les lignes avec un curseur avant uniquement est identique pour tous les pilotes. Dans certains cas, cela peut être plus difficile. Par exemple, le code pour construire des identificateurs pour une utilisation dans les instructions SQL doit prendre en compte la casse de l’identificateur, des guillemets et des conventions d’affectation de noms une seule partie, les deux parties et les trois parties.  
  
 En règle générale, code interopérable doit faire face à des problèmes de prise en charge de la fonctionnalité et la variabilité de la fonctionnalité. *Prise en charge des fonctionnalités* fait référence à ou non une fonctionnalité particulière est prise en charge. Par exemple, pas tous les SGBD prennent en charge les transactions et interopérable code doit fonctionner correctement, quel que soit prise en charge de la transaction. *Fonctionnalité de variabilité* fait référence à la variation de la manière dont une fonctionnalité particulière est prise en charge. Par exemple, les noms de catalogues sont placés au début des identificateurs dans certains SGBD et à la fin des identificateurs dans d’autres.  
  
 Les applications peuvent traiter avec prise en charge de la fonctionnalité et la variabilité de la fonctionnalité au moment du design ou au moment de l’exécution. Pour faire face avec prise en charge de fonctionnalité et de variabilité au moment du design, un développeur examine la cible SGBD et les pilotes et permet de s’assurer que le même code seront interopérable entre eux. Il s’agit généralement de la façon dans lequel les applications avec l’interopérabilité faible ou limitée traitent ces problèmes.  
  
 Par exemple, si le développeur garantit qu’une application verticale fonctionne qu’avec quatre SGBD particulier et si chacun de ces SGBD prend en charge les transactions, l’application doit-elle pas de code de vérification de la prise en charge de la transaction en cours d’exécution. Il peut toujours supposer que les transactions sont disponibles en raison de la décision au moment du design à utiliser seulement quatre SGBD, chacun d’eux prend en charge les transactions.  
  
 Pour faire face avec prise en charge de fonctionnalité et de variabilité en cours d’exécution, l’application doit tester différentes fonctionnalités en cours d’exécution et agir en conséquence. Cela est généralement celle dans laquelle des applications hautement interopérables traitent ces problèmes. Pour les problèmes de prise en charge de fonctionnalité, cela signifie que d’écrire du code qui rend le code de fonction facultatif ou d’écriture qui émule la fonctionnalité lorsqu’il n’est pas disponible. Pour les problèmes de variabilité de fonctionnalité, cela signifie que d’écrire du code qui prend en charge toutes les variations possibles.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Vérification de la prise en charge et de la variabilité des fonctionnalités](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Fonctionnalités à considérer avec attention](../../../odbc/reference/develop-app/features-to-watch-for.md)
