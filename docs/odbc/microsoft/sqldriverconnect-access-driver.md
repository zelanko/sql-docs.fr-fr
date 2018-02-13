---
title: SQLDriverConnect (Access Driver) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7362786d12678d90554cb0e7dab2d612fd061d2b
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access Driver)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Access. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de se connecter à un pilote sans création d’une source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**, et **FIL**.  
  
 Le **UID** et **PWD** mots clés sont également pris en charge.  
  
 Le mot clé de mot de passe ne doit pas inclure les caractères spéciaux (voir SQL_SPECIAL_CHARACTERS dans **SQLGetInfo** retourné de valeurs).  
  
 Le tableau suivant montre les mots clés minimales requises pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir une liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Microsoft Access|Driver, DBQ|Driver = {pilote Microsoft Access (*.mdb)} ; DBQ = c :\\\temp\\\sample.mdb|
