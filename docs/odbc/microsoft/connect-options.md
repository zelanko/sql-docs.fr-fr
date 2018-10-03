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
manager: craigg
ms.openlocfilehash: 06695bf1770c9e362decac5702dcd924d47c23bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750463"
---
# <a name="connect-options"></a>Options de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Ces options permettent la personnalisation de la connexion de base de données au sein d’une application.  
  
|Option de connexion|Remarques|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit explicitement valider ou restaurer les transactions avec [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_OPT_TRACE|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_OPT_TRACEFILE|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_TRANSLATE_DLL|Retourne l’erreur : « Driver non compatibles avec ».|  
|SQL_TRANSLATE_OPTION|Une valeur 32 bits est passé à la DLL de traduction.|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Les vParams suivantes ne sont pas prises en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Cet attribut de connexion ODBC 3.0 vous permet d’utiliser le pilote ODBC pour Oracle dans des transactions distribuées coordonnées par les Services de composants de Microsoft (ou MTS, si vous utilisez Windows NT). Il fournit le pointeur d’interface *pITransaction* à la transaction en tant que le *vParam* argument.|  
|SQL_ATTR_CONNECTION_DEAD|Cet attribut de connexion ODBC 3.5 en lecture seule vous permet de déterminer si la connexion au serveur Oracle a échoué. Get uniquement ; Impossible de définir.|
