---
description: Entrées du Registre (pilote ODBC Visual FoxPro)
title: Entrées de Registre (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc4c5d617590e6435d99756b159c6049551d2d69
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340345"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Entrées du Registre (pilote ODBC Visual FoxPro)
Lorsque vous installez le pilote ODBC Visual FoxPro, le programme d’installation met à jour le registre de votre système, dans la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, pour ajouter une nouvelle clé nommée Microsoft Visual FoxPro Driver. Sous cette clé, les valeurs décrites dans le tableau suivant sont ajoutées.  
  
|Nom de la valeur|Type de valeur|Valeur|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Pilote|REG_SZ|Chemin d’accès système au fichier vfpodbc.dll|  
|DriverODBCVer|REG_SZ|« 02,50 »|  
|FileExtns|REG_SZ|"*. DBF, \* . CDX, \* . FPT"|  
|FileUsage|REG_SZ|"1"|  
|Programme d’installation|REG_SZ|Chemin d’accès système au fichier vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 Le programme d’installation ajoute également la clé « fichiers Visual FoxPro », représentant le pilote Visual FoxPro par défaut, à la clé de HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini de votre système. Sous cette clé, le programme d’installation ajoute les valeurs décrites dans le tableau suivant.  
  
|Nom de la valeur|Type de valeur|Valeur|  
|----------------|----------------|-----------|  
|Pilote|REG_SZ|Chemin d’accès système au fichier vfpodbc.dll|  
  
 Chaque fois que vous ajoutez une source de données ODBC Visual FoxPro à votre configuration ODBC, une nouvelle clé est ajoutée pour ce nom de source de données. Les valeurs de la source de données correspondent aux valeurs que vous définissez dans la boîte de dialogue **installation de ODBC Visual FoxPro** , comme indiqué dans le tableau suivant.  
  
|Nom de la valeur (mot clé)|Type de valeur|Valeur|  
|----------------------------|----------------|-----------|  
|Copies assemblées|REG_SQ|Toutes les séquences de classement prises en charge|  
|Description|REG_SZ|Description de l’utilisateur de la source de données|  
|Pilote||Chemin d’accès système au fichier vfpodbc.dll|  
|Exclusif||Oui ou Non|  
|BackgroundFetch||Oui ou Non|  
|SourceDB|REG_SZ|Chemin d’accès à. Fichier DBC|  
|SourceType|REG_SZ|« DBC » ou « DBF »|  
  
 Vous ne devez pas accéder directement à ces informations ; toute administration du Registre est gérée par l’administrateur ODBC lorsque vous ajoutez, modifiez ou supprimez une source de données.  
  
 Vous pouvez utiliser certains de ces mots clés et valeurs comme paramètres dans la fonction API ODBC [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) .
