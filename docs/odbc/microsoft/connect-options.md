---
title: Options de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25cfe2a897b0c312f91cd0c1e41ad6fa11725ab8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281309"
---
# <a name="connect-options"></a>Options de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Ces options permettent de personnaliser la connexion à la base de données au sein d’une application.  
  
|Option Connect|Notes|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit valider ou restaurer explicitement des transactions avec [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Cet attribut de connexion est implémenté dans le gestionnaire de pilotes.|  
|SQL_OPT_TRACE|Cet attribut de connexion est implémenté dans le gestionnaire de pilotes.|  
|SQL_OPT_TRACEFILE|Cet attribut de connexion est implémenté dans le gestionnaire de pilotes.|  
|SQL_TRANSLATE_DLL|Retourne l’erreur : « pilote non conforme ».|  
|SQL_TRANSLATE_OPTION|Valeur 32 bits passée à translation. dll.|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Les vParams suivants ne sont pas pris en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Cet attribut de connexion ODBC 3,0 vous permet d’utiliser le pilote ODBC pour Oracle dans des transactions distribuées coordonnées par les services de composants Microsoft (ou MTS, si vous utilisez Windows NT). Il fournit le pointeur d’interface *pITransaction* à la transaction en tant qu’argument *vParam* .|  
|SQL_ATTR_CONNECTION_DEAD|Cet attribut de connexion ODBC 3,5 en lecture seule vous permet de déterminer si la connexion au serveur Oracle a échoué. Obtient uniquement. Impossible de définir.|
