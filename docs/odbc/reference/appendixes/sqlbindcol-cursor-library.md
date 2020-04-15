---
title: SQLBindCol (Cursor Library) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c29909a96f147a0f5ebc2140a68072dfe544255
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305470"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLBindCol** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLBindCol**, voir [SQLBindCol Function](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Une application alloue un ou plusieurs tampons pour la bibliothèque de curseurs pour retourner le ramset actuel. Il appelle **SQLBindCol** une ou plusieurs fois pour lier ces tampons à l’ensemble de résultats.  
  
 Une application peut appeler **SQLBindCol** pour relire les colonnes de jeu de résultat après qu’il a appelé **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**, tant que le type de données C, la taille de la colonne, et les chiffres décimaux de la colonne liée restent les mêmes. L’application n’a pas besoin de fermer le curseur pour rebind colonnes à différentes adresses.  
  
 La bibliothèque de curseurs prend en charge la définition de l’attribut de l’SQL_ATTR_ROW_BIND_OFFSET_PTR’énoncé pour utiliser des décalages de liaison. (**SQLBindCol** n’a pas besoin d’être appelé pour que cette rébination se produise.) Si la bibliothèque de curseurs est utilisée avec un conducteur ODBC *3.x,* le décalage de liaison n’est pas utilisé lorsque **SQLFetch** est appelé. Le décalage de liaison est utilisé si **SQLFetch** est appelé lorsque la bibliothèque de curseur est utilisé avec un conducteur ODBC *2.x* parce que **SQLFetch** est ensuite cartographié à **SQLExtendedFetch**.  
  
 La bibliothèque de curseurs prend en charge l’appel **SQLBindCol** pour lier la colonne de signets.  
  
 Lorsque vous travaillez avec un conducteur ODBC *2.x,* la bibliothèque de curseurs retourne SQLSTATE HY090 (longueur de ficelle ou tampon invalide) lorsque **SQLBindCol** est appelé à définir la longueur tampon pour une colonne de signets à une valeur pas égale à 4. Lorsque vous travaillez avec un conducteur ODBC *3.x,* la bibliothèque de curseurs permet au tampon d’être n’importe quelle taille.
