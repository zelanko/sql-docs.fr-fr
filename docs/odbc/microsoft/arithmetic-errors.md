---
title: "Les erreurs arithmétiques | Documents Microsoft"
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
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d3585f6e1be7a3f9451231004979321202d7852
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="arithmetic-errors"></a>Erreurs arithmétiques
Le pilote ODBC évalue la clause WHERE dans une instruction SELECT, il extrait chaque ligne. Si une ligne contient une valeur qui entraîne une erreur arithmétique, telles que de dépassement de capacité numérique ou de division par zéro, le pilote retourne toutes les lignes, mais renvoie des erreurs pour les colonnes avec des erreurs arithmétiques. Lors de l’insertion ou de mise à jour, toutefois, le pilote ODBC arrête insertion ou mise à jour des données lors de la première erreur arithmétique est rencontrée.

