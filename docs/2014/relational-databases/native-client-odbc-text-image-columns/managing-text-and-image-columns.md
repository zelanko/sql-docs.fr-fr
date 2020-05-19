---
title: Gestion des colonnes text et image | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e6f790a82b45f9a74318a8ec46ef1e4f2a283edb
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709287"
---
# <a name="managing-text-and-image-columns"></a>Gestion des colonnes text et image
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les données **Text**, **ntext**et **image** (également appelées données de type long) sont des types de données de chaîne de caractères ou binaires qui peuvent contenir des valeurs de données trop grandes pour tenir dans des colonnes **char**, **varchar**, **Binary**ou **varbinary** . Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données **Text** est mappé sur le type de données SQL_LONGVARCHAR ODBC ; **ntext** est mappé à SQL_WLONGVARCHAR ; et **images** est mappé à SQL_LONGVARBINARY. Certains éléments de données, tels que les longs documents ou les images bitmaps volumineuses, peuvent être trop grands pour pouvoir être stockés raisonnablement en mémoire. Pour récupérer des données de type long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans des parties séquentielles, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client permet à une application d’appeler [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Pour envoyer des données de type long dans des parties séquentielles, l’application peut appeler [SQLPutData](../native-client-odbc-api/sqlputdata.md). Les paramètres pour lesquels les données sont envoyées au moment de l'exécution sont connus comme paramètres de données en cours d'exécution.  
  
 Une application peut en fait écrire ou récupérer n’importe quel type de données (pas seulement des données longues) avec **SQLPutData** ou **SQLGetData**, bien que seules les données de type **caractère** et **binaire** puissent être envoyées ou récupérées dans des parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData** ou **SQLGetData**. Il est beaucoup plus facile de lier la mémoire tampon unique au paramètre ou à la colonne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes de texte et d'image liées et non liées](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifications enregistrées ou non enregistrées](logged-vs-unlogged-modifications.md)  
  
-   [Colonnes text, ntext ou image de données en cours d’exécution](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
