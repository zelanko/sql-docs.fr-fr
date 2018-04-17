---
title: SQLGetTypeInfo (pilote Paradox) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5908d86bd7c42aeb92340a825df0f62e2cb233af
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de Corel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) renvoyé dans la table générée par **SQLGetTypeInfo** sera le nom plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE s’affichera dans la colonne de recherche pour l’octet, compteur, Double, les types de données unique, longue et courte. (La fonction similaire peut être obtenue en convertissant la valeur à un caractère en utilisant les fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)
