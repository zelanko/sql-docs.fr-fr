---
title: Classe SQLServerXAResource | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64d2ae6fe7e4e57774dc75c34fc61ab680e99434
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
  
