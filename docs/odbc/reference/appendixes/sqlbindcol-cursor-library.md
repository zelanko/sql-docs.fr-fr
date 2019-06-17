---
title: SQLBindCol (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e9e1018754977ee73ecdc21db30b3d8c2aae8b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199686"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLBindCol** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLBindCol**, consultez [SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Une application alloue un ou plusieurs tampons pour retourner l’ensemble de lignes en cours dans la bibliothèque de curseurs. Il appelle **SQLBindCol** une ou plusieurs fois pour lier ces mémoires tampons pour le jeu de résultats.  
  
 Une application peut appeler **SQLBindCol** obligent le résultat à définie les colonnes après l’appel **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**, à condition que le type de données C, taille de colonne et les chiffres décimaux de la colonne liée restent les mêmes. L’application ne doive pas fermer le curseur pour relier les colonnes à des adresses différentes.  
  
 La bibliothèque de curseurs prend en charge la définition de l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR à utiliser les décalages de liaison. (**SQLBindCol** ne devra pas être appelée pour cette nouvelle liaison doit avoir lieu.) Si la bibliothèque de curseurs est utilisée avec un ODBC 3 *.x* pilote, le décalage de la liaison n’est pas utilisé lorsque **SQLFetch** est appelée. Le décalage de la liaison est utilisé si **SQLFetch** est appelée lorsque la bibliothèque de curseurs est utilisée avec un ODBC 2. *x* pilote car **SQLFetch** est ensuite mappé à **SQLExtendedFetch**.  
  
 La bibliothèque de curseurs prend en charge l’appel **SQLBindCol** pour lier la colonne de signet.  
  
 Lorsque vous travaillez avec un ODBC 2. *x* pilote, la bibliothèque de curseurs retourne SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide) lorsque **SQLBindCol** est appelée pour définir la longueur du tampon pour une colonne de signet sur une valeur non égale à 4. Lorsque vous travaillez avec un ODBC 3 *.x* pilote, la bibliothèque de curseurs permet d’être n’importe quelle taille de la mémoire tampon.
