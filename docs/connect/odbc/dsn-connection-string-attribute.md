---
title: Chaînes de connexion et la source de données des mots clés pour le pilote ODBC - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/04/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: MightyPen
ms.author: v-jizho2
author: karinazhou
manager: craigg
ms.openlocfilehash: e2db3b8df9ea63c16e0e96af9df42b7c22adaf80
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662873"
---
# <a name="dsn-and-connection-string-keywords-and-attributes"></a>Attributs et mots clés de chaîne de connexion et DSN

Cette page répertorie les mots clés des chaînes de connexion et les sources de données et les attributs de connexion de SQLSetConnectAttr et SQLGetConnectAttr, disponible dans le pilote ODBC pour SQL Server.

## <a name="supported-dsnconnection-string-keywords-and-connection-attributes"></a>Mots clés de chaîne de connexion/DSN et les attributs de connexion pris en charge

Le tableau suivant répertorie les mots clés disponibles et les attributs de chaque plateforme (L: Linux ; M : Mac ; W : Windows). Cliquez sur le mot clé ou un attribut pour plus d’informations.

| Mot clé de chaîne de connexion / DSN | Attribut de connexion | Plateforme |
|-|-|-|
| [Addr](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [Adresse](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [AnsiNPW](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ANSI_NPW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssansinpw) | DANS LA LMW |
| [APP](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [ApplicationIntent](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_APPLICATION_INTENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssapplicationintent) | DANS LA LMW |
| [AttachDBFileName](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ATTACHDBFILENAME](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssattachdbfilename) | DANS LA LMW |
| [Authentification](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sqlcoptssauthentication) | [SQL_COPT_SS_AUTHENTICATION](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sqlcoptssauthentication) | DANS LA LMW |
| [AutoTranslate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRANSLATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstranslate) | DANS LA LMW |
| [ColumnEncryption](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sqlcoptsscolumnencryption) | [SQL_COPT_SS_COLUMN_ENCRYPTION](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sqlcoptsscolumnencryption) | DANS LA LMW |
| [ConnectRetryCount](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | [SQL_COPT_SS_CONNECT_RETRY_COUNT](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | W |
| [ConnectRetryInterval](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | [SQL_COPT_SS_CONNECT_RETRY_INTERVAL](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | W |
| [Sauvegarde de la base de données](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_ATTR_CURRENT_CATALOG](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | DANS LA LMW |
| [Description](../../connect/odbc/dsn-connection-string-attribute.md#description) | | DANS LA LMW |
| [Driver](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [DSN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [Encrypt](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ENCRYPT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssencrypt) | DANS LA LMW |
| [Failover_Partner](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_FAILOVER_PARTNER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssfailoverpartner) | W |
| [FailoverPartnerSPN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_FAILOVER_PARTNER_SPN](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | W |
| [FileDSN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [KeystoreAuthentication](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | DANS LA LMW |
| [KeystorePrincipalId](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | DANS LA LMW |
| [KeystoreSecret](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | DANS LA LMW |
| [Langage](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [MARS_Connection](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_MARS_ENABLED](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssmarsenabled) | DANS LA LMW |
| [MultiSubnetFailover](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_MULTISUBNET_FAILOVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssmultisubnetfailover) | DANS LA LMW |
| [Net](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [Network](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [PWD](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [QueryLog_On](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfquery) | W |
| [QueryLogFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY_LOG](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfquerylog) | W |
| [QueryLogTIme](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY_INTERVAL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfqueryinterval) | W |
| [QuotedId](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_QUOTED_IDENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssquotedident) | DANS LA LMW |
| [Regional](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [SaveFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [Server](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [ServerSPN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_SERVER_SPN](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | DANS LA LMW |
| [StatsLog_On](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdata) | W |
| [StatsLogFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_DATA_LOG](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalog) | W |
| [TransparentNetworkIPResolution](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sqlcoptsstnir) | [SQL_COPT_SS_TNIR](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sqlcoptsstnir) | DANS LA LMW |
| [Trusted_Connection](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_INTEGRATED_SECURITY](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssintegratedsecurity) | DANS LA LMW |
| [TrustServerCertificate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRUST_SERVER_CERTIFICATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstrustservercertificate) | DANS LA LMW |
| [UID](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| [UseFMTONLY](../../connect/odbc/dsn-connection-string-attribute.md#usefmtonly) | | DANS LA LMW |
| [WSID](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | DANS LA LMW |
| | [SQL_ATTR_ACCESS_MODE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_ACCESS_MODE) | DANS LA LMW |
| | [SQL_ATTR_ASYNC_DBC_EVENT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_PCALLBACK](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_PCONTEXT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_ENABLE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_AUTO_IPD](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | DANS LA LMW |
| | [SQL_ATTR_AUTOCOMMIT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_AUTOCOMMIT) | DANS LA LMW |
| | [SQL_ATTR_CONNECTION_DEAD](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | DANS LA LMW |
| | [SQL_ATTR_CONNECTION_TIMEOUT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | DANS LA LMW |
| | [SQL_ATTR_DBC_INFO_TOKEN](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | DANS LA LMW |
| | [SQL_ATTR_LOGIN_TIMEOUT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_LOGIN_TIMEOUT) | DANS LA LMW |
| | [SQL_ATTR_METADATA_ID](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | DANS LA LMW |
| | [SQL_ATTR_ODBC_CURSORS](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_ODBC_CURSORS) | DANS LA LMW |
| | [SQL_ATTR_PACKET_SIZE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_PACKET_SIZE) | DANS LA LMW |
| | [SQL_ATTR_QUIET_MODE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_QUIET_MODE) | DANS LA LMW |
| | [SQL_ATTR_RESET_CONNECTION](../../odbc/reference/develop-driver/upgrading-a-3-5-driver-to-a-3-8-driver.md#connection-pooling) <br> (SQL_COPT_SS_RESET_CONNECTION) | DANS LA LMW |  
| | [SQL_ATTR_TRACE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_OPT_TRACE) | DANS LA LMW |
| | [SQL_ATTR_TRACEFILE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_OPT_TRACEFILE) | DANS LA LMW |
| | [SQL_ATTR_TRANSLATE_LIB](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TRANSLATE_DLL) | DANS LA LMW |
| | [SQL_ATTR_TRANSLATE_OPTION](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TRANSLATE_OPTION) | DANS LA LMW |
| | [SQL_ATTR_TXN_ISOLATION](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TXN_ISOLATION) | DANS LA LMW |
| | [SQL_COPT_SS_ACCESS_TOKEN](dsn-connection-string-attribute.md#sqlcoptssaccesstoken) | DANS LA LMW |
| | [SQL_COPT_SS_ANSI_OEM](dsn-connection-string-attribute.md#sqlcoptssansioem)| W |
| | [SQL_COPT_SS_BCP](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbcp) | DANS LA LMW |
| | [SQL_COPT_SS_BROWSE_CACHE_DATA](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) | DANS LA LMW |
| | [SQL_COPT_SS_BROWSE_CONNECT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseconnect) | DANS LA LMW |
| | [SQL_COPT_SS_BROWSE_SERVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseserver) | DANS LA LMW |
| | [SQL_COPT_SS_CEKEYSTOREDATA](dsn-connection-string-attribute.md#sqlcoptsscekeystoredata) | DANS LA LMW |
| | [SQL_COPT_SS_CEKEYSTOREPROVIDER](dsn-connection-string-attribute.md#sqlcoptsscekeystoreprovider) | DANS LA LMW |
| | [SQL_COPT_SS_CLIENT_CONNECTION_ID](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) | DANS LA LMW |
| | [SQL_COPT_SS_CONCAT_NULL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconcatnull) | DANS LA LMW |
| | [SQL_COPT_SS_CONNECTION_DEAD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconnectiondead) | DANS LA LMW |
| | [SQL_COPT_SS_ENLIST_IN_DTC](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssenlistindtc) | W |
| | [SQL_COPT_SS_ENLIST_IN_XA](dsn-connection-string-attribute.md#sql_copt_ss_enlist_in_xa) | DANS LA LMW |
| | [SQL_COPT_SS_FALLBACK_CONNECT](dsn-connection-string-attribute.md#sqlcoptssfallbackconnect) | DANS LA LMW |
| | [SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | DANS LA LMW |
| | [SQL_COPT_SS_MUTUALLY_AUTHENTICATED](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | DANS LA LMW |
| | [SQL_COPT_SS_OLDPWD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssoldpwd) | DANS LA LMW |
| | [SQL_COPT_SS_PERF_DATA_LOG_NOW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalognow) | W |
| | [SQL_COPT_SS_PRESERVE_CURSORS](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsspreservecursors) | DANS LA LMW |
| | [SQL_COPT_SS_TXN_ISOLATION](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstxnisolation) | DANS LA LMW |
| | [SQL_COPT_SS_USER_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssuserdata) | DANS LA LMW |
| | [SQL_COPT_SS_WARN_ON_CP_ERROR](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsswarnoncperror) | DANS LA LMW |


Voici quelques mots clés de chaîne de connexion et les attributs de connexion qui ne sont pas documentées dans [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md), [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) et [Fonction SQLSetConnectAttr](../../odbc/reference/syntax/sqlsetconnectattr-function.md).

### <a name="description"></a>Description

Utilisé pour décrire la source de données.

### <a name="sqlcoptssansioem"></a>SQL_COPT_SS_ANSI_OEM

Contrôles ANSI pour la conversion des données OEM. 

| Valeur d'attribut | Description |
|-|-|
| SQL_AO_OFF | (Valeur par défaut) Aucune conversion n’est effectuée. |
| SQL_AO_ON | Traduction est effectuée. |

### <a name="sqlcoptssfallbackconnect"></a>SQL_COPT_SS_FALLBACK_CONNECT

Contrôle l’utilisation de connexions de secours de SQL Server. Celle-ci n’est plus pris en charge.

| Valeur d'attribut | Description |
|-|-|
| SQL_FB_OFF | (Valeur par défaut) Connexions de secours sont désactivées. |
| SQL_FB_ON | Connexions de secours sont activées. |



## <a name="new-connection-string-keywords-and-connection-attributes"></a>Nouveau Connection String Keywords et les attributs de connexion

###  <a name="authentication---sqlcoptssauthentication"></a>Authentification - SQL_COPT_SS_AUTHENTICATION

Définit le mode d’authentification à utiliser lors de la connexion à SQL Server. Consultez [à l’aide d’Azure Active Directory](using-azure-active-directory.md) pour plus d’informations.

| Valeur de mot clé | Valeur d'attribut | Description |
|-|-|-|
| |SQL_AU_NONE|(Valeur par défaut) Pas définie. Combinaison d’autres attributs détermine le mode d’authentification.|
|SqlPassword|SQL_AU_PASSWORD|Authentification SQL Server avec nom d’utilisateur et mot de passe.|
|ActiveDirectoryIntegrated|SQL_AU_AD_INTEGRATED|Authentification intégrée à Azure Active Directory.|
|ActiveDirectoryPassword|SQL_AU_AD_PASSWORD|Authentification par mot de passe Azure Active Directory.|
|ActiveDirectoryInteractive|SQL_AU_AD_INTERACTIVE|Authentification interactive Azure Active Directory.|
|ActiveDirectoryMsi|SQL_AU_AD_MSI|Authentification Azure Active Directory Managed Service Identity. Pour l’identité affectée à l’utilisateur, UID est défini sur l’ID d’objet de l’identité de l’utilisateur. |
| |SQL_AU_RESET|Annuler la définition. Remplace tout DSN ou un paramètre de chaîne de connexion.|

> [!NOTE]
> Lorsque vous utilisez `Authentication` mot clé ou un attribut, vous devez explicitement spécifier `Encrypt` définissant la valeur souhaitée dans la chaîne de connexion / DSN / attribut de connexion. Reportez-vous à [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) pour plus d’informations.

### <a name="columnencryption---sqlcoptsscolumnencryption"></a>ColumnEncryption - SQL_COPT_SS_COLUMN_ENCRYPTION

Contrôle le chiffrement transparent de colonne (Always Encrypted). Consultez [à l’aide de toujours chiffré (ODBC)](using-always-encrypted-with-the-odbc-driver.md) pour plus d’informations.

| Valeur de mot clé | Valeur d'attribut | Description |
|-|-|-|
|Activé|SQL_CE_ENABLED|Active Always Encrypted.|
|Désactivé|SQL_CE_DISABLED|(Valeur par défaut) Désactive Always Encrypted.|
| |SQL_CE_RESULTSETONLY|Permet le déchiffrement uniquement (résultats et valeurs de retour).|

### <a name="transparentnetworkipresolution---sqlcoptsstnir"></a>TransparentNetworkIPResolution - SQL_COPT_SS_TNIR

Tente de la fonctionnalité de résolution d’adresses IP réseau Transparent, qui interagit avec MultiSubnetFailover pour autoriser une reconnexion plus rapide de contrôles. Consultez [résolution d’adresses IP de réseau Transparent à l’aide de](using-transparent-network-ip-resolution.md) pour plus d’informations.

| Valeur de mot clé | Valeur d'attribut| Description |
|-|-|-|
|Oui|SQL_IS_ON|(Par défaut) Active la résolution transparente d’adresses IP réseau.|
|Non|SQL_IS_OFF|Désactive la résolution d’adresses IP réseau transparente.|

### <a name="usefmtonly"></a>UseFMTONLY

Contrôle l’utilisation de SET FMTONLY pour les métadonnées lors de la connexion à SQL Server 2012 et les versions ultérieures.

| Valeur de mot clé | Description |
|-|-|
|Non|(Valeur par défaut) Utiliser sp_describe_first_result_set pour les métadonnées si elle est disponible. |
|Oui| Utilisez SET FMTONLY pour les métadonnées. |

### <a name="sqlcoptssaccesstoken"></a>SQL_COPT_SS_ACCESS_TOKEN

Autorise l’utilisation d’un jeton d’accès Azure Active Directory pour l’authentification. Consultez [à l’aide d’Azure Active Directory](using-azure-active-directory.md) pour plus d’informations.

| Valeur d'attribut | Description |
|-|-|
| NULL | (Valeur par défaut) Aucun jeton d’accès n’est fourni. |
| ACCESSTOKEN* | Pointeur vers un jeton d’accès. |

### <a name="sqlcoptsscekeystoredata"></a>SQL_COPT_SS_CEKEYSTOREDATA

Communique avec une bibliothèque de fournisseur de magasin de clés chargé. Consultez le chiffrement de colonne transparent de contrôles (Always Encrypted). Cet attribut n’a aucune valeur par défaut. Consultez [fournisseurs de magasin de clés personnalisés](custom-keystore-providers.md) pour plus d’informations.

| Valeur d'attribut | Description |
|-|-|
| CEKEYSTOREDATA * | Structure de données de communication pour la bibliothèque de fournisseur de magasin de clés |

### <a name="sqlcoptsscekeystoreprovider"></a>SQL_COPT_SS_CEKEYSTOREPROVIDER

Charge une bibliothèque de fournisseur de magasin de clés pour Always Encrypted, ou récupère les noms des bibliothèques de fournisseur de magasin de clés chargé. Consultez [fournisseurs de magasin de clés personnalisés](custom-keystore-providers.md) pour plus d’informations. Cet attribut n’a aucune valeur par défaut.

| Valeur d'attribut | Description |
|-|-|
| char * | Chemin d’accès à une bibliothèque de fournisseur de magasin de clés |

### <a name="sqlcoptssenlistinxa"></a>SQL_COPT_SS_ENLIST_IN_XA

Pour activer les transactions XA avec un processeur compatible XA Transaction (TP), l’application doit appeler **SQLSetConnectAttr** avec sql_copt_ss_enlist_in_xa ayant et un pointeur vers un `XACALLPARAM` objet. Cette option est prise en charge sur Windows, Linux (17.3 et versions ultérieures) et Mac.
```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, param, SQL_IS_POINTER);  // XACALLPARAM *param
``` 
 Pour associer une transaction XA avec une connexion ODBC uniquement, fournir TRUE ou FALSE sql_copt_ss_enlist_in_xa ayant au lieu du pointeur lors de l’appel **SQLSetConnectAttr**. Cela est uniquement valide sur Windows et ne peut pas être utilisé pour spécifier les opérations XA via une application cliente. 
 ```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, (SQLPOINTER)TRUE, 0);
``` 

|Valeur|Description|Plateformes|  
|-----------|-----------------|-----------------|  
|Objet XACALLPARAM *|Le pointeur vers `XACALLPARAM` objet.|Windows, Linux et Mac|
|TRUE|Associe la transaction XA à la connexion ODBC. Toutes les activités de base de données connexes seront effectuées sous la protection de la transaction XA.|Windows|  
|FALSE|Dissocie la transaction avec la connexion ODBC.|Windows|

 Consultez [à l’aide des Transactions XA](../../connect/odbc/use-xa-with-dtc.md) pour plus d’informations sur les transactions XA.
