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
ms.openlocfilehash: 32d538e31ca3f4a0d9b23411ebcb7b282df46b33
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67970310"
---
# <a name="sqlserverxaconnection-class"></a>SQLServerXAConnection, classe
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente les connexions JDBC qui peuvent participer à des transactions distribuées (XA).  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implémente :** javax.sql.XAConnection  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Notes  
 Un objet SQLServerXAConnection peut être inscrit dans une transaction distribuée au moyen d’un objet [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md). Un gestionnaire de transactions, faisant généralement partie d’un serveur de niveau intermédiaire, gère un objet SQLServerXAConnection à travers l’objet SQLServerXAResource.  
  
> [!NOTE]  
>  En général, les programmateurs d'applications n'utilisent pas cette interface directement. Elle est principalement utilisée par un gestionnaire de transactions actif dans le serveur de couche intermédiaire.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAConnection, membres](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
