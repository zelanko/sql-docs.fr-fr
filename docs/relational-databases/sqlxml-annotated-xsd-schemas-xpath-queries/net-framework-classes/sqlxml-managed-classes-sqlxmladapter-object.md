---
title: "Objet SqlXmlAdapter (Classes managées de SQLXML) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 999504b39724033f885d533f8177567455205276
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-managed-classes---sqlxmladapter-object"></a>Classes - managées SQLXML objet SqlXmlAdapter
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Cet objet fournit des méthodes qui facilitent l’interaction avec le dataset dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Pour obtenir un exemple fonctionnel, consultez [l’accès à des fonctionnalités de SQLXML dans l’environnement .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 L’objet SqlXmlAdapter prend en charge ces méthodes :  
  
 void Fill (DataSet ds)  
 Remplit le dataset dans le .NET Framework avec les données XML extraites de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Annuler la mise à jour (DataSet ds)  
 Applique des mises à jour aux enregistrements dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir des données dans le dataset.  
  
 L’objet SqlXmlAdapter prend en charge ces constructeurs :  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlXmlCommand &#40; Managées SQLXML Classes &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [Objet SqlXmlParameter &#40; Managées SQLXML Classes &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
