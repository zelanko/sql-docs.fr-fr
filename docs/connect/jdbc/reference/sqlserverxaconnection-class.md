---
title: Classe SQLServerXAConnection | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 177b10c9657c4cb8d6b37f7dec9d3b860308dcb7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788903"
---
# <a name="sqlserverxaconnection-class"></a>SQLServerXAConnection, classe
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente les connexions JDBC qui peuvent participer à des transactions distribuées (XA).  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implémente :** javax.sql.XAConnection  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Notes  
 Un objet SQLServerXAConnection peut être inscrit dans une transaction distribuée au moyen d’un objet [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md). Un gestionnaire de transactions, faisant généralement partie d’un serveur de couche intermédiaire, gère un objet SQLServerXAConnection via l’objet SQLServerXAResource.  
  
> [!NOTE]  
>  En général, les programmateurs d'applications n'utilisent pas cette interface directement. Elle est principalement utilisée par un gestionnaire de transactions actif dans le serveur de couche intermédiaire.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAConnection, membres](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
