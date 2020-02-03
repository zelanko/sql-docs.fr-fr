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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
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
  
  
