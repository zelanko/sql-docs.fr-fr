---
title: SQLNativeSql (bibliothèque de curseurs) | Documents Microsoft
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
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2bd3fd6851cd3d59187a239d7d6aad2ffd269ac
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLNativeSql** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLNativeSql**, consultez [sqlnativesql, fonction](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Si le pilote prend en charge cette fonction, la bibliothèque de curseurs appelle **SQLNativeSql** dans le pilote et le passe à l’instruction SQL. Pour la mise à jour positionnée, suppression positionnée, et **sélectionner pour la mise à jour** instructions, la bibliothèque de curseurs modifie l’instruction avant de le transmettre au pilote.  
  
> [!NOTE]  
>  La bibliothèque de curseurs retourne incorrectement SQLSTATE 34000 (nom de curseur non valide) si le nom du curseur n’est pas valide dans une mise à jour positionnée ou d’une instruction delete qui est passée dans le *InStatementText* argument de **SQLNativeSql**. **SQLNativeSql** n’est pas destinée à retourner des erreurs de syntaxe, qui sont retournées uniquement lors de la préparation ou de l’exécution.
