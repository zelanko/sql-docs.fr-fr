---
title: SQLFetch (Cursor Library) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bee83ccb5497888b57a45673599af6b92931a704
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298719"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLFetch** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLFetch**, voir [SQLFetch Function](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLFetch** ne peuvent pas être mélangés avec des appels à **SQLFetchScroll** ou **SQLExtendedFetch**.  
  
 Si **SQLFetch** est appelé avec SQL_ATTR_ROW_ARRAY_SIZE réglé à une valeur supérieure à 1, la bibliothèque de curseur passera l’appel au conducteur. Si le conducteur est un ODBC 2. *x* conducteur, la taille de l’aviron sera ignorée et l’appel à **SQLFetch** retournera une seule rangée de données.  
  
 Si la bibliothèque de curseurs est utilisée avec un ODBC 2. *x* conducteur, un décalage de liaison (tel que défini par l’attribut de déclaration SQL_ATTR_ROW_BIND_OFFSET_PTR) n’est pas utilisé lorsque **SQLFetch** est appelé.  
  
 Lorsque la bibliothèque de curseurs est chargée, une application ne peut pas appeler **SQLFetch** pour aller chercher des colonnes de signets. La bibliothèque de curseurs passe l’appel à **SQLFetch** jusqu’au conducteur, mais les appels de fonction pour activer les signets et lier la colonne de signets sont interceptés par la bibliothèque de curseurs.
