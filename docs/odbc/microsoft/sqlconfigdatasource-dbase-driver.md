---
title: SQLConfigDataSource (pilote dBASE) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 18c6721b4f34772e8c3cd8e4f515233f80566fb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283969"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (pilote dBASE)
> [!NOTE]  
>  Ce sujet fournit dBASE Des informations spécifiques au conducteur. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être : ASCII (la valeur par défaut) ou internationale.<br /><br /> Cela définit la même option que **Collating Sequence** dans la boîte de dialogue de configuration.|  
|DÉFAUTDIR|Le parcours du répertoire.|  
|DELETED|Pour le pilote DBASE, spécifiez si les lignes qui ont été marquées comme supprimées peuvent être récupérées ou positionnées. Si les lignes supprimées sont définies à 1, les lignes supprimées ne sont pas affichées; si définies à 0, les lignes supprimées sont traitées de la même façon que les lignes non supprimées.<br /><br /> Cela définit la même option que **Afficher les lignes supprimées** dans la boîte de dialogue de configuration.|  
|Description|Une description des données dans la source de données.<br /><br /> Cela définit la même option que **description** dans la boîte de dialogue de configuration.|  
|DRIVER|La spécification de chemin au conducteur DLL.|  
|DRIVERID (EN)|Une pièce d’identité pour le conducteur.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|FIL (EN)|Type de fichier dBase III, dBase IV, ou dBase 5|  
|PAGETIMEOUT|Spécifie la période de temps, en dixièmes de seconde, qu’une page (si elle n’est pas utilisée) reste dans le tampon avant d’être supprimée. La valeur par défaut est de 600 dixièmes de seconde (60 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que **Page Timeout** dans la boîte de dialogue de configuration.|  
|READONLY|VRAI pour faire lecture de fichier seulement; FALSE pour faire fichier non lu seulement.<br /><br /> Cela définit la même option que **Lire uniquement** dans la boîte de dialogue de configuration.|  
|STATISTICS|Pour le conducteur dBASE, détermine si les statistiques de taille de table sont approximatives. Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que Le compte de **ligne approximatif** dans la boîte de dialogue de configuration.|  
|Fils|Le nombre de fils d’arrière-plan pour le moteur à utiliser. Cette valeur est 3 et ne peut pas être changée.<br /><br /> Cela définit la même option que **Threads** dans la boîte de dialogue de configuration.|
