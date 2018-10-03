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
manager: craigg
ms.openlocfilehash: 93f138988e0b01d6408a7aec96d09ceff65a6f5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757717"
---
# <a name="serializability"></a>Sérialisabilité
Dans l’idéal, les transactions doivent être *sérialisable*. Les transactions sont dits se situer sérialisable si les résultats de l’exécution de transactions simultanément sont les mêmes que les résultats de leur exécution en série : autrement dit, une après l’autre. N’importe quelle transaction s’exécute en premier, uniquement que le résultat ne reflète pas aucun mélange des transactions.  
  
 Par exemple, supposons que la transaction A multiplie les valeurs de données par 2 et la transaction B ajoute 1 aux valeurs de données. Supposons maintenant qu’il n’y a deux valeurs de données : 0 et 10. Si ces transactions sont exécutées une après l’autre, les nouvelles valeurs sera 1 et 21 si la transaction A est exécutée en premier, ou 2 et 22 si la transaction B est exécutée en premier. Mais que se passe-t-il si l’ordre dans lequel les deux transactions sont exécutées est différent pour chaque valeur ? Si la transaction Qu'a est exécuté en premier sur la première valeur et la transaction B sont exécutés en premier sur la deuxième valeur, les nouvelles valeurs sont 1 et 22. Si cet ordre est inversé, les nouvelles valeurs sont 2 et 21. Les transactions sont sérialisables si 1, 21 et 2, 22 sont les résultats n’est possibles. Les transactions ne sont pas sérialisable si 1, 22 ou 2, 21 est un résultat possible.  
  
 Quel en est donc la sérialisation souhaitable ? En d’autres termes, pourquoi est-ce important qu’il s’affiche une transaction se termine avant le démarrage de la transaction suivante ? Prenez le problème suivant. Un commercial est saisie de commandes en même temps qu'un employé envoie factures. Supposons que le commercial entre une commande à partir de la société X, mais ne la valide pas ; le commercial toujours communique avec le représentant de la société X. Le régisseur demande une liste de toutes les commandes ouvertes et détecte l’ordre de la société X et les envoie une facture. Maintenant le représentant de la société X décide qu'ils souhaitent modifier leur ordre, de sorte que si le commercial il change avant de valider la transaction. Société X Obtient une facture incorrecte.  
  
 Si du commercial et du régisseur de transactions ont été sérialisables, ce problème aurait jamais se sont produites. Les transactions entre le commercial seraient terminées avant le début du transaction de régisseur, auquel cas le régisseur sera donc avoir envoyé la facture correcte, ou les transactions de l’employé seraient terminées avant du commercial de la transaction, auquel cas le régisseur n'aurait pas envoyé une facture à la société X du tout.
