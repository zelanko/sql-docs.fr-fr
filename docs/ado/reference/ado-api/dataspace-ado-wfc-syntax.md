---
title: DataSpace (syntaxe ADO-WFC) | Microsoft Docs
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
ms.openlocfilehash: 569944991c029c091f0f17be4e5d943a893333a7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919196"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO - syntaxe WFC)
La méthode **CreateObject** de la classe **DataSpace** spécifie à la fois un objet métier pour traiter les requêtes d’application cliente (*ProgID*) et le protocole de communication et le serveur (*connexion*). **CreateObject** retourne un objet [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) qui représente le serveur.  
  
## <a name="package-commswfcdata"></a>package com. ms. wfc. Data  
  
### <a name="constructor"></a>Constructeur  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Méthodes  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
