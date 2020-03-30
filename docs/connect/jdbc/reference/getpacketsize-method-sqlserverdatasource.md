---
title: Méthode getPacketSize (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b8f2cf03eb2eeaa3bb742a1f0d665c360e0d5f74
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67981040"
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>Méthode getPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la taille actuelle des paquets réseau utilisée pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], spécifiée en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur **int** contenant la taille actuelle des paquets réseau.  
  
## <a name="remarks"></a>Notes  
 Si la propriété packetSize n’est pas définie, la méthode getPacketSize retourne la valeur par défaut, 8000.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
