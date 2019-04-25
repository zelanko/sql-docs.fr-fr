---
title: SQLParamOptions (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a66f0cd3a17baa9a09a5eeef2ade3d730f0a206b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62636658"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 1  
  
 Permet à une application spécifier plusieurs valeurs pour le jeu de paramètres attribué par [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). La possibilité de spécifier plusieurs valeurs pour un ensemble de paramètres est utile pour les insertions en bloc et d’autres travaux qui nécessite que la source de données pour traiter la même instruction SQL plusieurs fois avec différentes valeurs de paramètre. Par exemple, une application peut spécifier trois ensembles de valeurs du jeu de paramètres associés à un **insérer** instruction, puis exécutez le **insérer** instruction qu’une seule fois pour effectuer les trois insérer opérations.  
  
 Pour plus d’informations, consultez [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) dans le *de référence du programmeur ODBC*.
