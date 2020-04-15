---
title: SQLConfigDataSource (Text File Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d2809f9b15dd6843e4404c7cf1887c3caa015a3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283919"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (pilote de fichier texte)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques au fichier texte. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|PERSONNAGESET|Pour le pilote de texte, OEM ou ANSI.|  
|COLNAMEHEADER|Pour le pilote de texte, indique si le premier enregistrement des données spécifiera les noms de colonne. SOIT VRAI, soit FALSE.|  
|DÉFAUTDIR|Le parcours du répertoire.|  
|Description|Une description des données dans la source de données.<br /><br /> Cela définit la même option que **description** dans la boîte de dialogue de configuration.|  
|DRIVER|La spécification de chemin au conducteur DLL.|  
|DRIVERID (EN)|Une pièce d’identité pour le conducteur. 27 (Texte)|  
|Extensions|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données.<br /><br /> Cela définit la même option que **la liste d’extensions** dans la boîte de dialogue de configuration.|  
|FIL (EN)|Texte de type fichier|  
|Filetype|Type de fichier pour le pilote de texte (Texte).|  
|FORMAT|Pour le pilote de texte, peut être FIXEDLENGTH, TABDELIMITED, CSVDELIMITED (par virgule), ou DELIMITED () (par le caractère spécial spécifié dans les parenthèses). Le personnage spécial est un personnage de longueur et peut être dans le format de caractère, décimale, ou hexadecimal.|  
|MAXSCANROWS (EN)|Nombre de lignes à numériser lors de la définition du type de données d’une colonne à partir des données existantes.<br /><br /> Pour le pilote textuel, vous pouvez entrer un numéro de 1 à 32767 pour le nombre de lignes à numériser; cependant, la valeur sera toujours par défaut à 25. (Un numéro en dehors de la limite retournera une erreur.)<br /><br /> Cela définit la même option que **Rows to Scan** dans la boîte de dialogue de configuration.|  
|READONLY|VRAI pour faire lecture de fichier seulement; FALSE pour faire fichier non lu seulement.<br /><br /> Cela définit la même option que **Lire uniquement** dans la boîte de dialogue de configuration.|
