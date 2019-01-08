---
title: Enregistrement en cours et la taille du Recordset | Microsoft Docs
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
ms.assetid: e63ff331-8655-4be7-82c6-e6cd6cc9d16d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bde55939e974c6c879dcd126fac863ef0a866487
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52520648"
---
# <a name="current-record-and-size-of-recordset"></a>Enregistrement actif et taille du recordset
Cette section décrit comment localiser la position actuelle du curseur dans l’exemple **Recordset** dans [exemple de Code JScript pour retourner un jeu d’enregistrements](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md).  
  
## <a name="current-record"></a>Enregistrement en cours  
 L’enregistrement actif dans le jeu de données correspond à qui référencée par la position du curseur de la **Recordset** objet. Quand un **Recordset** est retourné à partir de la source de données en tant que résultat de l’appel **Recordset.Open**, **Command.Execute**, ou **Connection.Execute**  (y compris **Connection.NamedCommand** et **Connection.StoredProcedure**), le curseur est défini pour pointer vers le premier enregistrement. Dans l’exemple de dataset, l’enregistrement actif initial est les « poires secs organiques d’oncle Bob » élément.  
  
## <a name="size-of-recordset"></a>Taille du jeu d’enregistrements  
 Pour connaître la taille d’un **Recordset** d’objet, obtenir la valeur de la **sur Recordset.RecordCount** propriété. Cette valeur est un entier long qui indique le nombre d’enregistrements dans le **Recordset**. Si le jeu de données est retourné à partir du fournisseur OLE DB pour Microsoft SQL Server, cette valeur indique le nombre de lignes retournées. Lire le **RecordCount** propriété sur un fermé **Recordset** provoque une erreur.  
  
 Si le nombre d’enregistrements ne peut pas être déterminé, la valeur de la propriété est -1.  
  
 La valeur de la **RecordCount** propriété dépend également des capacités du fournisseur et le type de curseur utilisé. Un curseur avant uniquement, la valeur est -1. Pour un curseur statique ou jeu de clés, la valeur est le nombre réel d’enregistrements renvoyés dans le **Recordset** objet. Pour un curseur dynamique, la valeur est -1 ou le nombre réel d’enregistrements, en fonction de la source de données.  
  
 Un curseur qui prend en charge **Recordcount** doit travail plus difficile et par conséquent nécessite davantage de puissance informatique, qu’un curseur ne prend pas en charge **Recordcount**. Si vous n’avez pas besoin de connaître le nombre d’enregistrements, à l’aide du type de curseur différent peut aider à améliorer les performances de votre application, en particulier si vous devez gérer un grand jeu de données.  
  
 Dans certains cas, un fournisseur ou le curseur ne peut pas déterminer le **RecordCount** valeur sans préalable à une extraction de tous les enregistrements à partir de la source de données. Pour vous assurer d’inventaire précis, appelez le **Recordset**. **MoveLast** méthode avant d’appeler **sur Recordset.RecordCount**.  
  
 L’exemple **Recordset** objet obtenu à l’aide de la [exemple de Code JScript](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md) utilise un curseur avant uniquement, ainsi, l’appel **RecordCount** sur cet objet entraîne toujours -1. Si vous modifiez la ligne de code qui appelle le **Recordset**. **Ouvrez** méthode comme illustré dans l’exemple suivant, le **RecordCount** propriété retournera le nombre réel d’enregistrements extraits.  
  
```  
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText   
```  
  
 Il s’agit, car statique curseurs avec le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) prennent en charge **RecordCount**. Dans cet exemple, il existe cinq enregistrements et par conséquent **RecordCount** doit céder la valeur 5.  
  
 Cette section contient les rubriques suivantes.  
  
 [Limites d’un recordset](../../../ado/guide/data/boundaries-of-a-recordset.md)
