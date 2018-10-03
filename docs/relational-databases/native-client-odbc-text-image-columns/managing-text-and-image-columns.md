---
title: La gestion des colonnes Text et Image | Microsoft Docs
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 31ac0f9f4a234f26241a98e3d9f52333e19c919d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47598867"
---
# <a name="managing-text-and-image-columns"></a>Gestion des colonnes text et image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte**, **ntext**, et **image** données (également appelées en tant que données de type long) sont des caractères ou des types de données de chaîne binaire qui peuvent contenir des valeurs de données trop volumineuses pour tenir dans **char**, **varchar**, **binaire**, ou **varbinary** colonnes. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte** type de données correspond au type de données ODBC SQL_LONGVARCHAR ; **ntext** mappe SQL_WLONGVARCHAR et **image** mappe à SQL_LONGVARBINARY. Certains éléments de données, tels que les longs documents ou les images bitmaps volumineuses, peuvent être trop grands pour pouvoir être stockés raisonnablement en mémoire. Pour récupérer des données de type long à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les parties séquentielles, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client permet à une application appeler [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Pour envoyer des données de type long dans les parties séquentielles, l’application peut appeler [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). Les paramètres pour lesquels les données sont envoyées au moment de l'exécution sont connus comme paramètres de données en cours d'exécution.  
  
 Une application peut en fait écrire ou récupérer n’importe quel type de données (pas simplement long) avec **SQLPutData** ou **SQLGetData**, même si seul **caractère** et  **binaire** données peuvent être envoyées ou extraites à certains endroits. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il est généralement inutile d’utiliser **SQLPutData** ou **SQLGetData**. Il est beaucoup plus facile de lier la mémoire tampon unique au paramètre ou à la colonne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes texte et image liées et non liées](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifications enregistrées ou non enregistrées](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Colonnes text, ntext ou image de données en cours d’exécution](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
