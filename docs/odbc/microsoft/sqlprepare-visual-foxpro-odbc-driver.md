---
title: SQLPrepare (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: f3ef083829b1ce322f2cede53f853c80683f01cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692177"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité d’API ODBC : Niveau principal  
  
 Prépare une instruction SQL par la planification de l’optimiser et exécutez l’instruction. L’instruction SQL est compilée pour l’exécution par [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 Si votre table, vue ou noms de champs contiennent des espaces, placez les noms à l’arrière guillemet simple (') marques. Par exemple, si votre base de données contient une table nommée My Table et le champ Mon champ, placez chaque élément de l’identificateur comme suit :  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 Pour plus d’informations, consultez [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md) dans le *de référence du programmeur ODBC*.
