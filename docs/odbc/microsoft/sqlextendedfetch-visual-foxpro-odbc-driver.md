---
title: SQLExtendedFetch (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.openlocfilehash: 3ecff538198a2b517f980cc63acfc97d29a9f162
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298649"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 2  
  
 Semblable à [SQLFetch,](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. L’ensemble de résultat est défilement vers l’avant et peut être rendu défilement vers l’arrière si le curseur est défini comme statique, et non vers l’avant seulement.  
  
 Par défaut, le visual FoxPro ODBC Driver ne renvoie pas les lignes marquées comme supprimées dans une table FoxPro. Les lignes marquées pour la suppression mais non encore retirées d’une table ne sont pas incluses dans le curseur de jeu de résultat. Vous pouvez modifier ce comportement en utilisant la commande [SET DELETED.](../../odbc/microsoft/set-deleted-command.md)  
  
 Pour plus d’informations, voir [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) dans la *référence du programmeur ODBC*.
