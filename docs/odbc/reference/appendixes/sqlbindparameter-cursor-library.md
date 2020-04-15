---
title: SQLBindParameter (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55708cc5192fb40149d6db7710f6ee638c4880d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305427"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLBindParameter** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLBindParameter**, voir [SQLBindParameter Function](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Une application peut appeler **SQLBindParameter** pour rebiner les paramètres, tant que le type de données C, la taille de la colonne et les chiffres décimaux de la colonne liée restent les mêmes.  
  
 La bibliothèque de curseurs prend en charge la définition de l’attribut de l’SQL_ATTR_ROW_BIND_OFFSET_PTR’énoncé pour utiliser des décalages de liaison. (**SQLBindParameter** n’a pas besoin d’être appelé pour que cette rebinding se produise.)  
  
 La bibliothèque de curseurs prend en charge les paramètres contraignants de données à l’exécution.
