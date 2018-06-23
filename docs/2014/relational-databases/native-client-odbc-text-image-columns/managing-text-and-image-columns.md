---
title: Gestion des colonnes Text et Image | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1316f093ac0d1f79c5155ae1be88df98f091bd8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152812"
---
# <a name="managing-text-and-image-columns"></a>Gestion des colonnes text et image
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte**, **ntext**, et **image** données (également appelées en tant que données de type long) sont des caractères ou des types de données de chaîne binaire qui peuvent contenir des valeurs de données trop volumineuses pour tenir dans **char**, **varchar**, **binaire**, ou **varbinary** colonnes. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte** type de données correspond au type de données ODBC SQL_LONGVARCHAR ; **ntext** est mappé avec SQL_WLONGVARCHAR et **image** avec SQL_LONGVARBINARY. Certains éléments de données, tels que les longs documents ou les images bitmaps volumineuses, peuvent être trop grands pour pouvoir être stockés raisonnablement en mémoire. Pour récupérer des données de type long à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les parties séquentielles, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client permet à une application d’appeler [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Pour envoyer des données de type long dans les parties séquentielles, l’application peut appeler [SQLPutData](../native-client-odbc-api/sqlputdata.md). Les paramètres pour lesquels les données sont envoyées au moment de l'exécution sont connus comme paramètres de données en cours d'exécution.  
  
 Une application peut réellement écrire ou extraire tout type de données (pas simplement long) avec **SQLPutData** ou **SQLGetData**, même si seules **caractère** et  **binaire** données peuvent être envoyées ou récupérées dans les parties. Toutefois, si les données sont assez petites pour tenir dans un tampon unique, il est généralement inutile d’utiliser **SQLPutData** ou **SQLGetData**. Il est beaucoup plus facile de lier la mémoire tampon unique au paramètre ou à la colonne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Colonnes texte et image liées et non liées](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifications enregistrées ou non enregistrées](logged-vs-unlogged-modifications.md)  
  
-   [Colonnes text, ntext ou image de données en cours d’exécution](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  