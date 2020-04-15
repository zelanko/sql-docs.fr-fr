---
title: SQLDriverConnect (Access Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a679cbb16ece3f239b1d17daabc8a294b808287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302910"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes: **DSN**, **DBQ**, et **FIL**.  
  
 Les mots clés **UID** et **PWD** sont également pris en charge.  
  
 Le mot clé PWD ne doit pas inclure l’un des caractères spéciaux (voir SQL_SPECIAL_CHARACTERS dans **SQLGetInfo** Valeurs retournées).  
  
 Le tableau suivant affiche les mots clés minimums requis pour se connecter à chaque pilote, et fournit un exemple de mots clés / paires de valeur utilisés avec **SQLDriverConnect**. Pour une liste complète des valeurs DRIVERID, voir [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Pilote|Mots-clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Microsoft Access|Pilote, DBQ|DriverMD Microsoft Access Driver (mdd)MD; DBQ-c:\\'temp\\'sample.mdb|
