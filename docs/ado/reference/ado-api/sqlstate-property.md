---
title: SQLState, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e43ace17f3f2b709c327f185a189a107b6b73065
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916882"
---
# <a name="sqlstate-property"></a>SQLState, propriété
Indique l’état SQL d’un objet d' [erreur](../../../ado/reference/ado-api/error-object.md) donné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **chaîne** de cinq caractères qui suit la norme ANSI SQL et indique le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **SQLSTATE** pour lire le code d’erreur à cinq caractères que le fournisseur retourne lorsqu’une erreur se produit pendant le traitement d’une instruction SQL. Par exemple, lorsque vous utilisez le fournisseur Microsoft OLE DB pour ODBC avec une base de données Microsoft SQL Server, les codes d’erreur d’état SQL proviennent d’ODBC, en fonction des erreurs spécifiques à ODBC ou des erreurs qui proviennent de Microsoft SQL Server, et sont ensuite mappées à des erreurs ODBC. Ces codes d’erreur sont documentés dans la norme ANSI SQL, mais peuvent être implémentés différemment selon les différentes sources de données.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
