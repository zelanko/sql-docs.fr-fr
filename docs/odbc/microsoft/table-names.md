---
title: Noms de table Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91a415cd456186f18ef358b9d504145f78152774
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303120"
---
# <a name="table-names"></a>Noms de tables
Lorsque le pilote dBASE, Microsoft Excel, Paradox ou Text est utilisé, les noms de table qui se produisent dans la clause FROM de SELECT ou DELETE, après la clause INTO dans INSERT, et après UPDATE, CREATE TABLE et DROP TABLE peuvent contenir un chemin valide, nom principal et extension du nom de fichier.  
  
 L’utilisation d’un nom de table ailleurs dans une déclaration SQL ne prend pas en charge l’utilisation de chemins ou d’extensions, mais n’acceptera que le nom principal (par exemple, EMP FROM C: 'ABC’EMP).  
  
 Les noms de corrélation (alias) peuvent être utilisés. Par exemple :  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
