---
title: SQLColumns (Text File Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78c2e20f12dedf399ab36dd908f83aa93bebffc4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307864"
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (pilote de fichier texte)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques au fichier texte. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin vers un répertoire est retourné.|  
|TABLE_OWNER|NULL est retourné dans cette colonne parce que le nom du propriétaire n’est pas pris en charge.|  
|NULLABLE|SQL_NO_NULLS est retourné pour les colonnes qui participent à une clé primaire ou un index unique.|
