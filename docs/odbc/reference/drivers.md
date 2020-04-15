---
title: Les conducteurs Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c8b40641be3db34fc6929edecdd5dd923700957
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294182"
---
# <a name="drivers"></a>Pilotes
*Les conducteurs* sont des bibliothèques qui implémentent les fonctions de l’API ODBC. Chacun est spécifique à un DBMS particulier; par exemple, un pilote pour Oracle ne peut pas accéder directement aux données dans un DBMS Informix. Les conducteurs exposent les capacités des DBMS sous-jacents; ils ne sont pas tenus de mettre en œuvre des capacités non prises en charge par le DBMS. Par exemple, si le DBMS sous-jacent ne prend pas en charge les jointures extérieures, le conducteur ne devrait pas non plus. La seule exception majeure à cela est que les conducteurs de DBMS qui n’ont pas de moteurs de base de données autonomes, comme Xbase, doivent mettre en œuvre un moteur de base de données qui prend au moins en charge une quantité minimale de SQL.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Tâches des pilotes](../../odbc/reference/driver-tasks.md)  
  
-   [Architecture des pilotes](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Pilotes ODBC fournis par Microsoft](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
