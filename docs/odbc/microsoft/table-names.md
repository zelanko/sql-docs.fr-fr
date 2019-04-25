---
title: Noms de tables | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d72d7868d0e19719ea7992bdb8ccd1f61f3718d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633162"
---
# <a name="table-names"></a>Noms de table
Lorsque le dBASE, Microsoft Excel, Paradox, ou pilote est utilisé, les noms de table qui se produisent dans la clause FROM de SELECT ou DELETE, après la clause INTO dans INSERT et après la mise à jour, CREATE TABLE et DROP TABLE peuvent contenir un chemin d’accès valide, nom de principal, fichier texte et nommez extension .  
  
 Utilisation d’un nom de table ailleurs dans une instruction SQL ne prend pas en charge l’utilisation de chemins d’accès ou des extensions, mais accepte uniquement le nom de principal (par exemple, une EMP à partir de C:\ABC\EMP).  
  
 Noms de corrélation (alias) peuvent être utilisés. Exemple :  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
