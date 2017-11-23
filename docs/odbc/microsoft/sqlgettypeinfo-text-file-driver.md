---
title: SQLGetTypeInfo (pilote du fichier texte) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 74cdefbb494d510bf67ca07387e7a23bcce8d44a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (pilote du fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) renvoyé dans la table générée par **SQLGetTypeInfo** sera le nom plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE s’affichera dans la colonne de recherche pour l’octet, compteur, Double, les types de données unique, longue et courte. (La fonction LIKE est possible en convertissant la valeur en un caractère en utilisant les fonctions de conversion canonique ODBC, puis effectuer la comparaison.)  
  
 Lorsque le pilote de texte est utilisé, **SQLGetTypeInfo** retourne CASE_SENSITIVE la valeur FALSE pour le texte (CHAR et LONGCHAR), les types de données lorsque les types de données réellement respectent la casse.
