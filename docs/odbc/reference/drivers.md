---
title: Pilotes | Documents Microsoft
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f25be027774c83a31077953eaf51ea8f643bf5e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="drivers"></a>Pilotes
*Pilotes* sont des bibliothèques qui implémentent les fonctions de l’API ODBC. Chacun est spécifique à un SGBD particulier ; par exemple, un pilote pour Oracle ne peut pas accéder directement les données dans un DBMS Informix. Pilotes d’exposent les fonctionnalités des SGBD sous-jacent ; ils ne sont pas requis pour implémenter des fonctionnalités non prises en charge par le SGBD. Par exemple, si le SGBD sous-jacent ne prend pas en charge les jointures externes, alors aucune des deux doit être le pilote. La seule exception majeure à cela est que les pilotes pour les SGBD qui n’ont pas de moteurs de base de données autonome, telles que Xbase, doivent implémenter un moteur de base de données qui prend en charge au moins d’une quantité minimale de SQL.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Tâches de pilote](../../odbc/reference/driver-tasks.md)  
  
-   [Architecture du pilote](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Pilotes ODBC de fournis par Microsoft](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)

