---
title: "Propriété de source de données (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b6003f19993835b937828948658e29cfb271cada
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="datasource-property-ado"></a>Propriété de source de données (ADO)
Indique un objet qui contient des données pour être représentée comme un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est utilisée pour créer des contrôles liés aux données avec l’environnement de données. L’environnement de données conserve des collections de données (sources de données) contenant des objets nommés (données membres) qui seront représentées comme un **Recordset** objet*.*  
  
 Le [DataMember](../../../ado/reference/ado-api/datamember-property.md) et **DataSource** propriétés doivent être utilisées conjointement.  
  
 L’objet référencé doit implémenter le **IDataSource** interface et doit contenir un **IRowset** interface.  
  
## <a name="usage"></a>Utilisation  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété DataMember](../../../ado/reference/ado-api/datamember-property.md)

