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
author: rothja
ms.author: jroth
ms.openlocfilehash: 485c53645387e5dafbe562442ec12503df0a6737
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760555"
---
# <a name="ado-java-class-wrappers"></a>Wrappers de classe Java ADO
Ce code déclare une instance du wrapper de la classe [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ADO et l’initialise, le tout sur la même ligne de code. En outre, il déclare des variables pour chacun des arguments de la méthode [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) , en particulier pour [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) et [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (car Java ne prend pas en charge les types énumérés). Il ouvre et ferme l’objet **Recordset** . La définition de RS1 sur NULL planifie simplement cette variable à libérer lorsque Java effectue sa mise en version systématique et intermittente des objets inutilisés.  
  
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
