---
title: Entrées de Registre (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de287802693adb18e39509fdc0e7577d05984949
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316825"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Entrées du Registre (pilote ODBC Visual FoxPro)
Lorsque vous installez le pilote ODBC Visual FoxPro, le programme d’installation met à jour le Registre de votre système, dans la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, pour ajouter une nouvelle clé appelée pilote Microsoft Visual FoxPro. Sous cette clé, les valeurs décrites dans le tableau suivant sont ajoutés.  
  
|Nom de valeur|Type de valeur|Value|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|« YYN »|  
|Pilote|REG_SZ|Chemin d’accès système au fichier vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|« *.dbf,\*.cdx,\*.fpt »|  
|FileUsage|REG_SZ|"1"|  
|Installation|REG_SZ|Chemin d’accès système au fichier vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 Le programme d’installation ajoute également la clé « Visual FoxPro Files », qui représente le pilote de Visual FoxPro par défaut, à la clé de HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini de votre système. Sous cette clé, le programme d’installation ajoute les valeurs décrites dans le tableau suivant.  
  
|Nom de valeur|Type de valeur|Value|  
|----------------|----------------|-----------|  
|Pilote|REG_SZ|Chemin d’accès système au fichier vfpodbc.dll|  
  
 Chaque fois que vous ajoutez une source de données ODBC Visual FoxPro à votre configuration ODBC, une nouvelle clé est ajoutée pour ce nom de source de données. Les valeurs pour la source de données correspondent aux valeurs que vous définissez dans le **d’installation de ODBC Visual FoxPro** boîte de dialogue, comme indiqué dans le tableau suivant.  
  
|Nom de la valeur (mot clé)|Type de valeur|Value|  
|----------------------------|----------------|-----------|  
|Copies assemblées|REG_SQ|Tout pris en charge l’ordre de tri|  
|Description|REG_SZ|Description de l’utilisateur de la source de données|  
|Pilote||Chemin d’accès système au fichier vfpodbc.dll|  
|Exclusive||Oui ou Non|  
|BackgroundFetch||Oui ou Non|  
|SourceDB|REG_SZ|Chemin d’accès. Fichier DBC|  
|SourceType|REG_SZ|« DBC » ou « DBF »|  
  
 Vous ne devez accéder ces informations directement ; toute l’administration du Registre est gérée par l’administrateur ODBC lorsque vous ajoutez, modifiez ou supprimez une source de données.  
  
 Vous pouvez utiliser certains de ces mots clés et les valeurs en tant que paramètres dans le [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) fonction API ODBC.
