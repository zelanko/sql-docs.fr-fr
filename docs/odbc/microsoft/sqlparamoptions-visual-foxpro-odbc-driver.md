---
title: SQLParamOptions, (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd714ce7774265a2afd00d42894d644a516bc402
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299469"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Permet à une application de spécifier plusieurs valeurs pour l’ensemble de paramètres assigné par [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). La possibilité de spécifier plusieurs valeurs pour un ensemble de paramètres est utile pour les insertions en bloc et d’autres travaux qui requièrent que la source de données traite la même instruction SQL plusieurs fois avec différentes valeurs de paramètre. Par exemple, une application peut spécifier trois ensembles de valeurs pour l’ensemble de paramètres associés à une instruction **Insert** , puis exécuter une fois l’instruction **Insert** pour effectuer les trois opérations d’insertion.  
  
 Pour plus d’informations, consultez [SQLParamOptions,](../../odbc/reference/syntax/sqlparamoptions-function.md) dans le *Guide de référence du programmeur ODBC*.
