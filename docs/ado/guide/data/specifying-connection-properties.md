---
title: Définition des propriétés de connexion | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8aea80d0bd512d75e46686722242d4955baa4769
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
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
