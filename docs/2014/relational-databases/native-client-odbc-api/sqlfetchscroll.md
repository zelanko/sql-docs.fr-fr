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
author: rothja
ms.author: jroth
ms.openlocfilehash: eecf9714a97577ff490b642cee5b9c380333e40b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022510"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  **SQLFetchScroll** retourne un ensemble de lignes de données à l'application. La taille de l'ensemble de lignes est définie à l'aide de [SQLSetStmtAttr](sqlsetstmtattr.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge toutes les instructions d'extraction définies (par exemple, SQL_FETCH_RELATIVE) avec les limitations suivantes :  
  
-   Si un curseur avant uniquement est défini pour l'instruction, SQL_FETCH_NEXT est requis et toute tentative d'extraction effectuée d'une autre manière retournera une erreur.  
  
-   SQL_FETCH_BOOKMARK est uniquement pris en charge pour les curseurs statiques et les curseurs de jeu de clés.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLFetchScroll des fonctionnalités de date et heure améliorées  
 Les valeurs de colonne de résultats de types date/heure sont converties comme décrit dans [conversions de SQL en C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Prise en charge par SQLFetchScroll des grands types CLR définis par l'utilisateur  
 **SQLFetchScroll** prend en charge les types CLR volumineux définis par l'utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFetchScroll, fonction](https://go.microsoft.com/fwlink/?LinkId=59343)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
