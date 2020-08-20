---
description: SQLTables (pilote ODBC Visual FoxPro)
title: SQLTables (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 089208ab612984283e3f87c4ad03aca0ccfa2b38
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471551"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Retourne la liste des noms de tables spécifiés par le paramètre dans l’instruction **SQLTables** . Si aucun paramètre n’est spécifié, retourne les noms de tables stockés dans la source de données actuelle. Le pilote retourne les informations sous la forme d’un jeu de résultats.  
  
 Les appels de type énumération ne recevront pas d’entrée de jeu de résultats pour les vues distantes ou les vues paramétrées locales. Toutefois, un appel à **SQLTables** avec un spécificateur de nom de table unique trouvera une correspondance pour une telle vue, si elle existe avec ce nom ; Cela permet à l’API d’être utilisée pour vérifier les conflits de noms avant la création d’une nouvelle table.  
  
> [!NOTE]  
>  Le pilote ODBC Visual FoxPro fait la différence entre les [tables de base de données](../../odbc/microsoft/visual-foxpro-terminology.md) et les [tables libres](../../odbc/microsoft/visual-foxpro-terminology.md), même lorsque les deux types de tables sont stockés dans le même répertoire sur votre système. Si votre source de données est un répertoire de tables libres, le pilote ODBC Visual FoxPro ne catalogue pas ou ne retourne pas les noms de toutes les tables associées à une base de données.  
  
 Pour plus d’informations, consultez [SQLTables](../../odbc/reference/syntax/sqltables-function.md) dans le *Guide de référence du programmeur ODBC*.
