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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4358756deaa595ee5e10df0490522631201b9c87
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023376"
---
# <a name="connect-options"></a>Options de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Ces options permettent la personnalisation de la connexion de base de données au sein d’une application.  
  
|Option de connexion|Notes|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit explicitement valider ou restaurer les transactions avec [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_OPT_TRACE|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_OPT_TRACEFILE|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_TRANSLATE_DLL|Retourne une erreur : « Driver non compatibles avec ».|  
|SQL_TRANSLATE_OPTION|Une valeur 32 bits est passé à la DLL de traduction.|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Les vParams suivantes ne sont pas prises en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Cet attribut de connexion ODBC 3.0 vous permet d’utiliser le pilote ODBC pour Oracle dans des transactions distribuées coordonnées par les Services de composants de Microsoft (ou MTS, si vous utilisez Windows NT). Il fournit le pointeur d’interface *pITransaction* à la transaction en tant que le *vParam* argument.|  
|SQL_ATTR_CONNECTION_DEAD|Cet attribut de connexion ODBC 3.5 en lecture seule vous permet de déterminer si la connexion au serveur Oracle a échoué. Get uniquement ; Impossible de définir.|
