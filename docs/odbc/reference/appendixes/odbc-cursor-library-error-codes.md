---
title: Codes d’erreur bibliothèque curseur ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1fb077261eda4b2e013abd6d87e894637a29216a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691127"
---
# <a name="odbc-cursor-library-error-codes"></a>Codes d’erreur de la bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Microsoft Data Access Component. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez les curseurs de pilote et du serveur.  
  
 La bibliothèque de curseurs ODBC retourne le SQLSTATE suivants en plus de ceux répertoriés dans [ODBC API Reference](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne trie pas les enregistrements d’état ; le Gestionnaire de pilotes et les ODBC 3. *x* pilotes sont responsables de classement des enregistrements d’état.  
  
|SQLSTATE|Description|Peut être retourné à partir de|  
|--------------|-----------------|--------------------------|  
|01000|Curseur n’est pas modifiable.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Bibliothèque de curseurs ne pas utilisé. Échec du chargement.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Bibliothèque de curseurs ne pas utilisé. Prise en charge de pilote insuffisante.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Bibliothèque de curseurs ne pas utilisé. Incompatibilité de version avec le Gestionnaire de pilotes.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Pilote a retourné SQL_SUCCESS_WITH_INFO. Le message d’avertissement a été perdu.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Erreur générale : Impossible de créer la mémoire tampon de fichier.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Erreur générale : Impossible de lire à partir de la mémoire tampon de fichier.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Erreur générale : Impossible d’écrire dans la mémoire tampon de fichier.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Erreur générale : Impossible de fermer ou supprimer la mémoire tampon de fichier.|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|Requête positionnée n’est pas possible, car aucune colonne de recherche ont été lié.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Requête positionnée n’a pas pu être effectuée, car le jeu de résultats a été créé par une condition de jointure.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Mémoire tampon dépendante dépasse la taille de segment maximale.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Jeu de résultats n’a pas été généré par un **sélectionnez** instruction.|**SQLGetData**|  
|SL005|**Sélectionnez** instruction contient une clause GROUP BY.|**SQLGetData**|  
|SL006|Tableaux de paramètres ne sont pas pris en charge avec des requêtes positionnées.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** n’est pas autorisée sur un curseur en avant uniquement (classe).|**SQLGetData**|  
|SL009|Aucune colonne n’était liées avant d’appeler **SQLFetch** ou **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** renvoyé SQL_ERROR lors d’une tentative pour lier à une mémoire tampon interne.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|L’option d’instruction est valide uniquement après avoir appelé **SQLFetch** ou **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Liaisons de l’instruction ne peuvent pas être modifiés lorsqu’un curseur est ouvert.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Une requête positionnée a été émise et tous les champs de nombre de colonnes ont été mis en mémoire tampon.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** et **SQLFetchScroll** ne peuvent pas être combinés.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
