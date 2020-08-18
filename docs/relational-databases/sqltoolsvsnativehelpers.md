---
description: SqlToolsVSNativeHelpers
title: SqlToolsVSNativeHelpers | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f2a367470a4f6ca7c8d6b3015ab45b77888bbab2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88324889"
---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
[!INCLUDE [SQL Server Azure SQL Database](../includes/applies-to-version/sql-asdb.md)]
  Bibliothèque qui prend en charge les fonctionnalités de SQL Server dans Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne, **True** si le point d'entrée de la DLL s'est initialisé correctement, sinon **False**.  
  
## <a name="see-also"></a>Voir aussi  
 [FrameWindowVisible](../relational-databases/sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
