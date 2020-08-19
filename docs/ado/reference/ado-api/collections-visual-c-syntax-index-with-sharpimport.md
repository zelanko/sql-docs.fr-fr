---
description: 'Collections (Visual C++ index de syntaxe avec #import)'
title: 'Collections (Visual C++ index de syntaxe avec #import) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
author: rothja
ms.author: jroth
ms.openlocfilehash: 58f7761cc67cd1320594988ba50bfcc79bcfc0d9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450911"
---
# <a name="collections-visual-c-syntax-index-with-import"></a>Collections (Visual C++ index de syntaxe avec #import)
Il est utile de savoir que les collections héritent de certaines méthodes et propriétés communes.  
  
 Toutes les collections héritent de la propriété **Count** et de la méthode **Refresh** , et toutes les collections ajoutent la propriété **Item** . La collection **Errors** ajoute la méthode **Clear** . La collection **Parameters** hérite des méthodes **Append** et **Delete** , tandis que la collection **Fields** ajoute les méthodes d' **Ajout**, de **suppression**et de **mise à jour** .  
  
## <a name="properties-collection"></a>Collection Properties  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Collection d’erreurs  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Collection Parameters  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Collection Fields  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Errors, collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
