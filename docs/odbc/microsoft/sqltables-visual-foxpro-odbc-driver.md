---
title: SQLTables (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d15e72670bda9c70939cc0b5f0eaa75f855edc7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 1  
  
 Retourne la liste des noms de table spécifié par le paramètre dans le **SQLTables** instruction. Si aucun paramètre n’est spécifié, retourne les noms de table stockées dans la source de données actuelle. Le pilote retourne les informations comme jeu de résultats.  
  
 Appels de type énumération ne reçoivent pas une entrée de jeu de résultats pour des vues paramétrées locales ou distant. Toutefois, un appel à **SQLTables** avec une table unique spécificateur de nom trouver une correspondance pour une telle vue s’il est présent portant ce nom ; Cela permet à l’API à utiliser pour rechercher les conflits de noms avant la création d’une nouvelle table.  
  
> [!NOTE]  
>  Le pilote ODBC Visual FoxPro établit la distinction entre [tables de base de données](../../odbc/microsoft/visual-foxpro-terminology.md) et [libre tables](../../odbc/microsoft/visual-foxpro-terminology.md), même si les deux types de tables sont stockées dans le même répertoire sur votre système. Si votre source de données est un répertoire de tables indépendantes, le pilote ODBC Visual FoxPro ne pas de catalogue ou retourner les noms de toutes les tables qui sont associés à une base de données.  
  
 Pour plus d’informations, consultez [SQLTables](../../odbc/reference/syntax/sqltables-function.md) dans les *de référence du programmeur ODBC*.
