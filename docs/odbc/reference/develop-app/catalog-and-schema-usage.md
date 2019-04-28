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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007887"
---
# <a name="catalog-and-schema-usage"></a>Utilisation des catalogues et des schémas
Sources de données ne gèrent pas nécessairement les noms de catalogue et le schéma en tant qu’identificateurs de nom d’objet dans toutes les instructions SQL. Sources de données peuvent prendre en charge les noms de catalogue et de schéma dans une ou plusieurs des classes d’instructions SQL suivantes : Instructions de langage de manipulation de données, les appels de procédure, les instructions de définition de table, instructions de définition d’index et les instructions de définition de privilège. Pour déterminer les classes d’instructions SQL dans le catalogue et de schéma les noms peuvent être utilisés, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_USAGE et SQL_SCHEMA_USAGE.
