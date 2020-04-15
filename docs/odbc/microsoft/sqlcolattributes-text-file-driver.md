---
title: SQLColAttributes (Text File Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Text File Driver
ms.assetid: 132fd1c0-1921-4a7d-910e-aedf1bff5453
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3eafe02ba76dcaa6078abee862d743deb4765bdd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307920"
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes (pilote de fichier texte)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques au fichier texte. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Commentaires|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Pour les données LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE est la longueur maximale de la colonne, et non la longueur maximale de la colonne fois 2.|  
|SQL_OWNER_NAME|Une chaîne vide ("") est retournée dans cette colonne parce que le nom du propriétaire n’est pas pris en charge.|  
|SQL_QUALIFIER_NAME|Le chemin vers un répertoire est retourné.|  
|SQL_COLUMN_SEARCHABLE|Les colonnes LONGVARBINARY et LONGVARCHAR sont signalées comme SQL_UNSEARCHABLE.<br /><br /> Les types de données binaires et de caractères à longueur fixe et variable sont consultables, même si LONGVARBINARY et LONGVARCHAR ne le sont pas.|
