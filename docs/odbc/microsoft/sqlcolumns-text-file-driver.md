---
title: SQLColumns (pilote du fichier texte) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5f64eb930bad551953c4a70b2d839924d127caf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (pilote du fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin d’accès à un répertoire est retournée.|  
|TABLE_OWNER|Valeur NULL est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|NULLABLE|SQL_NO_NULLS est retourné pour les colonnes qui participent dans une clé primaire ou un index unique.|
