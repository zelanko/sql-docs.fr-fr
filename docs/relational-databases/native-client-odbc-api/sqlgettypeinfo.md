---
description: SQLGetTypeInfo
title: SQLGetTypeInfo | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9bea9cc9285d99c5632dc443a135008ff5f3799
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97485061"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client signale la colonne supplémentaire usertype dans le jeu de résultats de **SQLGetTypeInfo**. USERTYPE signale la définition de type de données de bibliothèque de bases de données et est utile aux développeurs qui déplacent des applications de bibliothèque de bases de données existantes vers ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite l'identité comme un attribut, tandis que ODBC la traite comme un type de données. Pour résoudre ce problème, **SQLGetTypeInfo** retourne les types de données suivants : **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity** et **NumericIdentity**. La colonne de jeu de résultats **SQLGetTypeInfo** AUTO_UNIQUE_VALUE indique la valeur true pour ces types de données.  
  
 Pour les valeurs de type **varchar**, **nvarchar** et **varbinary**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client continue à signaler 8000, 4000 et 8000 pour la valeur COLUMN_SIZE, bien qu’il soit en fait illimité. Ceci a pour but de garantir la compatibilité descendante.  
  
 Pour le type de données **XML** , le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client signale SQL_SS_LENGTH_UNLIMITED COLUMN_SIZE pour indiquer une taille illimitée.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo et paramètres table  
 Le type de table pour les paramètres table est en fait un type méta, c’est-à-dire un type utilisé pour définir d’autres types. Par conséquent, il n’est pas nécessaire de l’exposer via SQLGetTypeInfo. Les applications doivent utiliser SQLTables, plutôt que SQLGetTypeInfo, pour récupérer les métadonnées des types de tables utilisés avec les paramètres table.  
  
 Pour plus d’informations sur la récupération de métadonnées pour les paramètres table, consultez [attributs d’instruction qui affectent les paramètres de Table-Valued](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLGetTypeInfo pour les fonctionnalités Date et Heure améliorées  
 Pour les valeurs retournées pour les types de date/heure, consultez [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Prise en charge SQLGetTypeInfo pour les types CLR volumineux définis par l'utilisateur  
 **SQLGetTypeInfo** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types de User-Defined CLR volumineux &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetTypeInfo, fonction](../../odbc/reference/syntax/sqlgettypeinfo-function.md)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
