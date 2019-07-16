---
title: SQLColAttributes (pilote Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c78229da8a577670ba31ae82c679bfefbef4f80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903982"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations d’accès spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribute|Commentaires|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Pour les données LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE est la longueur maximale de la colonne, pas la longueur maximale de la colonne heures 2.|  
|SQL_OWNER_NAME|Une chaîne vide (" ») est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|SQL_QUALIFIER_NAME|Le chemin d’accès à un fichier de base de données est retournée.|  
|SQL_COLUMN_SEARCHABLE|Colonnes LONGVARBINARY et LONGVARCHAR sont signalés comme SQL_UNSEARCHABLE.<br /><br /> Binaire de longueur fixe et de longueur variable et les types de données caractères des recherches sont possibles, même si LONGVARBINARY et LONGVARCHAR ne sont pas.|  
  
> [!NOTE]  
>  La méthode ci-dessus n’est pas une liste complète des attributs retournés par **SQLColAttributes**.
