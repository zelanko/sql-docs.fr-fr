---
title: Regroupement de connexions prenant en charge les pilotes dans ODBC Driver
description: Découvrez les améliorations apportées au regroupement de connexions prenant en charge les pilotes dans Microsoft ODBC Driver for SQL Server sur Windows.
ms.custom: ''
ms.date: 09/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1d8700e6868781480771c4a62f2a5fc6c92ddfc
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288101"
---
# <a name="driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server"></a>Regroupement de connexions prenant en charge le pilote dans le pilote ODBC pour SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le [regroupement de connexions prenant en charge les pilotes](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). Cette rubrique décrit les améliorations apportées au regroupement de connexions prenant en charge les pilotes dans Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Windows :  
  
-   Quelles que soient les propriétés de connexion, les connexions qui utilisent `SQLDriverConnect` arrivent dans un pool différent des connexions qui utilisent `SQLConnect`.
- Quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et le regroupement de connexions prenant en charge les pilotes, le pilote n’utilise pas le contexte de sécurité de l’utilisateur Windows pour le thread actuel afin de séparer les connexions dans le pool. Autrement dit, si les paramètres des connexions sont équivalents pour les scénarios d’emprunt d’identité Windows avec l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et qu’elles utilisent les mêmes informations d’identification pour l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour se connecter au serveur principal, différents utilisateurs Windows peuvent utiliser le même regroupement de connexions. Quand vous utilisez l’authentification Windows et le regroupement de connexions prenant en charge les pilotes, le pilote utilise le contexte de sécurité de l’utilisateur Windows actuel pour séparer les connexions dans le regroupement. Autrement dit, pour les scénarios d’emprunt d’identité Windows, les différents utilisateurs Windows ne partagent pas les connexions même si celles-ci utilisent les mêmes paramètres.
- Si vous utilisez Azure Active Directory et le regroupement de connexions avec prise en charge des pilotes, le pilote se sert également de la valeur d’authentification pour déterminer l’appartenance au pool de connexions.
  
-   Le regroupement de connexions prenant en charge les pilotes empêche une mauvaise connexion d’être retournée à partir du regroupement.  
  
-   Le regroupement de connexions prenant en charge les pilotes reconnaît les attributs de connexion spécifiques du pilote. Ainsi, si une connexion utilise `SQL_COPT_SS_APPLICATION_INTENT` en lecture seule, elle récupère son propre pool de connexions.
-   Si l’attribut `SQL_COPT_SS_ACCESS_TOKEN` est défini, la connexion est regroupée séparément. 
  
Si l’un des ID d’attribut de connexion ou des mots clés de chaîne de connexion suivants est différent entre votre chaîne de connexion et la chaîne de connexion regroupée, le pilote utilise une connexion regroupée. Toutefois, les performances sont meilleures si tous les ID d’attribut de connexion ou mots clés de chaîne de connexion correspondent. (Pour faire correspondre une connexion dans le regroupement, le pilote réinitialise l’attribut.) Les performances diminuent, car la réinitialisation des paramètres suivants nécessite un appel réseau supplémentaire.  
  
-    Si plusieurs des attributs de connexion ou mots clés de connexion suivants diffèrent, une connexion regroupée n’est pas utilisée.  
  
  - `Language`  
  - `QuoteId`  
  - `SQL_ATTR_TXN_ISOLATION` 
  - `SQL_COPT_SS_QUOTED_IDENT`  
  
-   En cas de différence dans l’un des mots clés de connexion suivants entre votre chaîne de connexion et une chaîne de connexion regroupée, une connexion regroupée n’est pas utilisée.  
  
    |Mot clé|ODBC Driver 17/13|ODBC Driver 11|
    |-|-|-|
    |`Address`|Oui|Oui|
    |`AnsiNPW`|Oui|Oui|
    |`App`|Oui|Oui|
    |`ApplicationIntent`|Oui|Oui|  
    |`Authentication`|Oui|Non|
    |`ColumnEncryption`|Oui|Non|
    |`Database`|Oui|Oui|
    |`Encrypt`|Oui|Oui|  
    |`Failover_Partner`|Oui|Oui|
    |`FailoverPartnerSPN`|Oui|Oui|
    |`MARS_Connection`|Oui|Oui|
    |`Network`|Oui|Oui|
    |`PWD`|Oui|Oui|
    |`Server`|Oui|Oui|
    |`ServerSPN`|Oui|Oui|
    |`TransparentNetworkIPResolution`|Oui|Oui|
    |`Trusted_Connection`|Oui|Oui|
    |`TrustServerCertificate`|Oui|Oui|
    |`UID`|Oui|Oui|
    |`WSID`|Oui|Oui|
    
- En cas de différence dans l’un des attributs de connexion suivants entre votre chaîne de connexion et une chaîne de connexion regroupée, une connexion regroupée n’est pas utilisée.  
  
    |Attribut|ODBC Driver 17/13|ODBC Driver 11|  
    |-|-|-|  
    |`SQL_ATTR_CURRENT_CATALOG`|Oui|Oui|
    |`SQL_ATTR_PACKET_SIZE`|Oui|Oui|
    |`SQL_COPT_SS_ANSI_NPW`|Oui|Oui|
    |`SQL_COPT_SS_ACCESS_TOKEN`|Oui|Non|
    |`SQL_COPT_SS_AUTHENTICATION`|Oui|Non|
    |`SQL_COPT_SS_ATTACHDBFILENAME`|Oui|Oui|
    |`SQL_COPT_SS_BCP`|Oui|Oui|
    |`SQL_COPT_SS_COLUMN_ENCRYPTION`|Oui|Non|
    |`SQL_COPT_SS_CONCAT_NULL`|Oui|Oui|
    |`SQL_COPT_SS_ENCRYPT`|Oui|Oui|
    |`SQL_COPT_SS_FAILOVER_PARTNER`|Oui|Oui|
    |`SQL_COPT_SS_FAILOVER_PARTNER_SPN`|Oui|Oui|
    |`SQL_COPT_SS_INTEGRATED_SECURITY`|Oui|Oui|
    |`SQL_COPT_SS_MARS_ENABLED`|Oui|Oui|
    |`SQL_COPT_SS_OLDPWD`|Oui|Oui|
    |`SQL_COPT_SS_SERVER_SPN`|Oui|Oui|
    |`SQL_COPT_SS_TRUST_SERVER_CERTIFICATE`|Oui|Oui|
    |`SSPROP_AUTH_REPL_SERVER_NAME`|Oui|Oui|
    |`SQL_COPT_SS_TNIR`|Oui|Non|
 
-   Le pilote peut réinitialiser et ajuster les mots clés et attributs de connexion suivants sans appel réseau supplémentaire. Le pilote réinitialise ces paramètres pour s’assurer que la connexion ne contient pas d’informations incorrectes.  
  
     Ces mots clés de connexion ne sont pas pris en considération quand le Gestionnaire de pilotes tente de faire correspondre votre connexion à une connexion dans le regroupement. (Même si vous modifiez l’un de ces paramètres, une connexion existante peut être réutilisée. Le pilote réinitialise les options, si nécessaire.) Ces attributs peuvent être réinitialisés côté client sans appel réseau supplémentaire.  
  
    |Mot clé|ODBC Driver 17/13|ODBC Driver 11|  
    |-|-|-|  
    |`AutoTranslate`|Oui|Oui|
    |`Description`|Oui|Oui|
    |`MultisubnetFailover`|Oui|Oui|  
    |`QueryLog_On`|Oui|Oui|
    |`QueryLogFile`|Oui|Oui|
    |`QueryLogTime`|Oui|Oui|
    |`Regional`|Oui|Oui|
    |`StatsLog_On`|Oui|Oui|
    |`StatsLogFile`|  Oui|Oui|
  
     Si vous modifiez l’un des attributs de connexion suivants, une connexion existante peut être réutilisée.  Le pilote réinitialise la valeur, si nécessaire. Le pilote peut réinitialiser ces attributs dans le client sans appel réseau supplémentaire.  
  
    |Attribut|ODBC Driver 17/13|ODBC Driver 11|  
    |-|-|-|  
    |Tous les attributs d’instruction|Oui|Oui|
    |`SQL_ATTR_AUTOCOMMIT`|Oui|Oui|
    |`SQL_ATTR_CONNECTION_TIMEOUT`|  Oui|Oui|
    |`SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT`|Oui|Oui|
    |`SQL_ATTR_LOGIN_TIMEOUT`|Oui|Oui|
    |`SQL_ATTR_ODBC_CURSORS`|  Oui|Oui|
    |`SQL_COPT_SS_PERF_DATA`|Oui|Oui|
    |`SQL_COPT_SS_PERF_DATA_LOG`|Oui|Oui|
    |`SQL_COPT_SS_PERF_DATA_LOG_NOW`| Oui|Oui| 
    |`SQL_COPT_SS_PERF_QUERY`|Oui|Oui|
    |`SQL_COPT_SS_PERF_QUERY_INTERVAL`|Oui|Oui|
    |`SQL_COPT_SS_PERF_QUERY_LOG`|  Oui|Oui|
    |`SQL_COPT_SS_PRESERVE_CURSORS`|Oui|Oui|
    |`SQL_COPT_SS_TRANSLATE`|Oui|Oui|
    |`SQL_COPT_SS_USER_DATA`|  Oui|Oui|
    |`SQL_COPT_SS_WARN_ON_CP_ERROR`|Oui|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft ODBC Driver for SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
