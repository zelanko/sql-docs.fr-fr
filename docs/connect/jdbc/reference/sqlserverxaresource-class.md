---
title: Classe SQLServerXAResource | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c5e0cb02544e0ea96c29758f7c50179de48cf7a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaresource-class"></a>Classe SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une XAResource pour XA de gestion des transactions distribuées.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.lang.Object  
  
 **Implémente :** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Notes  
 Les transactions XA sont implémentées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] à l’aide de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Distributed Transaction Manager (DTC). La classe SQLServerXAResource appelle un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] étendus dll nommée sqljdbc_xa.dll, qui sert d’interface avec DTC. Les appels XA reçus par SQLServerXAResource (XA_START, XA_END, XA_PREPARE, etc.) sont mappés aux appels correspondants aux fonctions DTC.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
