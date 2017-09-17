---
title: "Définition des propriétés de connexion | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 49399204f536d32321d46f1a8acba0ae435583c5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="specifying-connection-properties"></a>Définition des propriétés de connexion
Vous pouvez fournir une grande partie des informations spécifiées par un [chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md) en définissant les propriétés de la **connexion** objet avant l’ouverture de la connexion. Par exemple, vous pourriez obtenir le même effet comme indiqué par la chaîne de connexion dans [création d’une chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md) en utilisant le code suivant.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase est définie uniquement une fois que vous ouvrez la connexion.  
  
> [!NOTE]
>  Dans ADO, vous ne devez pas utiliser un mot de passe contenant un point-virgule (« ; »), sauf si le mot de passe est placée entre guillemets simples.
