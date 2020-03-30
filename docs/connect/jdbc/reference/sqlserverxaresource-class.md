---
title: Classe SQLServerXAResource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 282201b7ff3f5b2ebfe4d8a1224d4d1b39285c53
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67970086"
---
# <a name="sqlserverxaresource-class"></a>Classe SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une XAResource pour la gestion des transactions distribuées XA.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.lang.Object  
  
 **Implémente :** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Notes  
 Les transactions XA sont implémentées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Distributed Transaction Manager (DTC). La classe SQLServerXAResource fait des appels à une DLL étendue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nommée sqljdbc_xa.dll, qui joue le rôle d’interface avec DTC. Les appels XA reçus par SQLServerXAResource (XA_START, XA_END, XA_PREPARE, etc.) sont mappés aux appels correspondants faits aux fonctions DTC.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
