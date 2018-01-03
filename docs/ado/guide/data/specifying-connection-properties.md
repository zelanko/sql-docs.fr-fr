---
title: "Définition des propriétés de connexion | Documents Microsoft"
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
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80da1a4da2d2a04f6a73b05e57ab366d2cb40e97
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
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
