---
title: SQLGetTypeInfo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60c4c4d364f9c07e9ca241dd357535f7f7acb42d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046685"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client signale la colonne supplémentaire usertype dans le jeu de `SQLGetTypeInfo`résultats de. USERTYPE signale la définition de type de données de bibliothèque de bases de données et est utile aux développeurs qui déplacent des applications de bibliothèque de bases de données existantes vers ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite l'identité comme un attribut, tandis que ODBC la traite comme un type de données. Pour résoudre cette incompatibilité `SQLGetTypeInfo` , retourne les types de données suivants : **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity**et **NumericIdentity**. La `SQLGetTypeInfo` colonne de l’ensemble de résultats AUTO_UNIQUE_VALUE indique la valeur true pour ces types de données.  
  
 Pour les valeurs de type **varchar**, **nvarchar** et **varbinary**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client continue à signaler 8000, 4000 et 8000 pour la valeur COLUMN_SIZE, bien qu’il soit en fait illimité. Ceci a pour but de garantir la compatibilité descendante.  
  
 Pour le type de données **XML** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client signale SQL_SS_LENGTH_UNLIMITED COLUMN_SIZE pour indiquer une taille illimitée.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo et paramètres table  
 Le type de table pour les paramètres table est en fait un type méta, c’est-à-dire un type utilisé pour définir d’autres types. Par conséquent, il n’est pas nécessaire de l’exposer via SQLGetTypeInfo. Les applications doivent utiliser SQLTables, plutôt que SQLGetTypeInfo, pour récupérer les métadonnées des types de tables utilisés avec les paramètres table.  
  
 Pour plus d’informations sur la récupération de métadonnées pour les paramètres table, consultez [attributs d’instruction qui affectent les paramètres table](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLGetTypeInfo pour les fonctionnalités Date et Heure améliorées  
 Pour les valeurs retournées pour les types de date/heure, consultez [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Prise en charge SQLGetTypeInfo pour les types CLR volumineux définis par l'utilisateur  
 `SQLGetTypeInfo` prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetTypeInfo, fonction](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
