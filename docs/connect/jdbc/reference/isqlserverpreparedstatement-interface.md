---
description: Interface ISQLServerPreparedStatement
title: Interface ISQLServerPreparedStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf87892e-5c34-4ac6-8258-c2a81e117b26
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9afc2bb3561b650baa7d7ef45e1d949cdfd19ea0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433521"
---
# <a name="isqlserverpreparedstatement-interface"></a>Interface ISQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente l'implémentation de base de la fonctionnalité d'instruction préparée JDBC. Cette interface a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.sql.PreparedStatement, [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public interface ISQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée par [SQLServerPreparedStatement Class](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
 Cette interface expose les méthodes spécifiques au [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] suivantes :  
  
|Méthode|Pour plus d'informations, consultez la rubrique|  
|------------|-------------------------------|  
|public void setDateTimeOffset(int, microsoft.sql.DateTimeOffset)|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
