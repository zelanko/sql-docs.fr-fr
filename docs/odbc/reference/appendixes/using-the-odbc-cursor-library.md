---
title: Utilisation de la Bibliothèque des curseurs de l’ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], using cursor library
- cursor library [ODBC], using cursor library
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c740ed78de51684eac38ad0c54ab2224986018d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301400"
---
# <a name="using-the-odbc-cursor-library"></a>Utilisation de la bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Pour utiliser la bibliothèque de curseurs ODBC, une application :  
  
1.  Appelle **SQLSetConnectAttr** avec un *attribut* de SQL_ATTR_ODBC_CURSORS pour spécifier comment la bibliothèque de curseur doit être utilisée avec une connexion particulière. La bibliothèque de curseurs peut toujours être utilisée (SQL_CUR_USE_ODBC), utilisée uniquement si le conducteur ne prend pas en charge les curseurs défilementables (SQL_CUR_USE_IF_NEEDED), ou n’est jamais utilisé (SQL_CUR_USE_DRIVER).  
  
2.  Appels **SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect** pour se connecter à la source de données.  
  
3.  Appelle **SQLSetStmtAttr** pour spécifier le type de curseur (SQL_ATTR_CURSOR_TYPE), la concurrence (SQL_ATTR_CONCURRENCY) et la taille de l’aviron (SQL_ATTR_ROW_ARRAY_SIZE). La bibliothèque de curseurs prend en charge les curseurs avant-seulement et statiques. Les curseurs avant-seulement doivent être lus uniquement, tandis que les curseurs statiques peuvent être lus uniquement ou peuvent utiliser un contrôle de concurrence optimiste comparant les valeurs.  
  
4.  Alloue une ou plusieurs tampons encastrés et appelle **SQLBindCol** une ou plusieurs fois pour lier ces tampons pour obtenir des colonnes définies.  
  
5.  Génère un résultat défini en exécutant une déclaration **SELECT** ou une procédure, ou en appelant une fonction de catalogue. Si l’application exécute des instructions de mise à jour positionnées, elle doit exécuter une déclaration **SELECT FOR UPDATE pour** générer l’ensemble de résultats.  
  
6.  Appelle **SQLFetch** ou **SQLFetchScroll** une ou plusieurs fois pour faire défiler l’ensemble de résultats.  
  
 L’application peut modifier les valeurs de données dans les tampons rowset. Pour rafraîchir les tampons encastrés avec les données du cache de la bibliothèque de curseur, une application appelle **SQLFetchScroll** avec *l’argument FetchOrientation* mis à SQL_FETCH_RELATIVE et *l’argument FetchOffset* réglé à 0.  
  
 Pour récupérer les données d’une colonne non liée, l’application appelle **SQLSetPos** pour positionner le curseur sur la ligne désirée. Il appelle ensuite **SQLGetData** pour récupérer les données.  
  
 Pour déterminer le nombre de lignes qui ont été récupérées à partir de la source de données, l’application appelle **SQLRowCount**.
