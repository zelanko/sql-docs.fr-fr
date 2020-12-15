---
title: Noms des sources de données et systèmes d’exploitation 64 bits | Microsoft Docs
description: Découvrez comment créer et exécuter une application en tant qu’application 32 bits sur un système d’exploitation 64 bits en créant la source de données ODBC avec l’administrateur ODBC.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 416cd9e812cabccacc710f2b23c506702fae1778
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475970"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Noms des sources de données et systèmes d'exploitation 64 bits
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Pour générer et exécuter une application en tant qu'application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC à l'aide de l'Administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.  
  
## <a name="remarks"></a>Remarks  
 Un système d'exploitation Windows 64 bits possède deux fichiers odbcad32.exe :  
  
-   %SystemRoot%\system32\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 64 bits.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 32 bits, y compris les applications 32 bits qui s'exécutent sur des systèmes d'exploitation 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
