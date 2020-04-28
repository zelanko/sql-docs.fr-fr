---
title: SQLDriverConnect (pilote ODBC Visual FoxPro) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e270f8c9be42dc109adeaa49acb84f29f2b9511
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307090"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Établit une connexion à une source de données existante, qui peut être soit une [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) , soit un répertoire de [tables libres](../../odbc/microsoft/visual-foxpro-terminology.md). Les mots clés d’attribut ODBC UID et PWD sont ignorés. Le tableau suivant répertorie les mots clés d’attribut pris en charge supplémentaires.  
  
|Mot clé d’attribut ODBC|Valeur d'attribut|  
|----------------------------|---------------------|  
|DSN||  
|Identificateur d’utilisateur|Ignoré par le pilote ODBC Visual FoxPro, mais ne génère pas d’erreur.|  
|PWD|Ignoré par le pilote ODBC Visual FoxPro, mais ne génère pas d’erreur.|  
|Pilote|Le nom et l’emplacement du pilote ODBC Visual FoxPro ; implémenté par le gestionnaire de pilotes.|  
  
|Mot clé d’attribut du pilote ODBC Visual FoxPro|Valeur d'attribut|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|« Oui » ou « non »|  
|Copies assemblées|« Machine » ou autre séquence de classement. Pour obtenir la liste des séquences de classement prises en charge, consultez [Set COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Description||  
|Exclusif|« Oui » ou « non »|  
|SourceDB|Chemin d’accès complet à un répertoire contenant zéro ou plusieurs [tables libres](../../odbc/microsoft/visual-foxpro-terminology.md), ou le chemin d’accès absolu et le nom de fichier d’une [base de données](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|« DBC » ou « DBF »|  
|Version||  
  
 Si le nom de la source de données n’est pas spécifié, le gestionnaire de pilotes invite l’utilisateur à entrer les informations (en fonction du paramètre de l’argument *fDriverCompletion* ), puis continue. Si des informations supplémentaires sont requises, le pilote ODBC Visual FoxPro affiche la boîte de dialogue d’invite de commandes.  
  
 Pour plus d’informations, consultez [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) dans le *Guide de référence du programmeur ODBC*.
