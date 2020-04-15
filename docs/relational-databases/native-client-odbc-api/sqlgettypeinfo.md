---
title: SQLGetTypeInfo - France Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81ba57c6e66f156f13055ff5ec941fa8f0c86381
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298435"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur native Client ODBC signale la colonne supplémentaire USERTYPE dans l’ensemble de résultat de **SQLGetTypeInfo**. USERTYPE signale la définition de type de données de bibliothèque de bases de données et est utile aux développeurs qui déplacent des applications de bibliothèque de bases de données existantes vers ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite l'identité comme un attribut, tandis que ODBC la traite comme un type de données. Pour résoudre ce décalage, **SQLGetTypeInfo** retourne les types de données : **intidentité,** **petite identité,** **infimeté,** **décimalité,** **et numérique.** La colonne de jeu de résultat **SQLGetTypeInfo** AUTO_UNIQUE_VALUE signale la valeur VRAI pour ces types de données.  
  
 Pour **le varchar,** **le nvarchar** et le **varbinaire,** le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC continue de rapporter respectivement 8000, 4000 et 8000 pour la valeur COLUMN_SIZE, même si elle est en fait illimitée. Ceci a pour but de garantir la compatibilité descendante.  
  
 Pour le type de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données **xml,** le conducteur de Native Client ODBC signale SQL_SS_LENGTH_UNLIMITED pour COLUMN_SIZE de désigner la taille illimitée.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo et paramètres table  
 Le type de table pour les paramètres de valeur de table est effectivement un méta-type-qui est, un type utilisé pour définir d’autres types. Par conséquent, il n’a pas besoin d’être exposé par SQLGetTypeInfo. Les applications doivent utiliser SQLTables, plutôt que SQLGetTypeInfo, pour récupérer les métadonnées pour les types de table utilisés avec des paramètres de valeur de table.  
  
 Pour plus d’informations, sur la récupération des metdata pour les paramètres évalués à la table, voir [attributs d’énoncé qui affectent les paramètres de valeur de la table](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Pour plus d’informations sur les paramètres de valeur de table, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLGetTypeInfo pour les fonctionnalités Date et Heure améliorées  
 Pour les valeurs retournées pour les types de date/heure, consultez [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Prise en charge SQLGetTypeInfo pour les types CLR volumineux définis par l'utilisateur  
 **SQLGetTypeInfo** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLGetTypeInfo](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
