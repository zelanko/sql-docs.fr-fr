---
title: SQLDriverConnect (Pilote Paradox) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68171cfab2b65634433b107d829dd2a6e9b5c985
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307110"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (pilote Paradox)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Paradox Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes: **DSN**, **DBQ**, et **FIL**.  
  
 Le mot-clé **PWD** est également pris en charge. Le mot clé PWD ne doit pas inclure l’un des caractères spéciaux (voir SQL_SPECIAL_CHARACTERS dans **SQLGetInfo** Valeurs retournées).  
  
 Une fois qu’un fichier protégé par mot de passe a été ouvert par un utilisateur, d’autres utilisateurs ne sont pas autorisés à ouvrir le même fichier.  
  
 Le tableau suivant affiche les mots clés minimums requis pour se connecter à chaque pilote, et fournit un exemple de mots clés / paires de valeur utilisés avec **SQLDriverConnect**. Pour une liste complète des valeurs DRIVERID, voir [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote Paradox, le conducteur se connectera à l’annuaire actuel.  
  
|Pilote|Mots-clés requis|Exemple|  
|------------|-----------------------|-------------|  
|Paradoxe|Pilote, DriverID|DriverMD Microsoft Paradox Driver (md.db)MD; DBQ-c: Temp;DriverID-26|
