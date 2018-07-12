---
title: Les noms et les systèmes d’exploitation 64 bits de Source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 32e77babbaf5e92c81f12d43c320d357783a1e51
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410517"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Noms des sources de données et systèmes d'exploitation 64 bits
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Pour générer et exécuter une application en tant qu'application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC à l'aide de l'Administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.  
  
## <a name="remarks"></a>Notes  
 Un système d'exploitation Windows 64 bits possède deux fichiers odbcad32.exe :  
  
-   %SystemRoot%\system32\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 64 bits.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe permet de créer et de maintenir les noms des sources de données pour les applications 32 bits, y compris les applications 32 bits qui s'exécutent sur des systèmes d'exploitation 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
