---
title: Inscriptions au registre (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.openlocfilehash: bd2d419a94c45a872789e095b014159b41d7c217
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304836"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Entrées du Registre (pilote ODBC Visual FoxPro)
Lorsque vous installez le visual FoxPro ODBC Driver, le programme d’installation met à jour le registre de votre système, dans la clé de registre HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCInst.ini, pour ajouter une nouvelle clé appelée Microsoft Visual FoxPro Driver. En vertu de cette clé, les valeurs décrites dans le tableau suivant sont ajoutées.  
  
|Nom de la valeur|Type de valeur|Value|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Pilote|REG_SZ|Chemin du système vers le fichier vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"dbf,\*.cdx,\*.fpt"|  
|FileUsage (en)|REG_SZ|"1"|  
|Programme d’installation|REG_SZ|Chemin du système vers le fichier vfpodbc.dll|  
|SQLLevel (SQLLevel)|REG_SZ|"0"|  
  
 Le programme d’installation ajoute également la clé "Visual FoxPro Files", représentant le pilote Visual FoxPro par défaut, à la clé HKEY_CURRENT_USER-SOFTWARE-ODBC-Odbc.ini de votre système. Sous cette clé, le programme d’installation ajoute les valeurs décrites dans le tableau suivant.  
  
|Nom de la valeur|Type de valeur|Value|  
|----------------|----------------|-----------|  
|Pilote|REG_SZ|Chemin du système vers le fichier vfpodbc.dll|  
  
 Chaque fois que vous ajoutez une source de données Visual FoxPro ODBC à votre configuration ODBC, une nouvelle clé est ajoutée pour ce nom source de données. Les valeurs de la source de données correspondent aux valeurs que vous définissez dans la boîte de dialogue **ODBC Visual FoxPro Setup,** telle qu’indiquée dans le tableau suivant.  
  
|Nom de valeur (mot-clé)|Type de valeur|Value|  
|----------------------------|----------------|-----------|  
|Copies assemblées|REG_SQ|Toute séquence de collation prise en charge|  
|Description|REG_SZ|Description utilisateur de la source de données|  
|Pilote||Chemin du système vers le fichier vfpodbc.dll|  
|Exclusif||Oui ou Non|  
|ContexteFetch||Oui ou Non|  
|SourceDB|REG_SZ|Chemin vers . Fichier DBC|  
|SourceType|REG_SZ|"DBC" ou "DBF"|  
  
 Vous ne devriez pas accéder directement à ces informations; toute administration du registre est gérée par l’administrateur de l’ODBC lorsque vous ajoutez, modifiez ou supprimez une source de données.  
  
 Vous pouvez utiliser certains de ces mots clés et valeurs comme paramètres dans la fonction [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC API.
