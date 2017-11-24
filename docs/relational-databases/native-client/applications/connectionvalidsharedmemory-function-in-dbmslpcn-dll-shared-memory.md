---
title: Fonction ConnectionValidSharedMemory dans dbmslpcn.dll Shared Memory | Documents Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: de8df92448f4a873b5e1489a4c66c2e36db651dc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Fonction ConnectionValidSharedMemory dans dbmslpcn.dll de mémoire partagée
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  La fonction détermine si la mémoire partagée de SQL Server est installé et activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Paramètres  
 *szServerName*  
  
-   Type : **char\***  
  
-   Le nom du serveur SQL.  
  
## <a name="return-value"></a>Valeur retournée  
 Type : **BOOL**  
  
 Retourne 0 si non valide ; Sinon, retourne différente de zéro.  
  
  
