---
description: SQLExtendedFetch (pilote ODBC Visual FoxPro)
title: SQLExtendedFetch (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7f938dda4e9e474854d62c50401ee0bf91317983
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449171"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 2  
  
 Semblable à [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) , mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. Le jeu de résultats est un défilement vers l’avant et peut être rendu à défilement vers l’arrière si le curseur est défini comme statique, et non en avant uniquement.  
  
 Par défaut, le pilote ODBC Visual FoxPro ne retourne pas les lignes marquées comme supprimées dans une table FoxPro. Les lignes marquées pour suppression mais qui n’ont pas encore été supprimées d’une table ne sont pas incluses dans le curseur de jeu de résultats. Vous pouvez modifier ce comportement à l’aide de la commande [Set Deleted](../../odbc/microsoft/set-deleted-command.md) .  
  
 Pour plus d’informations, consultez [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) dans le *Guide de référence du programmeur ODBC*.
