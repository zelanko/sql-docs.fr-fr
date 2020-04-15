---
title: Rédaction d’une demande interopérable (fr) Microsoft Docs
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
ms.openlocfilehash: 553e718e0759e47701e7f8c04561693358d5dc52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289081"
---
# <a name="writing-an-interoperable-application"></a>Écriture d’une application interopérable
Chaque fois qu’une application utilise le même code contre plus d’un pilote, ce code doit être interopérable chez ces conducteurs. Dans la plupart des cas, c’est une tâche facile. Par exemple, le code pour aller chercher des rangées avec un curseur avant seulement est le même pour tous les conducteurs. Dans certains cas, cela peut être plus difficile. Par exemple, le code pour construire des identificateurs pour une utilisation dans les relevés SQL doit tenir compte des cas d’identification, de la citation et des conventions de nommage en deux parties en une partie et en trois parties.  
  
 En général, le code interopérable doit faire face aux problèmes de support des fonctionnalités et de variabilité des fonctionnalités. *Le support de fonctionnalité* se réfère à savoir si une fonctionnalité particulière est prise en charge. Par exemple, toutes les transactions de support DBMS ne doivent pas fonctionner correctement, quel que soit le support transactionnel. *La variabilité des fonctionnalités* se réfère à la variation de la façon dont une fonctionnalité particulière est prise en charge. Par exemple, les noms de catalogue sont placés au début des identificateurs dans certains DBMS et à la fin des identificateurs dans d’autres.  
  
 Les applications peuvent traiter de la prise en charge des fonctionnalités et de la variabilité des fonctionnalités au moment de la conception ou au moment de l’exécution. Pour faire face au support des fonctionnalités et à la variabilité au moment de la conception, un développeur examine les DBMS et les pilotes cibles et s’assure que le même code sera interopérable parmi eux. C’est généralement la façon dont les applications avec une interopérabilité faible ou limitée traitent ces problèmes.  
  
 Par exemple, si le développeur garantit qu’une application verticale ne fonctionnera qu’avec quatre DBMS particuliers et si chacun de ces DBMS prend en charge les transactions, l’application n’a pas besoin de code pour vérifier la prise en charge des transactions au moment de l’exécution. Il peut toujours supposer que les transactions sont disponibles en raison de la décision de conception-temps d’utiliser seulement quatre DBMS, dont chacun prend en charge les transactions.  
  
 Pour faire face à la prise en charge des fonctionnalités et à la variabilité au moment de l’exécution, l’application doit tester pour différentes capacités au moment de l’exécution et agir en conséquence. C’est généralement la façon dont les applications hautement interopérables traitent ces problèmes. Pour les problèmes de support de fonctionnalité, cela signifie la rédaction de code qui rend la fonctionnalité facultative ou la rédaction de code qui imite la fonctionnalité quand il n’est pas disponible. Pour les problèmes de variabilité des fonctionnalités, cela signifie la rédaction de code qui prend en charge toutes les variations possibles.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Vérification de la prise en charge et de la variabilité des fonctionnalités](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Fonctionnalités à considérer avec attention](../../../odbc/reference/develop-app/features-to-watch-for.md)
