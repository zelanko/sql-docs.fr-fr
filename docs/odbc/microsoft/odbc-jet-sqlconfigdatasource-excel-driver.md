---
title: ODBC Jet SQLConfigDataSource (Excel Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Excel Driver
- Excel driver [ODBC], SqlConfigDataSource
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a76482acd1182d900336d7ac9826b16968e00caa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293009"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet : SQLConfigDataSource (pilote Excel)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Excel Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|DBQ|Pour le pilote Microsoft Excel lors de l’accès à microsoft Excel 5.0 ou plus tard fichiers, le nom du fichier de cahier de travail.<br /><br /> Cela définit la même option que **la base de données** dans la boîte de dialogue de configuration.|  
|DÉFAUTDIR|Le parcours du répertoire.<br /><br /> Cela définit la même option que **Select Directory** ou **Select Workbook** dans la boîte de dialogue de configuration.|  
|Description|Une description des données dans la source de données.<br /><br /> Cela définit la même option que **description** dans la boîte de dialogue de configuration.|  
|DRIVER|La spécification de chemin au conducteur DLL.|  
|DRIVERID (EN)|Une pièce d’identité pour le conducteur.<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL (EN)|Type de fichier, par exemple, Excel 3.0, Excel 4.0, Excel 5.0, Excel 7.0, Excel 97, Excel 2000 ou Excel 2003.|  
|PRÉNOMS|Indique si les cellules de la première rangée de la plage contiennent les noms de colonne pour la table (1) ou non (0).|  
|MAXSCANROWS (EN)|Nombre de lignes à numériser lors de la définition du type de données d’une colonne à partir des données existantes.<br /><br /> Un nombre de 1 à 16 peut être entré pour que les lignes puissent être numérisées. La valeur par défaut à 8; s’il est réglé à 0, toutes les lignes sont numérisées. (Un numéro en dehors de la limite retournera une erreur.)<br /><br /> Cela définit la même option que **Rows to Scan** dans la boîte de dialogue de configuration.|  
|READONLY|VRAI pour faire lecture de fichier seulement; FALSE pour faire fichier non lu seulement.<br /><br /> Cela définit la même option que **Lire uniquement** dans la boîte de dialogue de configuration.|  
|Fils|Le nombre de fils d’arrière-plan pour le moteur à utiliser. Pour le pilote Microsoft Access, cette valeur est par défaut à 3, mais peut être modifiée. Pour le dBASE, MicrosoftExceldriver cette valeur est 3, et ne peut pas être changé.<br /><br /> Cela définit la même option que **Threads** dans la boîte de dialogue de configuration.|
