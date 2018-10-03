---
title: 'ODBC Jet : SQLConfigDataSource (pilote Excel) | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbad3b1e6dda82a9f9fc584683e53f8e2a109cca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715387"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet : SQLConfigDataSource (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le **SQLConfigDataSource** fonction qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|DBQ|Pour le pilote Microsoft Excel lorsque vous accédez à Microsoft Excel 5.0 ou ultérieurement les fichiers, le nom du fichier de classeur.<br /><br /> La même option est définie en tant que **base de données** dans la boîte de dialogue d’installation.|  
|DEFAULTDIR|La spécification de chemin d’accès au répertoire.<br /><br /> La même option est définie en tant que **sélectionner un répertoire** ou **Sélectionner classeur** dans la boîte de dialogue d’installation.|  
|DESCRIPTION|Une description des données dans la source de données.<br /><br /> La même option est définie en tant que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|La spécification de chemin d’accès à la DLL du pilote.|  
|DRIVERID|Un ID d’entier pour le pilote.<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL|Fichier de type, par exemple, Excel 3.0, 4.0 d’Excel, Excel 5.0, 7.0 d’Excel, Excel 97, Excel 2000 ou Excel 2003.|  
|FIRSTROWHASNAMES|Indique si les cellules de la première ligne de la plage contiennent les noms de colonnes pour la table (1) ou non (0).|  
|MAXSCANROWS|Le nombre de lignes à analyser lors de la définition de type de données d’une colonne en fonction des données existantes.<br /><br /> Nombre compris entre 1 et 16 pouvant être entré pour les lignes à balayer. La valeur par défaut est 8 ; Si elle est définie sur 0, toutes les lignes sont analysées. (Un nombre en dehors de la limite retournera une erreur).<br /><br /> La même option est définie en tant que **lignes à balayer** dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier en lecture seule ; FALSE pour rendre le fichier pas en lecture seule.<br /><br /> La même option est définie en tant que **en lecture seule** dans la boîte de dialogue d’installation.|  
|THREADS|Le nombre de threads d’arrière-plan pour le moteur à utiliser. Pour le pilote Microsoft Access, cette valeur par défaut est 3, mais peut être modifiée. Pour dBASE, MicrosoftExceldriver cette valeur est 3 et ne peut pas être modifié.<br /><br /> La même option est définie en tant que **Threads** dans la boîte de dialogue d’installation.|
