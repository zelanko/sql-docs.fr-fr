---
title: SQLNativeSql (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41f7617530f34d49852ca67db9f47cab94292385
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300569"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLNativeSql** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLNativeSql**, voir [SQLNativeSql Function](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Si le conducteur prend en charge cette fonction, la bibliothèque de curseur appelle **SQLNativeSql** dans le conducteur et lui transmet la déclaration SQL. Pour la mise à jour positionnée, la suppression positionnée et les instructions **SELECT FOR UPDATE,** la bibliothèque de curseur modifie l’instruction avant de la transmettre au conducteur.  
  
> [!NOTE]  
>  La bibliothèque de curseurs renvoie incorrectement SQLSTATE 34000 (nom de curseur invalide) si le nom du curseur est invalide dans une mise à jour ou une déclaration de suppression positionnée qui est adoptée dans *l’argument InStatementText* de **SQLNativeSql**. **SQLNativeSql** n’est pas destiné à retourner les erreurs de syntaxe, qui ne sont retournées qu’à la préparation ou à l’exécution des déclarations.
