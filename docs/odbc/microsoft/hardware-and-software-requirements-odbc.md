---
title: Configurations matérielle et logicielle requises (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3f40621645aad2d1e52cb0a89baa8ff29b01446
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471320"
---
# <a name="hardware-and-software-requirements-odbc"></a>Configuration matérielle et logicielle requise (ODBC)
Cette rubrique répertorie les conditions requises pour utiliser les pilotes de base de données ODBC Desktop.  
  
## <a name="hardware-requirements"></a>Configuration matérielle  
 Pour utiliser les pilotes de base de données ODBC Desktop, vous devez disposer de :  
  
-   Un ordinateur compatible IBM.  
  
-   Un disque dur avec 6 Mo d’espace disque libre.  
  
-   Au moins 16 Mo de mémoire vive (RAM).  
  
## <a name="software-requirements"></a>Configuration logicielle  
 Pour accéder aux données avec un pilote ODBC, vous devez disposer de :  
  
-   Le pilote ODBC.  
  
-   32 bits Gestionnaire de pilote ODBC, version 3.51 ou version ultérieure (Odbc32.dll).  
  
-   Microsoft Windows 95 ou version ultérieure, ou Windows NT 4.0 ou Windows 2000.  
  
-   Taille de pile d’au moins 20 Ko pour une application à l’aide d’un pilote ODBC de Microsoft.  
  
 Lorsque vous utilisez Microsoft Windows NT 4.0 ou Windows 2000, le pilote 32 bits est thread-safe, mais uniquement via l’utilisation d’un sémaphore global qui contrôle l’accès au pilote. Utilisation simultanée du pilote est très limitée sous Windows NT. Tous les accès à la couche de Jet ISAM sera monothread pour toutes les applications utilisant le moteur Microsoft Jet.  
  
 Lorsque vous exécutez plusieurs applications 16 bits sur Windows on Windows (WOW) sur Microsoft Windows NT 4.0, les applications doivent être exécutées dans des espaces mémoire distincts. (Le même espace mémoire ne peut pas être utilisé car ODBC ne prend pas en charge plusieurs environnements dans le même processus.) Pour exécuter une application dans un espace de mémoire distincts, sélectionnez icône de l’application dans le Gestionnaire de programme, ouvrez le **fichier** menu et cliquez sur **propriétés**, puis cliquez sur **exécuter dans la mémoire distincts Espace**.  
  
 L’utilisation de ces pilotes par les applications 16 bits sur Windows 95 n’est pas pris en charge.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Spécifiques au pilote matérielle et logicielle requise  
  
-   Le MicrosoftAccess et dBASEdrivers peut nécessiter des modifications dans les fichiers Autoexec.bat ou Config.sys.
