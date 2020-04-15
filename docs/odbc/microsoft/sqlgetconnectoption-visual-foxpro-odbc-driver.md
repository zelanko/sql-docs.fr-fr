---
title: SQLGetConnectOption (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2dd801988343ded46305665ab2a99aa4e7d76cba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298629"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Partielle  
  
 Conformité API ODBC: Niveau 1  
  
 Retourne le paramètre actuel d’une option de connexion. Cette fonction est partiellement soutenue: Le conducteur prend en charge toutes les valeurs pour *l’argument fOption,* mais ne supporte pas certaines des valeurs *vParam* pour *l’argument fOption* SQL_TXN_ISOLATION.  
  
 Le tableau suivant ne décrit que les arguments avec un comportement spécifique à la mise en œuvre visual FoxPro ODBC Driver de **SQLGetConnectOption**.  
  
|*fOption*|Notes|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre demande doit explicitement valider ou annuler des transactions avec [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); le visual FoxPro ODBC Driver ne commet pas automatiquement une déclaration de transaction à la fin. Le conducteur commence une transaction si l’instruction est transactionnable.|  
|SQL_CURRENT_QUALIFIER|Peut être un nom de base de données entièrement qualifié (.dbc fichier) ou le chemin entièrement qualifié vers un répertoire contenant zéro ou plus de tables (.dbf fichiers).|  
|SQL_LOGINTIMEOUT|Retourne l’erreur «Driver Not Capable».|  
|SQL_CURSORS|Retourne l’erreur «Driver Not Capable».|  
|SQL_PACKET_SIZE|Retourne l’erreur «Driver Not Capable».|  
|SQL_TXN_ISOLATION|Le conducteur n’autorise que SQL_TXN_READ_COMMITTED.<br /><br /> Les *vParam*suivants ne sont pas pris en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Pour plus d’informations, voir [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) dans la *référence du programmeur ODBC*.
