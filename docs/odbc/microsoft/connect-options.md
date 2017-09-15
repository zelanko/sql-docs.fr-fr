---
title: Les Options de connexion | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9bb45857d47ef145c5693f6718696cbf75ccd666
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connect-options"></a>Les Options de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Ces options permettent de personnaliser la connexion de base de données dans une application.  
  
|Option de connexion|Remarques|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit explicitement valider ou annuler les transactions avec [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_OPT_TRACE|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_OPT_TRACEFILE|Cet attribut de connexion est implémenté dans le Gestionnaire de pilotes.|  
|SQL_TRANSLATE_DLL|Retourne l’erreur : « Driver non compatibles avec ».|  
|SQL_TRANSLATE_OPTION|Une valeur 32 bits est passé à la DLL de traduction.|  
|SQL_TXN_ISOLATION|Le pilote permet uniquement de SQL_TXN_READ_COMMITTED.<br /><br /> Les vParams suivantes ne sont pas prises en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Cet attribut de connexion ODBC 3.0 vous permet d’utiliser le pilote ODBC Oracle dans des transactions distribuées coordonnées par les Services de composants de Microsoft (ou MTS, si vous utilisez Windows NT). Il fournit le pointeur d’interface *pITransaction* à la transaction en tant que le *vParam* argument.|  
|SQL_ATTR_CONNECTION_DEAD|Cet attribut de connexion ODBC 3.5 en lecture seule vous permet de déterminer si la connexion au serveur Oracle a échoué. Obtenir uniquement ; Impossible de définir.|
