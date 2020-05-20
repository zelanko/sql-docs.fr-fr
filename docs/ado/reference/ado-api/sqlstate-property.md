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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9b40c35730b02352f1e8667941aa4c220a7ad4df
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759765"
---
# <a name="sqlstate-property"></a>SQLState, propriété
Indique l’état SQL d’un objet d' [erreur](../../../ado/reference/ado-api/error-object.md) donné.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne une valeur de **chaîne** de cinq caractères qui suit la norme ANSI SQL et indique le code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la propriété **SQLSTATE** pour lire le code d’erreur à cinq caractères que le fournisseur retourne lorsqu’une erreur se produit pendant le traitement d’une instruction SQL. Par exemple, lorsque vous utilisez le fournisseur Microsoft OLE DB pour ODBC avec une base de données Microsoft SQL Server, les codes d’erreur d’état SQL proviennent d’ODBC, en fonction des erreurs spécifiques à ODBC ou des erreurs qui proviennent de Microsoft SQL Server, et sont ensuite mappées à des erreurs ODBC. Ces codes d’erreur sont documentés dans la norme ANSI SQL, mais peuvent être implémentés différemment selon les différentes sources de données.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
