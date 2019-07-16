---
title: SQLFetch (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2cb829f065421a13d3c7df06c670808bc3d9d77c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064433"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLFetch** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLFetch**, consultez [SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLFetch** ne peut pas être combiné avec les appels à **SQLFetchScroll** ou **SQLExtendedFetch**.  
  
 Si **SQLFetch** est appelée avec SQL_ATTR_ROW_ARRAY_SIZE définie sur une valeur supérieure à 1, la bibliothèque de curseurs transmettra l’appel au pilote. Si le pilote est une API ODBC 2. *x* pilote, la taille de l’ensemble de lignes sera ignorée et l’appel à **SQLFetch** renvoie une ligne unique de données.  
  
 Si la bibliothèque de curseurs est utilisée avec un ODBC 2. *x* pilote, une liaison de décalage (comme défini par l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR) n’est pas utilisé lorsque **SQLFetch** est appelée.  
  
 Lors du chargement de la bibliothèque de curseurs, une application ne peut pas appeler **SQLFetch** pour extraire des colonnes de signet. La bibliothèque de curseurs passe l’appel à **SQLFetch** via le pilote, mais la fonction appels à activer les signets et lier la colonne de signet sont interceptés par la bibliothèque de curseurs.
