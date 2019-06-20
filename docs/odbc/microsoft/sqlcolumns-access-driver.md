---
title: SQLColumns (pilote Access) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0e0977aebfe16b9274df8e93260eb98a24742cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666106"
---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations d’accès spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin d’accès à un fichier de base de données est retournée.|  
|TABLE_OWNER|Valeur NULL est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|NULLABLE|SQL_NO_NULLS est retournée pour les colonnes qui participent à dans une clé primaire ou un index unique.|
