---
title: Pilotes | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6460410488186c94713d859bf2912f2844ca2736
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915432"
---
# <a name="drivers"></a>Pilotes
*Pilotes* sont des bibliothèques qui implémentent les fonctions de l’API ODBC. Chacun est spécifique à un SGBD particulier ; par exemple, un pilote pour Oracle ne peut pas accéder directement aux données dans un DBMS Informix. Pilotes d’exposent les fonctionnalités des SGBD sous-jacent ; ils ne sont pas requis pour implémenter des fonctionnalités non prises en charge par le SGBD. Par exemple, si le SGBD sous-jacent ne prend pas en charge les jointures externes, puis ni doit le pilote. La seule exception majeure à cela est que les pilotes pour les SGBD qui n’ont pas de moteurs de base de données autonome, comme Xbase, doivent implémenter un moteur de base de données qui prend en charge au moins une quantité minimale de SQL.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Tâches des pilotes](../../odbc/reference/driver-tasks.md)  
  
-   [Architecture des pilotes](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Pilotes ODBC fournis par Microsoft](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
