---
title: SQLExtendedFetch (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053803"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 2  
  
 Semblable à [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. Le jeu de résultats est avec défilement avant et peut être effectué descendante déroulable si le curseur est défini comme étant statique, pas avant uniquement.  
  
 Par défaut, le pilote ODBC Visual FoxPro ne retourne pas de lignes marquées comme étant supprimées dans une table FoxPro. Lignes marquées pour suppression mais non encore supprimés à partir d’une table ne sont pas incluses dans le curseur de jeu de résultats. Vous pouvez modifier ce comportement à l’aide de la [SET DELETED](../../odbc/microsoft/set-deleted-command.md) commande.  
  
 Pour plus d’informations, consultez [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) dans le *de référence du programmeur ODBC*.
