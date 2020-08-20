---
description: 'ODBC Jet : SQLConfigDataSource (pilote Excel)'
title: ODBC Jet SQLConfigDataSource (pilote Excel) | Microsoft Docs
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
ms.openlocfilehash: 61fcc1e7df00f14a7b92e294262b7806382a3d52
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500302"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet : SQLConfigDataSource (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|DBQ|Pour le pilote Microsoft Excel qui accède aux fichiers Microsoft Excel 5,0 ou version ultérieure, il s’agit du nom du fichier de classeur.<br /><br /> Cela définit la même option que **base de données** dans la boîte de dialogue installation.|  
|DEFAULTDIR|Spécification du chemin d’accès au répertoire.<br /><br /> Cela définit la même option que **Sélectionner le répertoire** ou **Sélectionner un classeur** dans la boîte de dialogue d’installation.|  
|Description|Description des données dans la source de données.<br /><br /> Cela définit la même option que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|Spécification du chemin d’accès à la DLL du pilote.|  
|DRIVERID|ID d’entier du pilote.<br /><br /> 534 (Microsoft Excel 3,0)<br /><br /> 278 (Microsoft Excel 4,0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL|Type de fichier, par exemple, Excel 3,0, Excel 4,0, Excel 5,0, Excel 7,0, Excel 97, Excel 2000 ou Excel 2003.|  
|FIRSTROWHASNAMES|Indique si les cellules de la première ligne de la plage contiennent les noms de colonnes de la table (1) ou non (0).|  
|MAXSCANROWS|Nombre de lignes à analyser lors de la définition du type de données d’une colonne en fonction des données existantes.<br /><br /> Vous pouvez entrer un nombre compris entre 1 et 16 pour les lignes à analyser. La valeur par défaut est 8. Si la valeur est 0, toutes les lignes sont analysées. (Un nombre en dehors de la limite renverra une erreur.)<br /><br /> Cela définit la même option que **lignes à analyser** dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier accessible en lecture seule ; FALSe pour que le fichier ne soit pas en lecture seule.<br /><br /> Cela permet de définir la même option en **lecture seule** dans la boîte de dialogue d’installation.|  
|THÈMES|Nombre de threads d’arrière-plan à utiliser par le moteur. Pour le pilote Microsoft Access, cette valeur est définie par défaut sur 3, mais peut être modifiée. Pour le dBASE, MicrosoftExceldriver cette valeur est 3 et ne peut pas être modifiée.<br /><br /> Cela définit la même option que les **Threads** dans la boîte de dialogue d’installation.|
