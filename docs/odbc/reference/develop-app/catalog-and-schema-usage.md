---
title: Catalogue et l’utilisation de schéma | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0d28c36082c8bcc60b6332928532636f4952d036
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="catalog-and-schema-usage"></a>Catalogue et l’utilisation de schéma
Sources de données ne gèrent pas nécessairement les noms de catalogue et le schéma en tant qu’identificateurs de nom d’objet dans toutes les instructions SQL. Sources de données peuvent prendre en charge les noms de catalogue et de schéma dans une ou plusieurs des classes d’instructions SQL suivantes : instructions langage DML (Data Manipulation), les appels de procédure, les instructions de définition de table, instructions de définition d’index et les instructions de définition de privilège. Pour déterminer les classes d’instructions SQL dans le catalogue et de schéma les noms peuvent être utilisés, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_USAGE et SQL_SCHEMA_USAGE.
