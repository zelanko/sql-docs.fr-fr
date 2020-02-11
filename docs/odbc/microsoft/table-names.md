---
title: Noms des tables | Microsoft Docs
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
ms.openlocfilehash: 5dd8de055521f4a1831d20a9a34bedb9309d1de6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939789"
---
# <a name="table-names"></a>Noms de tables
Lorsque le pilote dBASE, Microsoft Excel, Paradox ou texte est utilisé, les noms de table qui se trouvent dans la clause FROM de SELECT ou DELETE, après la clause INTO dans INSERT, et après UPDATE, CREATE TABLE et DROP TABLE peuvent contenir un chemin d’accès, un nom principal et une extension de nom de fichier valides. .  
  
 L’utilisation d’un nom de table ailleurs dans une instruction SQL ne prend pas en charge l’utilisation de chemins d’accès ou d’extensions, mais n’accepte que le nom principal (par exemple, EMP de C:\ABC\EMP).  
  
 Les noms de corrélation (alias) peuvent être utilisés. Par exemple :  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
