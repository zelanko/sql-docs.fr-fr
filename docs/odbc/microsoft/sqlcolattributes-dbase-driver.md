---
title: SQLColAttributes (pilote dBASE) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66a37f3c9ceccdf3fb226ea423552886d36ed99f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67903970"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Commentaires|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Pour les données LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE est la longueur maximale de la colonne, et non la longueur maximale de la colonne fois 2.|  
|SQL_OWNER_NAME|Une chaîne vide ("") est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|SQL_QUALIFIER_NAME|Le chemin d’accès à un répertoire est retourné.|  
|SQL_COLUMN_SEARCHABLE|Les colonnes LONGVARBINARY et LONGVARCHAR sont signalées comme SQL_UNSEARCHABLE.<br /><br /> Les types de données binaires et de caractères de longueur fixe et de longueur variable peuvent faire l’objet d’une recherche, même si LONGVARBINARY et LONGVARCHAR ne le sont pas.|  
  
> [!NOTE]  
>  La liste ci-dessus n’est pas une liste complète des attributs retournés par **SQLColAttributes**.
