---
title: SQLParamOptions (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 17a82974d8531d0524f4bac89701d6c97a05198d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 1  
  
 Permet à une application spécifier plusieurs valeurs pour l’ensemble de paramètres affectés par [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). La possibilité de spécifier plusieurs valeurs pour un ensemble de paramètres est utile pour les insertions en bloc et d’autres tâches qui nécessite que la source de données pour traiter la même instruction SQL plusieurs fois avec différentes valeurs de paramètre. Par exemple, une application peut spécifier trois jeux de valeurs pour le jeu de paramètres associés à un **insérer** instruction, puis exécutez le **insérer** instruction une fois pour effectuer les trois opérations d’insertion.  
  
 Pour plus d’informations, consultez [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) dans les *de référence du programmeur ODBC*.

