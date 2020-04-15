---
title: SQLDriverConnect (pilote dBASE) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39d3d062ef8371ce37f812216cbb642d103eff98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302920"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (pilote dBASE)
> [!NOTE]  
>  Ce sujet fournit dBASE Des informations spécifiques au conducteur. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes: **DSN**, **DBQ**, et **FIL**.  
  
 Lorsque le pilote Paradox est utilisé, après l’ouverture d’un fichier protégé par mot de passe par un utilisateur, d’autres utilisateurs ne sont pas autorisés à ouvrir le même fichier.  
  
 Le tableau suivant affiche les mots clés minimums requis pour se connecter à chaque pilote, et fournit un exemple de mots clés / paires de valeur utilisés avec **SQLDriverConnect**. Pour une liste complète des valeurs DRIVERID, voir [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le dBASEdriver, le conducteur se connectera à l’annuaire actuel.  
  
|Pilote|Mots-clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Dbase|Pilote, DriverID|Driver microsoft dBASE Driver (.dbf)MD; DBQ-c: temp; DriverID 277|
