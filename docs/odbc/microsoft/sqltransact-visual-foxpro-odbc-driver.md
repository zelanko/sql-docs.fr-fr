---
title: SQLTransact (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1581cb7ecc694dc9adcbb03d83cf73a6ba41dbed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270040"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau principal  
  
 Demande une opération commit ou rollback pour toutes les opérations actives sur tous les descripteurs d’instruction (*hstmt*s) associé à une connexion ou pour toutes les connexions associées le handle d’environnement, *henv*. **SQLTransact** fonctionne uniquement pour les sources de données qui sont [bases de données](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Si une validation échoue en mode manuel, la transaction reste active ; Vous pouvez choisir de restaurer la transaction ou recommencez l’opération de validation. Si une opération de validation échoue en mode de transaction automatique, la transaction est restaurée automatiquement ; la transaction ne peut pas être inactive.  
  
 Pour plus d’informations, consultez [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) dans le *de référence du programmeur ODBC*.
