---
title: SQLDriverConnect (pilote Paradox) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f9265657327f71e41c124707ab66c8ad621bda55
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de Corel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de se connecter à un pilote sans création d’une source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**, et **FIL**.  
  
 Le **PWD** (mot clé) est également possible. Le mot clé de mot de passe ne doit pas inclure les caractères spéciaux (voir SQL_SPECIAL_CHARACTERS dans **SQLGetInfo** retourné de valeurs).  
  
 Une fois un fichier protégé par mot de passe a été ouvert par un utilisateur, les autres utilisateurs ne sont pas autorisés à ouvrir le même fichier.  
  
 Le tableau suivant montre les mots clés minimales requises pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir une liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote Paradox, le pilote se connecte au répertoire actif.  
  
|Pilote|Mots clés requis|Exemple|  
|------------|-----------------------|-------------|  
|Paradox|Pilote, DriverID|Driver = {Microsoft Paradox Driver (*.db)} ; DBQ = c:\temp ; DriverID = 26|

