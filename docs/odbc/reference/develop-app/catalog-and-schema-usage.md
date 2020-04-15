---
title: Catalogue et Utilisation de Schema Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 245bd007f070a94689283830ba7a1362e31353e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306250"
---
# <a name="catalog-and-schema-usage"></a>Utilisation des catalogues et des schémas
Les sources de données ne prennent pas nécessairement en charge les noms de catalogue et de schéma comme identifiants de nom d’objet dans toutes les déclarations SQL. Les sources de données peuvent prendre en charge les noms de catalogue et de schémas dans une ou plusieurs des catégories suivantes de déclarations SQL : déclarations de langage de manipulation de données (DML), appels de procédure, énoncés de définition de tableau, énoncés de définition d’index et énoncés de définition de privilège. Pour déterminer les classes de relevés SQL dans lesquels les noms de catalogue et de schéma peuvent être utilisés, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_USAGE et SQL_SCHEMA_USAGE.
