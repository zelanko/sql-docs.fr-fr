---
title: SQLConfigDataSource (pilote dBASE) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], dBASE Driver
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63d1951cfe835cbfca23ab366db2216215aa92c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631647"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations de dBASE spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le **SQLConfigDataSource** fonction qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être : ASCII (la valeur par défaut) ou International.<br /><br /> La même option est définie en tant que **séquence de classement** dans la boîte de dialogue d’installation.|  
|DEFAULTDIR|La spécification de chemin d’accès au répertoire.|  
|DELETED|Pour le pilote dBASE, spécifie si les lignes qui ont été marquées comme supprimées peuvent être récupérées ou positionnés sur. Si la valeur 1, les lignes supprimées n’est pas affichée ; Si la valeur 0, lignes supprimées sont traitées comme des lignes non supprimé.<br /><br /> La même option est définie en tant que **afficher les lignes supprimées** dans la boîte de dialogue d’installation.|  
|DESCRIPTION|Une description des données dans la source de données.<br /><br /> La même option est définie en tant que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|La spécification de chemin d’accès à la DLL du pilote.|  
|DRIVERID|Un ID d’entier pour le pilote.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|FIL|Fichier tapez dBase III, dBase IV ou dBase 5|  
|PAGETIMEOUT|Spécifie la période de temps, en dixièmes de seconde, une page (si non utilisé) reste dans la mémoire tampon avant d’être supprimés. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> La même option est définie en tant que **Page Timeout** dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier en lecture seule ; FALSE pour rendre le fichier pas en lecture seule.<br /><br /> La même option est définie en tant que **en lecture seule** dans la boîte de dialogue d’installation.|  
|STATISTICS|Pour le pilote dBASE, détermine si les statistiques de taille de table sont arrondies. Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> La même option est définie en tant que **nombre de lignes approximatif** dans la boîte de dialogue d’installation.|  
|THREADS|Le nombre de threads d’arrière-plan pour le moteur à utiliser. Cette valeur est 3 et ne peut pas être modifiée.<br /><br /> La même option est définie en tant que **Threads** dans la boîte de dialogue d’installation.|
