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
ms.openlocfilehash: e38f2f513b7da2c9342470ba75e2ee11b3d7e52a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053900"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**et **fil**.  
  
 Le tableau suivant indique les mots clés minimaux requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir la liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote Microsoft Excel 3,0 ou 4,0, le pilote se connecte au répertoire actif.  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3,0 ou 4,0|Pilote, DriverID|Driver = {pilote Microsoft Excel (*. xls)}; DBQ = c:\temp ; DriverID = 278|  
|Microsoft Excel 5.0/7.0|Pilote, DriverID, DBQ|Driver = {pilote Microsoft Excel (*. xls)}; DBQ = c:\Temp\sample.xls ; DriverID = 22|  
|Microsoft Excel 97 et versions ultérieures|Pilote, DriverID, DBQ|Driver = {pilote Microsoft Excel (*. xls)}; DBQ = c:\Temp\sample.xls ; DriverID = 790|
