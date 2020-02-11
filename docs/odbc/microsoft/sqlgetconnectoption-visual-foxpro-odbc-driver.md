---
title: Sqlgetconnectoption, (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.openlocfilehash: c17cd473d3c96032817c2b183bf65fe360cf3cdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053685"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : partielle  
  
 Conformité de l’API ODBC : niveau 1  
  
 Retourne le paramètre actuel d’une option de connexion. Cette fonction est partiellement prise en charge : le pilote prend en charge toutes les valeurs pour l’argument *fOption* , mais ne prend pas en charge certaines des valeurs *vParam* pour l’argument *fOption* SQL_TXN_ISOLATION.  
  
 Le tableau suivant décrit uniquement les arguments avec un comportement spécifique à l’implémentation du pilote ODBC Visual FoxPro de **sqlgetconnectoption,**.  
  
|*fOption*|Notes|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit valider ou restaurer explicitement des transactions avec [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); le pilote ODBC Visual FoxPro ne valide pas automatiquement une instruction qui peut être validée après l’achèvement. Le pilote commence une transaction si l’instruction est une instruction.|  
|SQL_CURRENT_QUALIFIER|Il peut s’agir d’un nom de base de données qualifié complet (fichier. DBC) ou d’un chemin d’accès complet à un répertoire contenant zéro ou plusieurs tables (fichiers. dbf).|  
|SQL_LOGINTIMEOUT|Retourne l’erreur « pilote non conforme ».|  
|SQL_CURSORS|Retourne l’erreur « pilote non conforme ».|  
|SQL_PACKET_SIZE|Retourne l’erreur « pilote non conforme ».|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Les *vParam*s suivants ne sont pas pris en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Pour plus d’informations, consultez [sqlgetconnectoption,](../../odbc/reference/syntax/sqlgetconnectoption-function.md) dans le *Guide de référence du programmeur ODBC*.
