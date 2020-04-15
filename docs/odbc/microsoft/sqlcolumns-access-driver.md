---
title: SQLColumns (Access Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Access Driver
- Access driver [ODBC], SQLColumns
ms.assetid: 1eac255c-6110-4805-a1bc-feee1eec35d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7031e9eebbb1ffae045598863d22399147503c88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307900"
---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin vers un fichier de base de données est retourné.|  
|TABLE_OWNER|NULL est retourné dans cette colonne parce que le nom du propriétaire n’est pas pris en charge.|  
|NULLABLE|SQL_NO_NULLS est retourné pour les colonnes qui participent à une clé primaire ou un index unique.|
