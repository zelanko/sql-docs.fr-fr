---
title: SQLDriverConnect (Text File Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2768669b7dbb2066de0acedd5711911be0eac8fa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307100"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (pilote de fichier texte)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques au fichier texte. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes: **DSN**, **DBQ**, et **FIL**.  
  
 Le tableau suivant affiche les mots clés minimums requis pour se connecter à chaque pilote, et fournit un exemple de mots clés / paires de valeur utilisés avec **SQLDriverConnect**. Pour une liste complète des valeurs DRIVERID, voir [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote textuel, le conducteur se connectera à l’annuaire actuel.  
  
|Pilote|Mots-clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Texte|Pilote|Pilote de texte Microsoft Driver (.txt;\*. csv)MD; DefaultDir-c: 'temp'|
