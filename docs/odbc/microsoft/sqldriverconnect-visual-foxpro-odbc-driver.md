---
title: SQLDriverConnect (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc0bcf6a191f67b87b422b17778f56feda1f5227
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63238087"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 1  
  
 Se connecte à une source de données existante, qui peut être soit un [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) ou un répertoire de [gratuit tables](../../odbc/microsoft/visual-foxpro-terminology.md). Mots clés attribut ODBC UID et PWD sont ignorés. Le tableau suivant répertorie les mots clés d’attribut prises en charge supplémentaire.  
  
|Mot clé d’attribut ODBC|Valeur d'attribut|  
|----------------------------|---------------------|  
|DSN||  
|UID|Ignoré par le pilote ODBC Visual FoxPro, mais ne génère pas d’erreur.|  
|PWD|Ignoré par le pilote ODBC Visual FoxPro, mais ne génère pas d’erreur.|  
|Pilote|Le nom et l’emplacement du pilote ODBC de Visual FoxPro ; implémenté par le Gestionnaire de pilotes.|  
  
|Mot clé d’attribut Visual FoxPro ODBC Driver|Valeur d'attribut|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|« Oui » ou « Non »|  
|Copies assemblées|« Ordinateur » ou autre séquence de classement. Pour obtenir la liste de séquences de classement pris en charge, consultez [définir COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Description||  
|Exclusive|« Oui » ou « Non »|  
|SourceDB|Un chemin d’accès complet à un répertoire contenant zéro ou plusieurs [gratuit tables](../../odbc/microsoft/visual-foxpro-terminology.md), ou le nom de fichier et le chemin absolu pour un [base de données](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|« DBC » ou « DBF »|  
|Version||  
  
 Si le nom de source de données n’est pas spécifié, le Gestionnaire de pilotes invite l’utilisateur pour les informations (selon le paramètre de la *fDriverCompletion* argument), puis continue. Si plus d’informations est requis, le pilote ODBC Visual FoxPro affiche la boîte de dialogue invite.  
  
 Pour plus d’informations, consultez [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) dans le *de référence du programmeur ODBC*.
