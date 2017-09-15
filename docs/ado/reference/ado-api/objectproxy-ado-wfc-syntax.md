---
title: ObjectProxy (ADO - syntaxe WFC) | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0bd3aa2bd2cf7b49432e6b29c312e65819d50f4a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - syntaxe WFC)
Un **ObjectProxy** objet représente un serveur et est retourné par la **createObject** méthode de la [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet. La classe ObjectProxy possède une méthode, **appeler**, qui peut appeler une méthode sur le serveur et retourner un objet à cet appel.  
  
 **package com.ms.wfc.data**  
  
## <a name="methods"></a>Méthodes  
  
### <a name="call-method-adowfc-syntax"></a>Méthode d’appel (syntaxe ADO/WFC)  
 Appelle une méthode sur le serveur représenté par l’objet ObjectProxy. Le cas échéant, les arguments de méthode peuvent être considérés comme un tableau d’objets.  
  
#### <a name="syntax"></a>Syntaxe  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Valeur renvoyée  
 Objet  
 Objet qui résulte de l’appel de la méthode.  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectProxy*  
 Un **ObjectProxy** objet qui représente le serveur.  
  
 *(méthode)*  
 Chaîne contenant le nom de la méthode à appeler sur le serveur.  
  
 *args*  
 Ce paramètre est facultatif. Un tableau d’objets qui sont des arguments de la méthode sur le serveur. Types de données Java sont automatiquement convertis en types de données pouvant être utilisée sur le serveur.
