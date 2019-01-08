---
title: SQLFetchScroll | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c9614a71c0015d17178a57d33c5fd0d9b62433c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358851"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  **SQLFetchScroll** retourne un ensemble de lignes de données à l'application. La taille de l'ensemble de lignes est définie à l'aide de [SQLSetStmtAttr](sqlsetstmtattr.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge toutes les instructions d'extraction définies (par exemple, SQL_FETCH_RELATIVE) avec les limitations suivantes :  
  
-   Si un curseur avant uniquement est défini pour l'instruction, SQL_FETCH_NEXT est requis et toute tentative d'extraction effectuée d'une autre manière retournera une erreur.  
  
-   SQL_FETCH_BOOKMARK est uniquement pris en charge pour les curseurs statiques et les curseurs de jeu de clés.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLFetchScroll des fonctionnalités de date et heure améliorées  
 Résultat des valeurs de colonnes de types date/heure sont converties comme décrit dans [Conversions à partir de SQL vers C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Pour plus d’informations, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Prise en charge par SQLFetchScroll des grands types CLR définis par l'utilisateur  
 **SQLFetchScroll** prend en charge les types CLR volumineux définis par l'utilisateur (UDT). Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLFetchScroll](https://go.microsoft.com/fwlink/?LinkId=59343)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
