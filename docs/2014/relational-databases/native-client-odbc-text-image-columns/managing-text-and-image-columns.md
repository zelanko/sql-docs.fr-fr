---
title: La gestion des colonnes Text et Image | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0989157eabe987ae8d1bdac22deb25ad2c6d028
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426988"
---
# <a name="managing-text-and-image-columns"></a>Gestion des colonnes text et image
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte**, **ntext**, et **image** données (également appelées en tant que données de type long) sont des caractères ou des types de données de chaîne binaire qui peuvent contenir des valeurs de données trop volumineuses pour tenir dans **char**, **varchar**, **binaire**, ou **varbinary** colonnes. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte** type de données correspond au type de données ODBC SQL_LONGVARCHAR ; **ntext** mappe SQL_WLONGVARCHAR et **image** mappe à SQL_LONGVARBINARY. Certains éléments de données, tels que les longs documents ou les images bitmaps volumineuses, peuvent être trop grands pour pouvoir être stockés raisonnablement en mémoire. Pour récupérer des données de type long à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les parties séquentielles, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client permet à une application appeler [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Pour envoyer des données de type long dans les parties séquentielles, l’application peut appeler [SQLPutData](../native-client-odbc-api/sqlputdata.md). Les paramètres pour lesquels les données sont envoyées au moment de l'exécution sont connus comme paramètres de données en cours d'exécution.  
  
 Une application peut en fait écrire ou récupérer n’importe quel type de données (pas simplement long) avec **SQLPutData** ou **SQLGetData**, même si seul **caractère** et  **binaire** données peuvent être envoyées ou extraites à certains endroits. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il est généralement inutile d’utiliser **SQLPutData** ou **SQLGetData**. Il est beaucoup plus facile de lier la mémoire tampon unique au paramètre ou à la colonne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes texte et image liées et non liées](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifications enregistrées ou non enregistrées](logged-vs-unlogged-modifications.md)  
  
-   [Colonnes text, ntext ou image de données en cours d’exécution](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
