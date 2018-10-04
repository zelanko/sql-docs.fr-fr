---
title: Définition des propriétés de connexion | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 885d201736adb3cd16efbea4f3907cd0aa324128
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622757"
---
# <a name="specifying-connection-properties"></a>Spécification des propriétés d’une connexion
Vous pouvez fournir une grande partie des informations spécifiées par un [chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md) en définissant des propriétés de la **connexion** objet avant l’ouverture de la connexion. Par exemple, vous pourriez obtenir le même effet comme indiqué par la chaîne de connexion dans [création d’une chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md) en utilisant le code suivant.  
  
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
