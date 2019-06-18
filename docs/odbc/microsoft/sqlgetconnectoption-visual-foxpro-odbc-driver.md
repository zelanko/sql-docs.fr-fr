---
title: SQLGetConnectOption (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62f1033abeaa32499602534f7f43b17fefe55ce9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313181"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Partielle  
  
 Conformité d’API ODBC : Niveau 1  
  
 Retourne le paramètre actuel d’une option de connexion. Cette fonction est partiellement prises en charge : Le pilote prend en charge toutes les valeurs pour le *fOption* argument mais ne prend ne pas en charge certaines des *vParam* valeurs pour le *fOption* argument SQL_TXN_ISOLATION.  
  
 Le tableau suivant décrit uniquement les arguments avec un comportement spécifique à l’implémentation pilote ODBC Visual FoxPro de **SQLGetConnectOption**.  
  
|*fOption*|Notes|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit explicitement valider ou restaurer les transactions avec [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); le pilote ODBC Visual FoxPro ne valide pas automatiquement une instruction transactable à l’achèvement. Le pilote commence une transaction si l’instruction est transactable.|  
|SQL_CURRENT_QUALIFIER|Peut être un nom qualifié complet de la base de données (fichier .dbc) ou le chemin d’accès complet à un répertoire qui contient zéro ou plusieurs tables (fichiers .dbf).|  
|SQL_LOGINTIMEOUT|Retourne une erreur « Pilotes non compatibles avec ».|  
|SQL_CURSORS|Retourne une erreur « Pilotes non compatibles avec ».|  
|SQL_PACKET_SIZE|Retourne une erreur « Pilotes non compatibles avec ».|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Ce qui suit *vParam*s ne sont pas prises en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Pour plus d’informations, consultez [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) dans le *de référence du programmeur ODBC*.
