---
title: Noms des sources de données et systèmes d’exploitation 64 bits | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055845"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Noms des sources de données et systèmes d'exploitation 64 bits
  Pour générer et exécuter une application en tant qu'application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC à l'aide de l'Administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.  
  
## <a name="remarks"></a>Remarques  
 Un système d'exploitation Windows 64 bits possède deux fichiers odbcad32.exe :  
  
-   %SystemRoot%\system32\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 64 bits.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 32 bits, y compris les applications 32 bits qui s'exécutent sur des systèmes d'exploitation 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
