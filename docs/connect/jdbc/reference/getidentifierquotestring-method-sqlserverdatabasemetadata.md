---
title: Méthode getIdentifierQuoteString (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIdentifierQuoteString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dea35a0-56a8-412c-8cd3-6539527ff597
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 85a7b4b32c0c66e5825dc2728a5783c028410d45
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921529"
---
# <a name="getidentifierquotestring-method-sqlserverdatabasemetadata"></a>Méthode getIdentifierQuoteString (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la **chaîne** utilisée pour encadrer les identificateurs SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getIdentifierQuoteString()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant l'identificateur de devis.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getIdentifierQuoteString est spécifiée par la méthode getIdentifierQuoteString de l’interface java.sql.DatabaseMetaData.  
  
 Lors de l’utilisation du pilote [!INCLUDE[msCoName](../../../includes/msconame_md.md)] JDBC avec une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode retourne des guillemets **doubles** ("").  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
