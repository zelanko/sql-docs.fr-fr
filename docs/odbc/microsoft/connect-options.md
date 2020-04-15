---
title: Connectez-vous aux options Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281309"
---
# <a name="connect-options"></a>Options de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Ces options permettent la personnalisation de la connexion de base de données au sein d’une application.  
  
|Connecter l’option|Notes|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre demande doit explicitement valider ou annuler des transactions avec [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Cet attribut de connexion est implémenté dans le Driver Manager.|  
|SQL_OPT_TRACE|Cet attribut de connexion est implémenté dans le Driver Manager.|  
|SQL_OPT_TRACEFILE|Cet attribut de connexion est implémenté dans le Driver Manager.|  
|SQL_TRANSLATE_DLL|Erreur de retour : « Pilote pas capable. »|  
|SQL_TRANSLATE_OPTION|Une valeur 32 bits transmise à la traduction .dll.|  
|SQL_TXN_ISOLATION|Le conducteur n’autorise que SQL_TXN_READ_COMMITTED.<br /><br /> Les vParams suivants ne sont pas pris en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Cet attribut de connexion ODBC 3.0 vous permet d’utiliser le pilote ODBC pour Oracle dans les transactions distribuées coordonnées par Microsoft Component Services (ou MTS, si vous utilisez Windows NT). Il fournit le pointeur d’interface *pITransaction* à la transaction comme l’argument *vParam.*|  
|SQL_ATTR_CONNECTION_DEAD|Cet attribut de connexion ODBC 3.5 uniquement lu vous permet de déterminer si la connexion au serveur Oracle a échoué. Obtenez seulement; ne peut pas définir.|
