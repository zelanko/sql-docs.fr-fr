---
title: Wrappers de classe Java ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70486a27cfbe5c977d371906da89563059685093
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67927005"
---
# <a name="ado-java-class-wrappers"></a>Wrappers de classe Java ADO
Ce code déclare une instance de l’ADO.NET [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wrapper de classe et initialise le tout sur la même ligne de code. En outre, il déclare des variables pour chacun des arguments dans le [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) (méthode), en particulier pour [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) et [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (Java ne prend pas en charge énuméré types). Il s’ouvre et ferme le **Recordset** objet. Définissant simplement Rs1 NULL planifie cette variable doit être publié lorsque Java effectue sa libération systématique et intermittente des objets inutilisés.  
  
```java
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du SDK Microsoft pour Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
