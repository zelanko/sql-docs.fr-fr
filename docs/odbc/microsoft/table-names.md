---
title: Noms de tables | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 480ca31108b608139b5563f0c18d1fa020e76f75
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="table-names"></a>Noms de tables
Lorsque le dBASE, Microsoft Excel, Paradox, ou pilote est utilisé, les noms de table qui se produisent dans la clause FROM de SELECT ou DELETE, après la clause INTO dans INSERT et après la mise à jour, CREATE TABLE et DROP TABLE peuvent contenir un chemin d’accès valide, nom du serveur principal, fichier texte et extension de nom.  
  
 Utilisation d’un nom de table dans une instruction SQL ne prend pas en charge l’utilisation de chemins d’accès ou des extensions, mais accepte uniquement le nom de principal (par exemple, une EMP à partir de C:\ABC\EMP).  
  
 Noms de corrélation (alias) peuvent être utilisés. Exemple :  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
