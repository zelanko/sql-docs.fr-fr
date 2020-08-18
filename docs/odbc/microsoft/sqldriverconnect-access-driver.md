---
description: SQLDriverConnect (pilote Access)
title: SQLDriverConnect (pilote Access) | Microsoft Docs
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
ms.openlocfilehash: 52bbcbfa379be53ea24c150d2522242e85e61fea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449211"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**et **fil**.  
  
 Les mots clés **UID** et **PWD** sont également pris en charge.  
  
 Le mot clé PWD ne doit inclure aucun caractère spécial (voir SQL_SPECIAL_CHARACTERS dans **SQLGetInfo** valeurs retournées).  
  
 Le tableau suivant indique les mots clés minimaux requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir la liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Microsoft Access|Pilote, DBQ|Driver = {pilote Microsoft Access (*. mdb)}; DBQ = c : \\ \temp \\ \Sample.mdb|
