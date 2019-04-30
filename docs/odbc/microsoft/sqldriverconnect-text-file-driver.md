---
title: SQLDriverConnect (Text File Driver) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 715d51aeccf3085b8f98cd4b49b4a14efa87afe9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238326"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de se connecter à un pilote sans création d’une source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**, et **FIL**.  
  
 Le tableau suivant montre les mots-clés minimales requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir une liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote de texte, le pilote se connecte dans le répertoire actif.  
  
|Pilote|Mots clés requis|Exemples|  
|------------|-----------------------|--------------|  
|Text|Pilote|Driver={Microsoft Text Driver (*.txt;\*.csv)}; DefaultDir=c:\temp|
