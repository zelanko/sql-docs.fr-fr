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
manager: jroth
ms.openlocfilehash: 9e4804b5cbdec4008e1c967b81620ea96eead924
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711317"
---
# <a name="sqlstate-property"></a>SQLState, propriété
Indique l’état SQL d’une donnée [erreur](../../../ado/reference/ado-api/error-object.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne les cinq caractères **chaîne** valeur qui respecte la norme ANSI SQL et indique le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **SQLState** propriété à lire le code d’erreur à cinq caractères renvoyé par le fournisseur lorsqu’une erreur se produit pendant le traitement d’une instruction SQL. Par exemple, lorsque vous utilisez le fournisseur Microsoft OLE DB pour ODBC avec une base de données Microsoft SQL Server, codes d’erreur SQL état issus de ODBC, basé sur les erreurs spécifiques à ODBC ou sur les erreurs qui proviennent de Microsoft SQL Server et sont ensuite mappées à ODBC erreurs. Ces codes d’erreur sont documentées dans la norme SQL ANSI, mais peuvent être implémentées différemment par différentes sources de données.  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
