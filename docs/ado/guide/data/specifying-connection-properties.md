---
description: Spécification des propriétés d’une connexion
title: Spécification des propriétés de connexion | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e1f7a26e66eae550bc740f2f9be5a3606650dcb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452831"
---
# <a name="specifying-connection-properties"></a>Spécification des propriétés d’une connexion
Vous pouvez fournir une grande partie des informations spécifiées par une [chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md) en définissant les propriétés de l’objet de **connexion** avant d’ouvrir la connexion. Par exemple, vous pouvez obtenir le même effet que la chaîne de connexion décrite dans [création d’une chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md) à l’aide du code suivant.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase est défini uniquement après l’ouverture de la connexion.  
  
> [!NOTE]
>  Dans ADO, vous ne devez pas utiliser un mot de passe contenant des points-virgules (« ; »), sauf si le mot de passe est placé entre guillemets simples.
