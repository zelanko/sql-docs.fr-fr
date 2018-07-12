---
title: Les noms et les systèmes d’exploitation 64 bits de Source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb7d29b7196f4c1e43de06a0a8fc17dae5acec9c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431848"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Noms des sources de données et systèmes d'exploitation 64 bits
  Pour générer et exécuter une application en tant qu'application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC à l'aide de l'Administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.  
  
## <a name="remarks"></a>Notes  
 Un système d'exploitation Windows 64 bits possède deux fichiers odbcad32.exe :  
  
-   %SystemRoot%\system32\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 64 bits.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 32 bits, y compris les applications 32 bits qui s'exécutent sur des systèmes d'exploitation 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
