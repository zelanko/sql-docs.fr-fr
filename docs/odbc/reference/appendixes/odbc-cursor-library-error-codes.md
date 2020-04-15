---
title: Codes d’erreur de la bibliothèque de cursor d’ODBC (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c263ce53c41546e63dc2a830d3db3b903e2e3515
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301430"
---
# <a name="odbc-cursor-library-error-codes"></a>Codes d’erreur de la bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Microsoft Data Access Component. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt des curseurs de conducteur et de serveur.  
  
 La bibliothèque de curseurs ODBC renvoie les SQLSTATEs suivants en plus de celles énumérées dans [ODBC API Reference](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne commande pas de dossiers d’état; le Driver Manager et ODBC 3. *x* les conducteurs sont responsables de la commande des dossiers d’état.  
  
|SQLSTATE|Description|Peut être retourné de|  
|--------------|-----------------|--------------------------|  
|01000|Le curseur n’est pas updatable.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Bibliothèque de curseur non utilisée. La charge a échoué.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Bibliothèque de curseur non utilisée. Soutien insuffisant du conducteur.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Bibliothèque de curseur non utilisée. Décalage de version avec Driver Manager.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Le conducteur est revenu SQL_SUCCESS_WITH_INFO. Le message d’avertissement a été perdu.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Erreur générale : Impossible de créer un tampon de fichier.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Erreur générale : Impossible de lire à partir du tampon de fichier.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Erreur générale : Impossible d’écrire pour déposer un tampon.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Erreur générale : Impossible de fermer ou de supprimer le tampon de fichier.|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001 (en)|La demande positionnée ne peut pas être effectuée parce qu’aucune colonne consultable n’était liée.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002 (EN)|La demande positionnée n’a pas pu être effectuée parce que l’ensemble de résultat a été créé par une condition de jointure.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003 (en)|Le tampon lié dépasse la taille maximale du segment.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004 (en)|L’ensemble de résultats n’a pas été généré par une déclaration **SELECT.**|**SQLGetData**|  
|SL005 (en)|**L’instruction SELECT** contient une clause GROUPE BY.|**SQLGetData**|  
|SL006 (EN)|Les tableaux de paramètres ne sont pas pris en charge par les demandes positionnées.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008 (EN)|**SQLGetData** n’est pas autorisé sur un curseur avant seulement (non emballé).|**SQLGetData**|  
|SL009|Aucune colonne n’était liée avant d’appeler **SQLFetch** ou **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** est retourné SQL_ERROR lors d’une tentative de se lier à un tampon interne.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011 (en)|L’option d’instruction n’est valable qu’après avoir appelé **SQLFetch** ou **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Les fixations de déclaration ne peuvent pas être modifiées pendant qu’un curseur est ouvert.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Une demande positionnée a été émise et tous les champs de comptage des colonnes n’ont pas été tamponnés.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** et **SQLFetchScroll** ne peuvent pas être mélangés.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
