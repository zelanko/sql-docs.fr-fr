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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3ac58e59f66dd107a9523a42f5647c90b4fb737
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297710"
---
# <a name="managing-text-and-image-columns"></a>Gestion des colonnes text et image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les données **Text**, **ntext**et **image** (également appelées données de type long) sont des types de données de chaîne de caractères ou binaires qui peuvent contenir des valeurs de données trop grandes pour tenir dans des colonnes **char**, **varchar**, **Binary**ou **varbinary** . Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données **Text** est mappé sur le type de données SQL_LONGVARCHAR ODBC ; **ntext** est mappé à SQL_WLONGVARCHAR ; et **images** est mappé à SQL_LONGVARBINARY. Certains éléments de données, tels que les longs documents ou les images bitmaps volumineuses, peuvent être trop grands pour pouvoir être stockés raisonnablement en mémoire. Pour récupérer des données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type long dans des parties [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] séquentielles, le pilote ODBC Native Client permet à une application d’appeler [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Pour envoyer des données de type long dans des parties séquentielles, l’application peut appeler [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). Les paramètres pour lesquels les données sont envoyées au moment de l'exécution sont connus comme paramètres de données en cours d'exécution.  
  
 Une application peut en fait écrire ou récupérer n’importe quel type de données (pas seulement des données longues) avec **SQLPutData** ou **SQLGetData**, bien que seules les données de type **caractère** et **binaire** puissent être envoyées ou récupérées dans des parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData** ou **SQLGetData**. Il est beaucoup plus facile de lier la mémoire tampon unique au paramètre ou à la colonne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes de texte et d'image liées et non liées](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifications enregistrées ou non enregistrées](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Colonnes text, ntext ou image de données en cours d’exécution](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
