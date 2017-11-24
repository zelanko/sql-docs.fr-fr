---
title: Collections (syntaxe ADO pour Visual C++) | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
dev_langs: C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58d14610c2d7cbebfddd8d9312cc218d4fd91bbe
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="collections-ado-for-visual-c-syntax"></a>Collections (syntaxe ADO pour Visual C++)
## <a name="parameters"></a>Paramètres  
  
### <a name="methods"></a>Méthodes  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Append, méthode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propriétés  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>Champs  
  
### <a name="methods"></a>Méthodes  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Append, méthode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propriétés  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>Erreurs  
  
### <a name="methods"></a>Méthodes  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Clear, méthode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propriétés  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>Propriétés  
  
### <a name="methods"></a>Méthodes  
  
```  
Refresh(void);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propriétés  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Pour plus d'informations, consultez  
  
-   [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Collection d’erreurs (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
