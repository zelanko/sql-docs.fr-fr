---
title: Catalogue et l’utilisation de schéma | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9476f4f928890514354f97ce604f871bd8a06d11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702827"
---
# <a name="catalog-and-schema-usage"></a>Utilisation des catalogues et des schémas
Sources de données ne gèrent pas nécessairement les noms de catalogue et le schéma en tant qu’identificateurs de nom d’objet dans toutes les instructions SQL. Sources de données peuvent prendre en charge les noms de catalogue et de schéma dans un ou plusieurs des classes d’instructions SQL suivantes : instructions de langage DML (Data Manipulation), les appels de procédure, instructions de définition de table, instructions de définition d’index et définition de privilège instructions. Pour déterminer les classes d’instructions SQL dans le catalogue et de schéma les noms peuvent être utilisés, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_USAGE et SQL_SCHEMA_USAGE.
