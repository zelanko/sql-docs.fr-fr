---
description: NativeError, propriété (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c22667a9cd5855e4715b8aa37774a9137ab3cc4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774058"
---
# <a name="nativeerror-property-ado"></a>NativeError, propriété (ADO)
Indique le code d’erreur spécifique au fournisseur pour un objet d' [erreur](./error-object.md) donné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type long** qui indique le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **NativeError** pour récupérer les informations d’erreur propres à la base de données pour un objet d' **erreur** particulier. Par exemple, lorsque vous utilisez le fournisseur Microsoft ODBC pour OLE DB avec une base de données Microsoft SQL Server, les codes d’erreur natifs qui proviennent de SQL Server passent par ODBC et le fournisseur ODBC à la propriété **Native NativeError** .  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Error](./error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)