---
title: "Native Error, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords: NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55a6415051943de6b92327ce4e9cf157c972edd4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="nativeerror-property-ado"></a>Native Error, propriété (ADO)
Indique le code d’erreur spécifique au fournisseur pour une donnée [erreur](../../../ado/reference/ado-api/error-object.md) objet.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **Long** valeur qui indique le code d’erreur.  
  
## <a name="remarks"></a>Notes   
 Utilisez le **Native Error** propriété à récupérer les informations d’erreur spécifique à la base de données pour un particulier **erreur** objet. Par exemple, lors de l’utilisation du fournisseur Microsoft ODBC pour OLE DB avec une base de données Microsoft SQL Server, les codes d’erreur qui proviennent de SQL Server transitent ODBC et le fournisseur ODBC à ADO **Native Error** propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, Native Error, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, Native Error, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
