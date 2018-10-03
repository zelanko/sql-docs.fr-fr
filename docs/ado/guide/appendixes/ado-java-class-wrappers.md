---
title: Wrappers de classe Java ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 840d8a0e266a6f913a8a74ec1451bc6285fbb08b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729217"
---
# <a name="ado-java-class-wrappers"></a>Wrappers de classe Java ADO
Ce code déclare une instance de l’ADO.NET [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wrapper de classe et initialise le tout sur la même ligne de code. En outre, il déclare des variables pour chacun des arguments dans le [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) (méthode), en particulier pour [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) et [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (Java ne prend pas en charge énuméré types). Il s’ouvre et ferme le **Recordset** objet. Définissant simplement Rs1 NULL planifie cette variable doit être publié lorsque Java effectue sa libération systématique et intermittente des objets inutilisés.  
  
```  
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du SDK Microsoft pour Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
