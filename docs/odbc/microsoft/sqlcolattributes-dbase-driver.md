---
title: SQLColAttributes (dBASE Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLColAttributes
ms.assetid: ed44de2b-0b01-4dce-a340-f5eb3aac30b7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9e9d5adb75a99784d7244852bfda0499e481fc4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307950"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (pilote dBASE)
> [!NOTE]  
>  Ce sujet fournit dBASE Des informations spécifiques au conducteur. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Commentaires|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Pour les données LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE est la longueur maximale de la colonne, et non la longueur maximale de la colonne fois 2.|  
|SQL_OWNER_NAME|Une chaîne vide ("") est retournée dans cette colonne parce que le nom du propriétaire n’est pas pris en charge.|  
|SQL_QUALIFIER_NAME|Le chemin vers un répertoire est retourné.|  
|SQL_COLUMN_SEARCHABLE|Les colonnes LONGVARBINARY et LONGVARCHAR sont signalées comme SQL_UNSEARCHABLE.<br /><br /> Les types de données binaires et de caractères à longueur fixe et variable sont consultables, même si LONGVARBINARY et LONGVARCHAR ne le sont pas.|  
  
> [!NOTE]  
>  Ce qui précède n’est pas une liste complète des attributs retournés par **SQLColAttributes**.
