---
description: SQLDriverConnect (pilote de fichier texte)
title: SQLDriverConnect (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2eb5c35e9f6ae56caa3c6e4ca7473defe3b8bc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421803"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de vous connecter à un pilote sans créer de source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**et **fil**.  
  
 Le tableau suivant indique les mots clés minimaux requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir la liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote de texte, le pilote se connecte au répertoire actif.  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Texte|Pilote|Driver = {pilote Microsoft Text (*. txt ; \* . CSV)}; DefaultDir = c:\temp|
