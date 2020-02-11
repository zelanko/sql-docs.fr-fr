---
title: Sérialisation | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 49552e7333d8cac2b55a9ae6e8dd7a41ff4c5955
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094331"
---
# <a name="serializability"></a>Sérialisabilité
Dans l’idéal, les transactions doivent être *sérialisables*. Les transactions sont considérées comme sérialisables si les résultats des transactions exécutées simultanément sont les mêmes que les résultats de leur exécution en série, c’est-à-dire l’un après l’autre. Il n’est pas important que la transaction s’exécute en premier, mais uniquement que le résultat ne reflète pas la combinaison des transactions.  
  
 Par exemple, supposons que la transaction A multiplie les valeurs de données par 2 et que la transaction B ajoute 1 aux valeurs de données. Supposons à présent qu’il y ait deux valeurs de données : 0 et 10. Si ces transactions sont exécutées l’une après l’autre, les nouvelles valeurs sont 1 et 21 si la transaction A est exécutée en premier, ou 2 et 22 si la transaction B est exécutée en premier. Mais que se passe-t-il si l’ordre dans lequel les deux transactions sont exécutées est différent pour chaque valeur ? Si la transaction A est exécutée en premier sur la première valeur et que la transaction B est d’abord exécutée sur la deuxième valeur, les nouvelles valeurs sont 1 et 22. Si cet ordre est inversé, les nouvelles valeurs sont 2 et 21. Les transactions sont sérialisables si 1, 21 et 2, 22 sont les seuls résultats possibles. Les transactions ne sont pas sérialisables si 1, 22 ou 2, 21 est un résultat possible.  
  
 Pourquoi la sérialisation est-elle souhaitable ? En d’autres termes, pourquoi est-il important qu’une transaction se termine avant le début de la transaction suivante ? Considérez le problème suivant. Un commercial saisit des commandes en même temps qu’un régisseur envoie des factures. Supposons que le commercial entre une commande de la société X, mais ne la valide pas ; le commercial parle toujours du représentant de la société X. L’employé demande une liste de toutes les commandes ouvertes et Découvre la commande pour la société X et lui envoie une facture. À présent, le représentant de la société X décide qu’il souhaite modifier sa commande, de sorte que le commercial le modifie avant de valider la transaction. La société X obtient une facture incorrecte.  
  
 Si les transactions du commercial et du Clerk étaient sérialisables, ce problème ne se produirait jamais. Soit la transaction du commercial est terminée avant le début de la transaction du régisseur, auquel cas le régisseur aurait envoyé la facture correcte, ou la transaction du Clerk est terminée avant le début de la transaction du commercial, auquel cas le le régisseur n’aurait pas envoyé de facture à la société X.
