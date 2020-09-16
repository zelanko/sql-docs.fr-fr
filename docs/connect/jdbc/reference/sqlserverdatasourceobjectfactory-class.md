---
description: Classe SQLServerDataSourceObjectFactory
title: Classe SQLServerDataSourceObjectFactory | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c41473da9a29cc962f1b3ad37df22b0699def3b3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450588"
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Classe SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une fabrique d'objet permettant de matérialiser des sources de données à partir de JNDI (Java Naming and Directory Interface).  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.lang.Object  
  
 **Implémente :** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Notes  
 Cette méthode est héritée par toutes les classes de source de données. Dans le cadre de sa prise en charge de l’interface Referenceable, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] expose cette classe qui implémente un ObjectFactory. Les serveurs d’applications Java appelleront getReference sur une classe de source de données, entraînant ainsi la création d’un objet Reference qui utilise de façon interne le nom de classe en tant que fabrique de classe.  
  
 Lorsque le serveur d’applications Java doit déréférencer l’objet Reference, il crée une instance de l’objet SQLServerDataSourceObjectFactory et appelle la méthode [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md), en transmettant l’objet Reference, pour récupérer l’instance de source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSourceObjectFactory, membres](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
