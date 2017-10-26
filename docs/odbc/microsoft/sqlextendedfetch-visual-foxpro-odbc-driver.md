---
title: SQLExtendedFetch (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 25a9e0b16551ca27a6818fcfd890e56aeabfb44b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 2  
  
 Semblable à [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. Le jeu de résultats avant-autorise le défilement et peut être effectué descendante déroulable si le curseur est défini comme étant statique, pas de type avant uniquement.  
  
 Par défaut, le pilote ODBC Visual FoxPro ne retourne pas de lignes marquées comme supprimées dans une table FoxPro. Lignes marquées pour suppression mais non encore supprimés à partir d’une table ne sont pas inclus dans le curseur de jeu de résultats. Vous pouvez modifier ce comportement à l’aide de la [SET DELETED](../../odbc/microsoft/set-deleted-command.md) commande.  
  
 Pour plus d’informations, consultez [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) dans les *de référence du programmeur ODBC*.

