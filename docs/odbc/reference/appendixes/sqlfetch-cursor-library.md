---
title: SQLFetch (bibliothèque de curseurs) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 05bfa99a97afa812928e91b7f0a77ced1eb4d1eb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLFetch** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLFetch**, consultez [fonction SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLFetch** ne peut pas être combiné avec des appels vers **SQLFetchScroll** ou **SQLExtendedFetch**.  
  
 Si **SQLFetch** est appelée avec SQL_ATTR_ROW_ARRAY_SIZE défini sur une valeur supérieure à 1, la bibliothèque de curseurs passe l’appel au pilote. Si le pilote est une API ODBC 2. *x* pilote, la taille de l’ensemble de lignes sera ignorée et l’appel à **SQLFetch** renvoie une ligne unique de données.  
  
 Si la bibliothèque de curseurs est utilisée avec une API ODBC 2. *x* pilote, une liaison de décalage (comme défini par l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR) n’est pas utilisée lorsque **SQLFetch** est appelée.  
  
 Lors du chargée de la bibliothèque de curseurs, une application ne peut pas appeler **SQLFetch** pour extraire des colonnes de signet. La bibliothèque de curseurs passe l’appel à **SQLFetch** via le pilote, mais la fonction appelle pour activer des signets et lier la colonne de signet est interceptés par la bibliothèque de curseurs.
