---
title: SQLDriverConnect (pilote dBASE) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 238931112d55214c239dab732f951a197d359615
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053923"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**et **fil**.  
  
 Lorsque le pilote Paradox est utilisé, les utilisateurs n’ont pas la possibilité d’ouvrir le même fichier après qu’un utilisateur a ouvert un fichier protégé par mot de passe.  
  
 Le tableau suivant indique les mots clés minimaux requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir la liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le dBASEdriver, le pilote se connecte au répertoire actif.  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|dBASE|Pilote, DriverID|Driver = {pilote Microsoft dBASE (*. dbf)}; DBQ = c:\temp ; DriverID = 277|
