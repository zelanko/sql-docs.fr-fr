---
description: Classe SQLServerXAResource
title: Classe SQLServerXAResource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8126ecb70b0985845536d6d023937df6bbd344ff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458191"
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
  
  
