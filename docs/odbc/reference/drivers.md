---
description: Pilotes
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 81e8989fc178728e687baa13b37e6055692d9413
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494592"
---
# <a name="drivers"></a>Pilotes
Les *pilotes* sont des bibliothèques qui implémentent les fonctions dans l’API ODBC. Chaque est spécifique à un SGBD particulier. par exemple, un pilote pour Oracle ne peut pas accéder directement aux données d’un SGBD Informix. Les pilotes exposent les fonctionnalités des SGBD sous-jacents. ils ne sont pas requis pour implémenter des fonctionnalités non prises en charge par le SGBD. Par exemple, si le SGBD sous-jacent ne prend pas en charge les jointures externes, le pilote ne doit pas être le même. La seule exception majeure est que les pilotes des SGBD qui n’ont pas de moteurs de base de données autonomes, tels que xbase, doivent implémenter un moteur de base de données qui, au moins, prend en charge une quantité minimale de SQL.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Tâches des pilotes](../../odbc/reference/driver-tasks.md)  
  
-   [Architecture des pilotes](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Pilotes ODBC fournis par Microsoft](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
