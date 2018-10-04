---
title: SQLDriverConnect (pilote Excel) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2d7e879c35e7cbf2f2b261d94eff22936f7880b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775347"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de se connecter à un pilote sans création d’une source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**, et **FIL**.  
  
 Le tableau suivant montre les mots-clés minimales requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir une liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour Microsoft Excel 3.0 ou 4.0 pilote, le pilote se connecte dans le répertoire actif.  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 ou 4.0|Pilote, DriverID|Driver = {pilote Microsoft Excel (*.xls)} ; DBQ = c:\temp ; DriverID = 278|  
|Microsoft Excel 5.0/7.0|Pilote, DriverID, DBQ|Driver = {pilote Microsoft Excel (*.xls)} ; DBQ=c:\Temp\sample.xls ; DriverID = 22|  
|Microsoft Excel 97 et versions ultérieur|Pilote, DriverID, DBQ|Driver = {pilote Microsoft Excel (*.xls)} ; DBQ=c:\Temp\sample.xls ; DriverID = 790|
