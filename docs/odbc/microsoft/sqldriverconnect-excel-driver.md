---
title: SQLDriverConnect (Excel Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1108206bf38183887540b114fda5a1e913aa67d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307120"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (pilote Excel)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Excel Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes: **DSN**, **DBQ**, et **FIL**.  
  
 Le tableau suivant affiche les mots clés minimums requis pour se connecter à chaque pilote, et fournit un exemple de mots clés / paires de valeur utilisés avec **SQLDriverConnect**. Pour une liste complète des valeurs DRIVERID, voir [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote Microsoft Excel 3.0 ou 4.0, le pilote se connectera à l’annuaire actuel.  
  
|Pilote|Mots-clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 ou 4.0|Pilote, DriverID|DriverMD Microsoft Excel Driver (en anglais seulement) ; DBQ-c: temp; DriverID 278|  
|Microsoft Excel 5.0/7.0|Pilote, DriverID, DBQ|DriverMD Microsoft Excel Driver (en anglais seulement) ; DBQ-c: temp.sample.xls; DriverID 22|  
|Microsoft Excel 97 et plus tard|Pilote, DriverID, DBQ|DriverMD Microsoft Excel Driver (en anglais seulement) ; DBQ-c: temp.sample.xls; DriverID 790|
