---
title: NativeError, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords:
- NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f6ee8724454a8871f6642f5d812584ccffd9385
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242388"
---
# <a name="nativeerror-property-ado"></a>NativeError, propriété (ADO)
Indique le code d’erreur spécifique au fournisseur pour une donnée [erreur](../../../ado/reference/ado-api/error-object.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Long** valeur qui indique le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **NativeError** propriété pour récupérer les informations d’erreur spécifique à la base de données pour un particulier **erreur** objet. Par exemple, lorsque vous utilisez le fournisseur ODBC de Microsoft pour OLE DB avec une base de données Microsoft SQL Server, les codes d’erreur provenant de SQL Server transitent ODBC et le fournisseur ODBC pour ADO **NativeError** propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
