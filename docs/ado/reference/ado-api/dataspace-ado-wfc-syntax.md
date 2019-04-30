---
title: DataSpace (ADO - syntaxe WFC) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94a539fb2ba3285bd8bb5c3668879695598725a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140107"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO - syntaxe WFC)
Le **createObject** méthode de la **DataSpace** classe spécifie un objet métier pour traiter les demandes des applications clientes (*progid*) et le protocole de communication et le serveur (*connexion*). **createObject** retourne un [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) objet qui représente le serveur.  
  
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
### <a name="constructor"></a>Constructeur  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Méthodes  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Properties  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
