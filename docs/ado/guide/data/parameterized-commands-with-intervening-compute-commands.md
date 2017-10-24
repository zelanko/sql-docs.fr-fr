---
title: "Des commandes avec les commandes de calcul qui interviennent paramétrées | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8821ebd2fb20cf32c6b1921c36e45404421f415b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>Les commandes paramétrables par l’intermédiaire des commandes COMPUTE
Une forme paramétrée commande APPEND contient généralement une clause qui crée un parent **Recordset** avec une commande de requête et une autre clause qui crée un enfant **Recordset** avec une commande de requête paramétrée : Autrement dit, une commande contenant un espace réservé de paramètre (un point d’interrogation « ? »). La forme résultant **Recordset** a deux niveaux, dans laquelle le parent occupe le niveau supérieur et le niveau inférieur occupé par l’enfant.  
  
 La clause qui crée l’enfant **Recordset** peut maintenant être un nombre arbitraire de forme imbriquées commandes de calcul, la commande la plus profondément imbriquée contenant la requête paramétrable. La forme résultant **Recordset** a plusieurs niveaux, dans lequel occupé par le parent le plus haut niveau, l’enfant occupe le niveau de la plus basse et un nombre arbitraire de **Recordset**s générés par le commandes de mise en forme occupent les niveaux intermédiaires.  
  
 L’utilisation classique pour cette fonctionnalité consiste à appeler la fonction d’agrégation et les fonctionnalités de regroupement de shapeCOMPUTE commandes pour créer des intervenants **Recordset** objets avec des informations analytiques sur l’enfant **Recordset **. En outre, comme il s’agit d’une commande de mise en forme paramétrée, chaque fois qu’une colonne de chapitre du parent est accessible, un nouvel enfant **Recordset** peuvent être récupérées. Étant donné que les niveaux intermédiaires sont dérivés de l’enfant, ils également recalculés.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)

