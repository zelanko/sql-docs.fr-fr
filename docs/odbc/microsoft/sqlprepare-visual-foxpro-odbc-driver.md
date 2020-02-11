---
title: SQLPrepare (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5835ddaf27d097dcfff608649f50c1f7f41a93df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996308"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau principal  
  
 Prépare une instruction SQL en planifiant l’optimisation et l’exécution de l’instruction. L’instruction SQL est compilée pour être exécutée par [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 Si vos noms de table, de vue ou de champ contiennent des espaces, mettez les noms entre guillemets ('). Par exemple, si votre base de données contient une table nommée My table et le champ My Field, placez chaque élément de l’identificateur comme suit :  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 Pour plus d’informations, consultez [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md) dans le *Guide de référence du programmeur ODBC*.
