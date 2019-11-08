---
title: Gestion des colonnes text et image | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 221d83188a3d48fe5383a109b878c7b5a59bdad5
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73758398"
---
# <a name="managing-text-and-image-columns"></a>Gestion des colonnes text et image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données **Text**, **ntext**et **image** (également appelées données de type long) sont des types de données de chaîne de caractères ou binaires qui peuvent contenir des valeurs de données trop grandes pour tenir dans **char**, **varchar**, **Binary**ou **varbinary** colonnes. Le type de données de **texte** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est mappé sur le type de données ODBC SQL_LONGVARCHAR ; **ntext** est mappé à SQL_WLONGVARCHAR ; et **images** est mappé à SQL_LONGVARBINARY. Certains éléments de données, tels que les longs documents ou les images bitmaps volumineuses, peuvent être trop grands pour pouvoir être stockés raisonnablement en mémoire. Pour extraire des données de type long de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans des parties séquentielles, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client permet à une application d’appeler [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Pour envoyer des données de type long dans des parties séquentielles, l’application peut appeler [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). Les paramètres pour lesquels les données sont envoyées au moment de l'exécution sont connus comme paramètres de données en cours d'exécution.  
  
 Une application peut en fait écrire ou récupérer n’importe quel type de données (pas seulement des données longues) avec **SQLPutData** ou **SQLGetData**, bien que seules les données de type **caractère** et **binaire** puissent être envoyées ou récupérées dans des parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData** ou **SQLGetData**. Il est beaucoup plus facile de lier la mémoire tampon unique au paramètre ou à la colonne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes de texte et d’image liées et non liées](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifications journalisées et non journalisées](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Colonnes text, ntext ou image de données en cours d’exécution](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
