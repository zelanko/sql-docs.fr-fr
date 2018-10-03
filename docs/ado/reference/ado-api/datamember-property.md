---
title: DataMember, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7a1bb2d55fbf4e8d2030c612a1d000b93ca1110
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603707"
---
# <a name="datamember-property"></a>DataMember, propriété
Indique le nom du membre de données qui est récupérée à partir de la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) référencé par le [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) propriété.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur. Le nom n’est pas sensible à la casse.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est utilisée pour créer des contrôles liés aux données avec l’environnement de données. L’environnement de données conserve des collections de données (sources de données) contenant des objets nommés (données membres) qui seront représentés comme un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
 Le **DataMember** et **DataSource** propriétés doivent être utilisées ensemble.  
  
 Le **DataMember** propriété détermine quel objet spécifié par le **DataSource** propriété est représentée comme un **Recordset** objet. Le **Recordset** objet doit être fermé avant que cette propriété est définie. Une erreur est générée si le **DataMember** propriété n’est pas définie avant la **DataSource** propriété, ou si le **DataMember** nom n’est pas reconnu par l’objet spécifié dans le **DataSource** propriété.  
  
## <a name="usage"></a>Utilisation  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataSource, propriété (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
