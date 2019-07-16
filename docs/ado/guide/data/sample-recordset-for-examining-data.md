---
title: Exemple de jeu d’enregistrements pour l’examen des données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1882c5298d92e17a7ddaa165288fddfab7fdb02b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924308"
---
# <a name="sample-recordset-for-examining-data"></a>Exemple de recordset pour l’examen des données
Tout d’abord, examinons le **Recordset** de l’objet renvoyé à l’aide de la requête SQL suivante, exécutée sur les données d’exemple Northwind base dans Microsoft SQL Server.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 La résultante **Recordset** objet contient tous les génère dans la base de données indiqué dans le tableau suivant.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Poires secs organiques d’oncle Bob|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle choucroute|45.6000|  
|51|Manjimup pommes en poudre|53.0000|  
|74|Longlife Tofu|10.0000|  
  
 Si vous êtes intéressé par l’obtention de ces résultats vous-même, essayez l’exemple JScript suivant :  
  
-   [Exemple JScript pour retourner un jeu d’enregistrements](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
