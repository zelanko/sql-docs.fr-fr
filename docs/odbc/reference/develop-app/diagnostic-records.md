---
description: Enregistrements de diagnostic
title: Enregistrements de diagnostic | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b407ef1f8664191a16f54942f42f4088824517c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499920"
---
# <a name="diagnostic-records"></a>Enregistrements de diagnostic
Les *enregistrements de diagnostic*sont associés à chaque handle d’environnement, de connexion, d’instruction et de descripteur. Ces enregistrements contiennent des informations de diagnostic sur la dernière fonction appelée qui utilisait un handle particulier. Les enregistrements sont remplacés uniquement lorsqu’une autre fonction est appelée à l’aide de ce handle. Le nombre d’enregistrements de diagnostic pouvant être stockés à un moment donné n’est pas limité.  
  
 Il existe deux types d’enregistrements de diagnostic : un *enregistrement d’en-tête* et zéro, un ou plusieurs *enregistrements d’État*. L’enregistrement d’en-tête est l’enregistrement 0 ; les enregistrements d’État sont les enregistrements 1 et ultérieur. Les enregistrements de diagnostic sont composés d’un certain nombre de champs distincts, qui sont différents pour l’enregistrement d’en-tête et les enregistrements d’État. En outre, les composants ODBC peuvent définir leurs propres champs d’enregistrement de diagnostic.  
  
 Bien que les enregistrements de diagnostic puissent être considérés comme des structures, il n’est pas nécessaire qu’ils soient réellement des structures ; la façon dont un pilote stocke les informations de diagnostic est spécifique au pilote.  
  
 Les champs des enregistrements de diagnostic sont récupérés avec **SQLGetDiagField**. Les champs SQLSTATE, numéro d’erreur natif et message de diagnostic des enregistrements d’État peuvent être récupérés en un seul appel avec **SQLGetDiagRec**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Enregistrement d’en-tête](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Enregistrements d’état](../../../odbc/reference/develop-app/status-records.md)
