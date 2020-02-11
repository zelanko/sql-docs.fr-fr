---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d58d7885eed1a8ed0611470f29cb24e8072afcb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053803"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 2  
  
 Semblable à [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) , mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. Le jeu de résultats est un défilement vers l’avant et peut être rendu à défilement vers l’arrière si le curseur est défini comme statique, et non en avant uniquement.  
  
 Par défaut, le pilote ODBC Visual FoxPro ne retourne pas les lignes marquées comme supprimées dans une table FoxPro. Les lignes marquées pour suppression mais qui n’ont pas encore été supprimées d’une table ne sont pas incluses dans le curseur de jeu de résultats. Vous pouvez modifier ce comportement à l’aide de la commande [Set Deleted](../../odbc/microsoft/set-deleted-command.md) .  
  
 Pour plus d’informations, consultez [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) dans le *Guide de référence du programmeur ODBC*.
