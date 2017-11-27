---
title: SQLDriverConnect (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4233d9785ae420a2634db0e97d226bc1c2abbc7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 1  
  
 Se connecte à une source de données, ce qui peut être soit un [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) ou un répertoire de [libre tables](../../odbc/microsoft/visual-foxpro-terminology.md). Mots clés attribut ODBC UID et PWD sont ignorés. Le tableau suivant répertorie les mots clés des attributs pris en charge supplémentaires.  
  
|Mot clé d’attribut ODBC|Valeur d'attribut|  
|----------------------------|---------------------|  
|DSN||  
|UID|Ignoré par le pilote ODBC Visual FoxPro, mais ne génère pas d’erreur.|  
|PWD|Ignoré par le pilote ODBC Visual FoxPro, mais ne génère pas d’erreur.|  
|Pilote|Le nom et l’emplacement du pilote ODBC de Visual FoxPro ; implémenté par le Gestionnaire de pilotes.|  
  
|Mot clé d’attribut Visual FoxPro ODBC Driver|Valeur d'attribut|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|« Oui » ou « Non »|  
|Copies assemblées|« Ordinateur » ou autres l’ordre de tri. Pour obtenir la liste des séquences de classement pris en charge, consultez [définir COLLATE](../../odbc/microsoft/set-collate-command.md).|  
| Description||  
|Exclusive|« Oui » ou « Non »|  
|SourceDB|Un chemin d’accès complet d’un répertoire contenant zéro ou plusieurs [libre tables](../../odbc/microsoft/visual-foxpro-terminology.md), ou le nom de fichier et le chemin absolu pour un [base de données](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|« DBC » ou « DBF »|  
|Version||  
  
 Si le nom de source de données n’est pas spécifié, le Gestionnaire de pilote invite l’utilisateur pour obtenir les informations (selon le paramètre de la *fDriverCompletion* argument), puis continue. Si plus d’informations est nécessaire, le pilote ODBC Visual FoxPro affiche la boîte de dialogue invite de commandes.  
  
 Pour plus d’informations, consultez [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) dans les *de référence du programmeur ODBC*.
