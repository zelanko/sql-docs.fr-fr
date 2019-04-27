---
title: SQLGetInfo (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Cursor Library
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 443f8e36e4b9f537f33774a97b6d2fa0659e620d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62751204"
---
# <a name="sqlgetinfo-cursor-library"></a>SQLGetInfo (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLGetInfo** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLGetInfo**, consultez [SQLGetInfo, fonction](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 La bibliothèque de curseurs retourne des valeurs pour les valeurs suivantes de *InfoType* (&#124; représente une opération OR au niveau du bit) ; pour toutes les autres valeurs de *InfoType*, il appelle **SQLGetInfo** dans le pilote.  
  
|*InfoType*|Valeur renvoyée|  
|----------------|--------------------|  
|SQL_BOOKMARK_PERSISTENCE|SQL_BP_SCROLL|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|0|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|0|  
|SQL_FETCH_DIRECTION[1]|SQL_FD_FETCH_ABSOLUTE &#124; SQL_FD_FETCH_FIRST &#124; SQL_FD_FETCH_LAST &#124; SQL_FD_FETCH_NEXT &#124; SQL_FD_FETCH_PRIOR &#124; SQL_FD_FETCH_RELATIVE &#124; SQL_FD_FETCH_BOOKMARK|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &AMP;#124; SQL_CA1_ABSOLUTE &AMP;#124; SQL_CA1_RELATIVE &AMP;#124; SQL_CA1_LOCK_NO_CHANGE &AMP;#124; SQL_CA1_POS_POSITION &AMP;#124; SQL_CA1_POSITIONED_DELETE &AMP;#124; SQL_CA1_POSITIONED_UPDATE &AMP;#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &#124; SQL_CA2_OPT_VALUES_CONCURRENCY &#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_GETDATA_EXTENSIONS|SQL_GD_BLOCK &#124; toutes les valeurs renvoyées par le pilote **Remarque :**  Lorsque les données sont récupérées avec **SQLFetchScroll**, **SQLGetData** prend en charge la fonctionnalité spécifiée avec les masques de bits SQL_GD_ANY_COLUMN et SQL_GD_BOUND.|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1|0|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2|0|  
|SQL_LOCK_TYPES[1]|SQL_LCK_NO_CHANGE|  
|SQL_STATIC_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &AMP;#124; SQL_CA1_ABSOLUTE &AMP;#124; SQL_CA1_RELATIVE &AMP;#124; SQL_CA1_BOOKMARK &AMP;#124; SQL_CA1_LOCK_NO_CHANGE &AMP;#124; SQL_CA1_POS_POSITION &AMP;#124; SQL_CA1_POSITIONED_DELETE &AMP;#124; SQL_CA1_POSITIONED_UPDATE &AMP;#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_STATIC_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &#124; SQL_CA2_OPT_VALUES_ CONCURRENCY &#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_POS_OPERATIONS[1]|SQL_POS_POSITION|  
|SQL_POSITIONED_STATEMENTS[1]|SQL_PS_POSITIONED_DELETE &#124; SQL_PS_POSITIONED_UPDATE &#124; SQL_PS_SELECT_FOR_UPDATE|  
|SQL_ROW_UPDATES|"Y"|  
|SQL_SCROLL_CONCURRENCY[1]|SQL_SCCO_READ_ONLY &#124; SQL_SCCO_OPT_VALUES|  
|SQL_SCROLL_OPTIONS|SQL_SO_FORWARD_ONLY &#124; SQL_SO_STATIC|  
|SQL_STATIC_SENSITIVITY[1]|SQL_SS_UPDATES|  
  
 [1] utilisé uniquement lorsque la bibliothèque de curseurs est utilisée avec un pilote de 2.x ODBC.  
  
> [!IMPORTANT]  
>  La bibliothèque de curseurs implémente le comportement du curseur même lorsque les transactions sont validées ou annulées en tant que la source de données. Autrement dit, la validation ou la restauration d’une transaction, soit en appelant **SQLEndTran** ou à l’aide de l’attribut de connexion SQL_ATTR_AUTOCOMMIT peut provoquer la source de données supprimer les plans d’accès et de fermer les curseurs pour toutes les instructions sur une connexion. Pour plus d’informations, consultez les types d’informations SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).
