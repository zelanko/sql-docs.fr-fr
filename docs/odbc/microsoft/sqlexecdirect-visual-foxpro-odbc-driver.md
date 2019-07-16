---
title: SQLExecDirect (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e701340217a885fbf1e3372c33ed1a8cfdb21457
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053852"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau principal  
  
 Exécute un nouveau [préparable instruction SQL](../../odbc/microsoft/visual-foxpro-terminology.md). Le pilote ODBC Visual FoxPro utilise les valeurs actuelles des variables de marqueur de paramètre si tous les paramètres existent dans l’instruction.  
  
 Pour créer une commande batch pour envoyer plusieurs instructions SQL à la fois, utilisez un point-virgule ( ;) pour séparer chaque instruction SQL du lot.  
  
 Si votre table, vue ou noms de champs contiennent des espaces, placez les noms à l’arrière guillemet marques. Par exemple, si votre base de données contient une table nommée My Table et le champ Mon champ, placez chaque élément de l’identificateur comme suit :  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Pour plus d’informations, consultez [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) dans le *de référence du programmeur ODBC*.
