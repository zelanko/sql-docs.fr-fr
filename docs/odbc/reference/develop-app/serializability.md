---
title: Serializability (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transaction isolation [ODBC]
- transactions [ODBC], serialization
- serialization [ODBC]
- transactions [ODBC], isolation
ms.assetid: 142e4ac0-2977-4a2b-96ae-c9e5bd2c448a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0557e011578d313765614c05a2a9cf1b975bbc08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304160"
---
# <a name="serializability"></a>Sérialisabilité
Idéalement, les transactions devraient être *sérialisables*. Les transactions sont dites sérialisables si les résultats des transactions en cours d’exécution simultanément sont les mêmes que les résultats de les exécuter en série - c’est-à-dire, l’un après l’autre. Il n’est pas important quelle transaction s’exécute en premier, mais seulement que le résultat ne reflète aucun mélange des transactions.  
  
 Par exemple, supposons que la transaction A multiplie les valeurs de données par 2 et la transaction B ajoute 1 aux valeurs de données. Supposons maintenant qu’il existe deux valeurs de données : 0 et 10. Si ces transactions sont exécutées l’une après l’autre, les nouvelles valeurs seront de 1 et 21 si la transaction A est exécutée en premier, ou 2 et 22 si la transaction B est exécutée en premier. Mais que se passe-t-il si l’ordre dans lequel les deux transactions sont exécutées est différent pour chaque valeur? Si la transaction A est exécutée en premier sur la première valeur et que la transaction B est exécutée en premier sur la deuxième valeur, les nouvelles valeurs sont de 1 et 22. Si cet ordre est inversé, les nouvelles valeurs sont 2 et 21. Les transactions sont sérialisables si 1, 21 et 2, 22 sont les seuls résultats possibles. Les transactions ne sont pas sérialisables si 1, 22 ou 2, 21 est un résultat possible.  
  
 Alors pourquoi la sérialisation est-elle souhaitable ? En d’autres termes, pourquoi est-il important qu’il semble qu’une transaction se termine avant le début de la prochaine transaction? Considérez le problème suivant. Un vendeur entre les commandes en même temps qu’un commis envoie des factures. Supposons que le vendeur entre dans une commande de la Société X, mais ne l’engage pas; le vendeur parle toujours au représentant de la société X. Le greffier demande une liste de toutes les commandes ouvertes et découvre la commande pour la société X et leur envoie une facture. Maintenant, le représentant de la société X décide qu’ils veulent changer leur commande, de sorte que le vendeur le change avant de commettre la transaction. La compagnie X reçoit une facture incorrecte.  
  
 Si les transactions du vendeur et du commis étaient sérialisables, ce problème ne se serait jamais produit. Soit la transaction du vendeur aurait pris fin avant le début de la transaction du commis, auquel cas le greffier aurait envoyé le bon projet de loi, soit la transaction du commis aurait pris fin avant le début de la transaction du vendeur, auquel cas le greffier n’aurait pas du tout envoyé une facture à la compagnie X.
