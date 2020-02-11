---
title: Enregistrement actuel et taille du Recordset | Microsoft Docs
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
ms.openlocfilehash: a01e17ea9c786a724e5869a28bf4d8927b58ac81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925692"
---
# <a name="current-record-and-size-of-recordset"></a>Enregistrement actif et taille du recordset
Cette section décrit comment localiser la position actuelle du curseur dans l’exemple de code **Recordset** dans [JScript pour retourner un Recordset](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md).  
  
## <a name="current-record"></a>Enregistrement actif  
 L’enregistrement en cours dans le jeu de données correspond à celui pointé par la position du curseur de l’objet **Recordset** . Lorsqu’un objet **Recordset** est retourné à partir de la source de données suite à l’appel de **Recordset. Open**, **Command. Execute**ou **Connection. Execute** (y compris **Connection. NamedCommand** et **Connection. StoredProcedure**), le curseur est défini pour pointer au premier enregistrement. Dans l’exemple de jeu de données, l’enregistrement initial actuel est l’élément « poires séchées organiques de l’oncle Bob ».  
  
## <a name="size-of-recordset"></a>Taille du Recordset  
 Pour déterminer la taille d’un objet **Recordset** , obtenez la valeur de la propriété **Recordset. RecordCount** . Cette valeur est un entier long qui indique le nombre d’enregistrements dans le **Recordset**. Si le jeu de données est retourné par le fournisseur OLEDB pour Microsoft SQL Server, cette valeur indique le nombre de lignes retournées. La lecture de la propriété **RecordCount** sur un **jeu d’enregistrements** fermé génère une erreur.  
  
 Si le nombre d’enregistrements ne peut pas être déterminé, la valeur de la propriété est-1.  
  
 La valeur de la propriété **RecordCount** dépend également des fonctionnalités du fournisseur et du type de curseur utilisé. Pour un curseur avant uniquement, la valeur est-1. Pour un curseur de jeu de clés ou statique, la valeur est le nombre réel d’enregistrements retournés dans l’objet **Recordset** . Pour un curseur dynamique, la valeur est soit-1, soit le nombre réel d’enregistrements, en fonction de la source de données.  
  
 Un curseur qui prend en charge **RecordCount** doit fonctionner plus difficile et, par conséquent, nécessite plus de puissance de calcul qu’un curseur ne prend pas en charge **RecordCount**. Si vous n’avez pas besoin de connaître le nombre d’enregistrements, l’utilisation d’un type de curseur différent peut contribuer à améliorer les performances de votre application, en particulier si vous devez gérer un jeu de données volumineux.  
  
 Dans certains cas, un fournisseur ou un curseur ne peut pas déterminer la valeur **RecordCount** sans extraire d’abord tous les enregistrements de la source de données. Pour garantir un comptage précis, appelez le **Recordset**. Méthode **MoveLast** avant **d’appeler Recordset. RecordCount**.  
  
 L’exemple **d’objet Recordset** obtenu à l’aide de l' [exemple de code JScript](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md) utilise un curseur avant uniquement. par conséquent, l’appel de **RecordCount** sur cet objet donne toujours la résultat-1. Si vous modifiez la ligne de code qui appelle le **Recordset**. Méthode **Open** , comme indiqué dans l’exemple suivant, la propriété **RecordCount** retourne le nombre réel d’enregistrements extraits.  
  
```  
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText   
```  
  
 Cela est dû au fait que les curseurs statiques avec le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) prennent en charge la fonction **RecordCount**. Dans cet exemple, il y a cinq enregistrements et, par conséquent, **RecordCount** doit donner la valeur 5.  
  
 Cette section contient la rubrique suivante.  
  
 [Limites d’un recordset](../../../ado/guide/data/boundaries-of-a-recordset.md)
