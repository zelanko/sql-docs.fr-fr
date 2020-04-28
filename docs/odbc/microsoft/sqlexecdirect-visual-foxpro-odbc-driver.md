---
title: SQLExecDirect (pilote ODBC Visual FoxPro) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 40c0a3404a3e7a9a67b6f71d197343eddb417955
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298669"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau principal  
  
 Exécute une nouvelle [instruction SQL préparable](../../odbc/microsoft/visual-foxpro-terminology.md). Le pilote ODBC Visual FoxPro utilise les valeurs actuelles des variables de marqueur de paramètre si des paramètres existent dans l’instruction.  
  
 Pour créer une commande Batch pour envoyer plusieurs instructions SQL à la fois, utilisez un point-virgule (;) pour séparer chaque instruction SQL dans le lot.  
  
 Si vos noms de table, de vue ou de champ contiennent des espaces, mettez les noms entre guillemets. Par exemple, si votre base de données contient une table nommée My table et le champ My Field, placez chaque élément de l’identificateur comme suit :  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Pour plus d’informations, consultez [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) dans le *Guide de référence du programmeur ODBC*.
