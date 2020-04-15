---
title: SQLExecDirect (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298669"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC : Niveau de base  
  
 Exécute une nouvelle [déclaration SQL préparlementable](../../odbc/microsoft/visual-foxpro-terminology.md). Le visual FoxPro ODBC Driver utilise les valeurs actuelles des variables de marqueur de paramètres s’il existe des paramètres dans l’énoncé.  
  
 Pour créer une commande par lots pour soumettre plus d’une déclaration SQL à la fois, utilisez un point-virgule (;) pour séparer chaque relevé SQL dans le lot.  
  
 Si votre table, vue ou noms de champ contiennent des espaces, enfermez les noms dans les guillemets arrière. Par exemple, si votre base de données contient une table nommée Ma Table et le champ Mon champ, regroupez chaque élément de l’identifiant comme suit :  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Pour plus d’informations, voir [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) dans la *référence du programmeur ODBC*.
