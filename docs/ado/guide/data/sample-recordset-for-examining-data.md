---
description: Exemple de recordset pour l’examen des données
title: Exemple d’ensemble d’enregistrements pour l’examen des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: rothja
ms.author: jroth
ms.openlocfilehash: f4c989667d5b4a5ceb3fb0c4f4d929e49be92e00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452911"
---
# <a name="sample-recordset-for-examining-data"></a>Exemple de recordset pour l’examen des données
Tout d’abord, examinons l’objet **Recordset** comme retourné à l’aide de la requête SQL suivante, exécutée sur l’exemple de base de données Northwind dans Microsoft SQL Server.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 L’objet **Recordset** obtenu contient tous les produits de la base de données indiquée dans le tableau suivant.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Poires séchées Organic d’oncle Bob|30,0000|  
|14|Tofu|23,2500|  
|28|Rssle choucroute|45,6000|  
|51|Manjimup pommes séchées|53,0000|  
|74|Longlife Tofu|10,0000|  
  
 Si vous souhaitez obtenir ces résultats vous-même, essayez l’exemple JScript suivant :  
  
-   [Exemple JScript pour retourner un jeu d’enregistrements](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
