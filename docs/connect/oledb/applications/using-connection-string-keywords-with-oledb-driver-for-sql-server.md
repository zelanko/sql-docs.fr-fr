---
title: Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server | Microsoft Docs
description: Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: pelopes
ms.openlocfilehash: cf754729c99d8826072b6b97acfc99a9986a9abc
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381875"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Certains OLE DB pilote pour SQL Server API utilisent des chaînes de connexion pour spécifier les attributs de connexion. Les chaînes de connexion sont des listes de mots clés et de valeurs associées ; chaque mot clé identifie un attribut de connexion particulier.  
  
> [!NOTE]
> OLE DB Driver pour SQL Server autorise l’ambiguïté dans les chaînes de connexion afin de maintenir la compatibilité descendante (par exemple, certains mots clés peuvent être spécifiés plusieurs fois et des mots clés en conflit peuvent être autorisés avec la résolution en fonction de la position ou de la précédence). Les versions ultérieures du pilote OLE DB pour SQL Server peuvent ne pas autoriser l’ambiguïté dans les chaînes de connexion. Lors de la modification d’applications, il est conseillé d’utiliser OLE DB Driver pour SQL Server pour éliminer toute dépendance vis-à-vis de l’ambiguïté des chaînes de connexion.  
  
 Les sections suivantes décrivent les mots clés qui peuvent être utilisés avec le pilote OLE DB pour SQL Server et ActiveX Data Objects (ADO) lors de l’utilisation de OLE DB pilote pour SQL Server en tant que fournisseur de données.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>Mots clés de chaîne de connexion OLE DB Driver  
 Il existe deux manières pour les applications OLE DB d'initialiser des objets source de données :  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Dans le premier cas, une chaîne du fournisseur peut être utilisée pour initialiser des propriétés de connexion en définissant la propriété DBPROP_INIT_PROVIDERSTRING dans le jeu de propriétés DBPROPSET_DBINIT. Dans le deuxième cas, une chaîne d’initialisation peut être passée à la méthode **IDataInitialize::GetDataSource** pour initialiser des propriétés de connexion. Les deux méthodes initialisent les mêmes propriétés de connexion OLE DB, mais des jeux de mots clés différents sont utilisés. L’ensemble de mots clés utilisé par **IDataInitialize::GetDataSource** est au minimum la description des propriétés présentes dans le groupe de propriétés d’initialisation.  
  
 Lorsqu'un paramètre de chaîne du fournisseur qui a une propriété OLE DB correspondante définie à une certaine valeur par défaut ou explicitement définie avec une valeur, la valeur de la propriété OLE DB remplace le paramètre dans la chaîne du fournisseur.  
  
 Les propriétés booléennes définies dans les chaînes du fournisseur via des valeurs DBPROP_INIT_PROVIDERSTRING sont définies à l'aide des valeurs « yes » et « no ». Les propriétés booléennes définies dans les chaînes d’initialisation à l’aide de **IDataInitialize::GetDataSource** sont définies à l’aide des valeurs « true » et « false ».  
  
 Les applications qui utilisent **IDataInitialize::GetDataSource** peuvent également utiliser les mots clés utilisés par **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois le mot clé **IDataInitialize::GetDataSource** et le mot clé **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé **IDataInitialize::GetDataSource** est utilisé. Il est fortement recommandé que les applications n’utilisent pas de mots clés **IDBInitialize::Initialize** dans les chaînes de connexion **IDataInitialize:GetDataSource**, car ce comportement peut ne pas être conservé dans les versions ultérieures.  
  
> [!NOTE]  
>  Une chaîne de connexion passée via **IDataInitialize::GetDataSource** est convertie en propriétés et appliquée via **IDBProperties::SetProperties**. Si les services de composants ont trouvé la description de la propriété dans **IDBProperties::GetPropertyInfo**, cette propriété sera appliquée comme une propriété autonome. Sinon, elle sera appliquée par le biais de la propriété DBPROP_PROVIDERSTRING. Par exemple, si vous spécifiez la chaîne de connexion **Data source = server1 ; Server = Server2**, la **source de données** sera définie en tant que propriété, mais le **serveur** passera dans une chaîne de fournisseur.  
  
 Si vous spécifiez plusieurs instances de la même propriété spécifique au fournisseur, la première valeur de la première propriété est utilisée.  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant DBPROP_INIT_PROVIDERSTRING avec **IDBInitialize::Initialize** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre accolades, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs d'attributs contiennent des signes non alphanumériques. Il est supposé que la première accolade fermante dans la valeur termine la valeur ; par conséquent, les valeurs ne peuvent pas contenir de caractères d'accolade fermante.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec DBPROP_INIT_PROVIDERSTRING.  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Synonyme de « Address ».|  
|**Adresse**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau du serveur exécutant une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** est généralement le nom réseau du serveur, mais il peut s’agir d’autres noms tels qu’un canal, une adresse IP ou un port TCP/IP et une adresse de socket.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La valeur de l' **adresse** est prioritaire sur la valeur transmise au **serveur** dans les chaînes de connexion lors de l’utilisation de OLE DB pilote pour SQL Server. Notez également que `Address=;` se connecte au serveur spécifié dans le mot clé **Server**, tandis que `Address= ;, Address=.;`, `Address=localhost;` et `Address=(local);` entraîne tous l’établissement d’une connexion au serveur local.<br /><br /> La syntaxe complète du mot clé **Address** est la suivante :<br /><br /> [_protocol_ **:** ]_Address_[ **,** _port &#124;\pipe\pipename_]<br /><br /> Le_protocole_ peut avoir la valeur **tcp** (TCP/IP), **lpc** (mémoire partagée) ou **np** (canaux nommés). Pour plus d'informations, consultez [Configure Client Protocols](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Si ni le _protocole_ ni le mot clé **Network** ne sont spécifiés, OLE DB pilote pour SQL Server utilisera l’ordre des protocoles spécifié dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.|   
|**APP**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour les [, consultez ](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server.|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé Database de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Authentification**<a href="#table1_1"><sup id="table1_authmode">**1**</sup></a>|SSPROP_AUTH_MODE|Spécifie l’authentification SQL ou Active Directory utilisée. Les valeurs valides sont :<br/><ul><li>`(not set)` : mode d’authentification déterminé par les autres mots clés.</li><li>`ActiveDirectoryPassword:`User l’authentification par ID et mot de passe avec une identité Azure Active Directory.</li><li>`ActiveDirectoryIntegrated:` l’authentification intégrée avec une identité Azure Active Directory.</li><br/>**Remarque :** Le mot clé `ActiveDirectoryIntegrated` peut également être utilisé pour l’authentification Windows pour SQL Server. Il remplace les mots clés d’authentification `Integrated Security` (ou `Trusted_Connection`). Il est **recommandé** que les applications qui utilisent des mots clés `Integrated Security` (ou `Trusted_Connection`) ou leurs propriétés correspondantes définissent la valeur du mot clé `Authentication` (ou de sa propriété correspondante) à `ActiveDirectoryIntegrated` pour activer le nouveau chiffrement et le comportement de validation de certificat .<br/><br/><li>`ActiveDirectoryInteractive:` l’authentification interactive avec une identité Azure Active Directory. Cette méthode prend en charge Azure Multi-Factor Authentication (MFA). </li><li>`ActiveDirectoryMSI:` [Managed Service Identity (MSI)](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) l’authentification. Pour une identité affectée par l’utilisateur, l’ID d’utilisateur doit être défini sur l’ID d’objet de l’identité de l’utilisateur.</li><li>`SqlPassword:` l’authentification à l’aide de l’ID d’utilisateur et du mot de passe.</li><br/>**Remarque :** Il est **recommandé** que les applications qui utilisent `SQL Server` authentification définissent la valeur du mot clé `Authentication` (ou de sa propriété correspondante) sur `SqlPassword` pour activer le [nouveau chiffrement et le comportement de validation des certificats](../features/using-azure-active-directory.md#encryption-and-certificate-validation).</ul>|
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « yes » et « no ».|  
|**Sauvegarde de la base de données**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|**Chiffrer**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide entraîne l’utilisation par le pilote OLE DB pour SQL Server d’utiliser le nom de principal du service par défaut généré par le fournisseur.|  
|**Langage**|SSPROPT_INIT_CURRENTLANGUAGE|Langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Spécifiez toujours **MultiSubnetFailover=Yes** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=Yes** configure OLE DB Driver pour SQL Server pour accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier. Les valeurs possibles sont **Yes** et **No**. La valeur par défaut est **No**. Par exemple :<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour les [, consultez ](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server.|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « yes » et « no » comme valeurs. Lorsque « no » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|**PWD**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur doit être le nom d'un serveur sur le réseau, une adresse IP ou le nom d'un alias du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Le mot clé **Address** remplace le mot clé **Server** .<br /><br /> Vous pouvez vous connecter à l’instance par défaut sur le serveur local en spécifiant l’un des éléments suivants :<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** *instancename* **;**<br /><br /> Pour plus d’informations sur la prise en charge de la base de données locale, consultez [OLE DB Driver for SQL Server Support pour](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)la base de données locale.<br /><br /> Pour spécifier une instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ajoutez **\\** _nom_instance_.<br /><br /> Si aucun serveur n'est spécifié, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La syntaxe complète du mot clé **Server** est la suivante :<br /><br /> **Server=** [_protocol_ **:** ]*Server*[ **,** _port_]<br /><br /> Le_protocole_ peut avoir la valeur **tcp** (TCP/IP), **lpc** (mémoire partagée) ou **np** (canaux nommés).<br /><br /> Voici un exemple de spécification d'un canal nommé :<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Cette ligne spécifie le protocole de canal nommé, un canal nommé sur l'ordinateur local (`\\.\pipe`), le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) et le nom par défaut du canal nommé (`sql/query`).<br /><br /> Si ni un *protocole* ni le mot clé **Network** ne sont spécifiés, OLE DB pilote pour SQL Server utilisera l’ordre des protocoles spécifié dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.<br /><br /> Les espaces sont ignorés au début de la valeur transmise au **serveur** dans les chaînes de connexion lors de l’utilisation de OLE DB pilote pour SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide entraîne l’utilisation par le pilote OLE DB pour SQL Server d’utiliser le nom de principal du service par défaut généré par le fournisseur.|  
|**Délai d'expiration**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Lorsque la valeur « yes » est spécifiée, fait en sorte que le pilote ODBC  Native Client utilise le mode d'authentification Windows pour la validation de connexion. Autrement, fait en sorte qu’OLE DB Driver pour SQL Server utilise un nom d’utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la validation de connexion, et les mots clés UID et PWD doivent être spécifiés.|  
|**TrustServerCertificate**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « yes » et « no » comme valeurs. La valeur par défaut est « no », ce qui signifie que le certificat de serveur sera validé.|  
|**UID**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|Contrôle la façon dont les métadonnées sont récupérées pendant la connexion à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».<br /><br />Par défaut, le pilote OLE DB pour SQL Server utilise des procédures stockées [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) et [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) pour récupérer des métadonnées. Ces procédures stockées présentent des limitations (par exemple, elles échouent lors de l’utilisation de tables temporaires). La définition de **UseFMTONLY** sur « Oui » indique au pilote d’utiliser à la place [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) pour la récupération des métadonnées.|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Ce mot clé est déconseillé et sa valeur est ignorée par le fournisseur OLE DB  Native Client.|  
|**WSID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
<b id="table1_1">[1] :</b> Pour améliorer la sécurité, le chiffrement et le comportement de validation de certificat sont modifiés lorsque vous utilisez les propriétés d’initialisation de jeton d’authentification/d’accès ou les mots clés de chaîne de connexion correspondants. Pour plus d’informations, consultez [chiffrement et validation des certificats](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 Les chaînes de connexion utilisées par les applications OLE DB utilisant **IDataInitialize::GetDataSource** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilisation des propriétés doit être conforme à la syntaxe autorisée dans l'étendue.  Par exemple, **WSID** utilise des accolades ( **{}** ) des guillemets et **nom de l’application** utilise des guillemets simples ( **'** ) ou doubles ( **"** ). Seules les propriétés de chaîne peuvent être mises entre guillemets. Si vous tentez de placer entre guillemets un entier ou une propriété énumérée, une erreur indiquant que la chaîne de connexion n'est pas conforme à la spécification OLE DB sera générée.  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets simples ou doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Le caractère de guillemet utilisé peut également apparaître dans des valeurs, à condition d'être doublé.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Si une chaîne de connexion a plusieurs des propriétés répertoriées dans le tableau suivant, la valeur de la dernière propriété sera utilisée.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec **IDataInitialize::GetDataSource** :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Jeton d'accès**<a href="#table2_1"><sup id="table2_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|Jeton d’accès utilisé pour l’authentification auprès de Azure Active Directory. <br/><br/>**Remarque :** Il s’agit d’une erreur pour spécifier ce mot clé et également `UID`, `PWD`, `Trusted_Connection` ou `Authentication` Mots clés de chaîne de connexion ou leurs propriétés/Mots clés correspondants.|
|**Application Name**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**Intention de l’application**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour les [, consultez ](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server.|  
|**Authentification**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|Spécifie l’authentification SQL ou Active Directory utilisée. Les valeurs valides sont :<br/><ul><li>`(not set)` : mode d’authentification déterminé par les autres mots clés.</li><li>`ActiveDirectoryPassword:`User l’authentification par ID et mot de passe avec une identité Azure Active Directory.</li><li>`ActiveDirectoryIntegrated:` l’authentification intégrée avec une identité Azure Active Directory.</li><br/>**Remarque :** Le mot clé `ActiveDirectoryIntegrated` peut également être utilisé pour l’authentification Windows pour SQL Server. Il remplace les mots clés d’authentification `Integrated Security` (ou `Trusted_Connection`). Il est **recommandé** que les applications qui utilisent des mots clés `Integrated Security` (ou `Trusted_Connection`) ou leurs propriétés correspondantes définissent la valeur du mot clé `Authentication` (ou de sa propriété correspondante) à `ActiveDirectoryIntegrated` pour activer le nouveau chiffrement et le comportement de validation de certificat .<br/><br/><li>`ActiveDirectoryInteractive:` l’authentification interactive avec une identité Azure Active Directory. Cette méthode prend en charge Azure Multi-Factor Authentication (MFA). </li><li>`ActiveDirectoryMSI:` [Managed Service Identity (MSI)](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) l’authentification. Pour une identité affectée par l’utilisateur, l’ID d’utilisateur doit être défini sur l’ID d’objet de l’identité de l’utilisateur.</li><li>`SqlPassword:` l’authentification à l’aide de l’ID d’utilisateur et du mot de passe.</li><br/>**Remarque :** Il est **recommandé** que les applications qui utilisent `SQL Server` authentification définissent la valeur du mot clé `Authentication` (ou de sa propriété correspondante) sur `SqlPassword` pour activer le [nouveau chiffrement et le comportement de validation des certificats](../features/using-azure-active-directory.md#encryption-and-certificate-validation).</ul>|
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Source de données**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Server** dans cette rubrique.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide entraîne l’utilisation par le pilote OLE DB pour SQL Server d’utiliser le nom de principal du service par défaut généré par le fournisseur.|  
|**Catalogue initial**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**Nom de fichier initial**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Sécurité intégrée**|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Spécifiez toujours **MultiSubnetFailover=True** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** configure OLE DB Driver pour SQL Server pour accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier. Les valeurs possibles sont **True** et **False**. La valeur par défaut est **False**. Par exemple :<br /><br /> `MultiSubnetFailover=True`<br /><br /> Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour les [, consultez ](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server.|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Address**, dans cette rubrique.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**Mot de passe**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|**Fournisseur**||Pour OLE DB pilote pour SQL Server, il doit s’agir de « MSOLEDBSQL ».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide entraîne l’utilisation par le pilote OLE DB pour SQL Server d’utiliser le nom de principal du service par défaut généré par le fournisseur.|  
|**Faire confiance au certificat de serveur**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|**Utiliser le chiffrement pour les données**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|Contrôle la façon dont les métadonnées sont récupérées pendant la connexion à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».<br /><br />Par défaut, le pilote OLE DB pour SQL Server utilise des procédures stockées [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) et [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) pour récupérer des métadonnées. Ces procédures stockées présentent des limitations (par exemple, elles échouent lors de l’utilisation de tables temporaires). L' **utilisation de FMTONLY** avec la valeur « true » indique au pilote d’utiliser à la place [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) pour la récupération des métadonnées.|  
|**ID d'utilisateur**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
<b id="table2_1">[1] :</b> Pour améliorer la sécurité, le chiffrement et le comportement de validation de certificat sont modifiés lorsque vous utilisez les propriétés d’initialisation de jeton d’authentification/d’accès ou les mots clés de chaîne de connexion correspondants. Pour plus d’informations, consultez [chiffrement et validation des certificats](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 **Remarque** Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe actuel (éventuellement périmé) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Mots clés de chaîne de connexion ActiveX Data Objects (ADO)  
 Les applications ADO définissent la propriété **ConnectionString** des objets **ADODBConnection** ou fournissent une chaîne de connexion comme paramètre à la méthode **Open** des objets **ADODBConnection**.  
  
 Les applications ADO peuvent également utiliser les mots clés utilisés par la méthode OLE DB **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois les mots clés ADO et les mots clés **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé ADO est utilisé. Il est vivement recommandé que les applications utilisent uniquement des mots clés de chaîne de connexion ADO.  
  
 Les chaînes de connexion utilisées par ADO ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Les valeurs d'attributs ne peuvent pas contenir de guillemets doubles.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec une chaîne de connexion ADO :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Jeton d'accès**<a href="#table3_1"><sup id="table3_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|Jeton d’accès utilisé pour l’authentification auprès de Azure Active Directory.<br/><br/>**Remarque :** Il s’agit d’une erreur pour spécifier ce mot clé et également `UID`, `PWD`, `Trusted_Connection` ou `Authentication` Mots clés de chaîne de connexion ou leurs propriétés/Mots clés correspondants.|
|**Intention de l’application**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour les [, consultez ](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server.|  
|**Application Name**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**Authentification**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|Spécifie l’authentification SQL ou Active Directory utilisée. Les valeurs valides sont :<br/><ul><li>`(not set)` : mode d’authentification déterminé par les autres mots clés.</li><li>`ActiveDirectoryPassword:`User l’authentification par ID et mot de passe avec une identité Azure Active Directory.</li><li>`ActiveDirectoryIntegrated:` l’authentification intégrée avec une identité Azure Active Directory.</li><br/>**Remarque :** Le mot clé `ActiveDirectoryIntegrated` peut également être utilisé pour l’authentification Windows pour SQL Server. Il remplace les mots clés d’authentification `Integrated Security` (ou `Trusted_Connection`). Il est **recommandé** que les applications qui utilisent des mots clés `Integrated Security` (ou `Trusted_Connection`) ou leurs propriétés correspondantes définissent la valeur du mot clé `Authentication` (ou de sa propriété correspondante) à `ActiveDirectoryIntegrated` pour activer le nouveau chiffrement et le comportement de validation de certificat .<br/><br/><li>`ActiveDirectoryInteractive:` l’authentification interactive avec une identité Azure Active Directory. Cette méthode prend en charge Azure Multi-Factor Authentication (MFA). </li><li>`ActiveDirectoryMSI:` [Managed Service Identity (MSI)](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) l’authentification. Pour une identité affectée par l’utilisateur, l’ID d’utilisateur doit être défini sur l’ID d’objet de l’identité de l’utilisateur.</li><li>`SqlPassword:` l’authentification à l’aide de l’ID d’utilisateur et du mot de passe.</li><br/>**Remarque :** Il est **recommandé** que les applications qui utilisent `SQL Server` authentification définissent la valeur du mot clé `Authentication` (ou de sa propriété correspondante) sur `SqlPassword` pour activer le [nouveau chiffrement et le comportement de validation des certificats](../features/using-azure-active-directory.md#encryption-and-certificate-validation).</ul>|
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Source de données**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Server** dans cette rubrique.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données qui sera utilisé. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide entraîne l’utilisation par le pilote OLE DB pour SQL Server d’utiliser le nom de principal du service par défaut généré par le fournisseur.|  
|**Catalogue initial**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**Nom de fichier initial**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Sécurité intégrée**|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Spécifiez toujours **MultiSubnetFailover=True** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** configure OLE DB Driver pour SQL Server pour accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier. Les valeurs possibles sont **True** et **False**. La valeur par défaut est **False**. Par exemple :<br /><br /> `MultiSubnetFailover=True`<br /><br /> Pour plus d’informations sur la prise en charge de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour les [, consultez ](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server.|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Address**, dans cette rubrique.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**Mot de passe**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes.|  
|**Fournisseur**||Pour OLE DB pilote pour SQL Server, il doit s’agir de « MSOLEDBSQL ».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide entraîne l’utilisation par le pilote OLE DB pour SQL Server d’utiliser le nom de principal du service par défaut généré par le fournisseur.|  
|**Faire confiance au certificat de serveur**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|**Utiliser le chiffrement pour les données**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|Contrôle la façon dont les métadonnées sont récupérées pendant la connexion à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».<br /><br />Par défaut, le pilote OLE DB pour SQL Server utilise des procédures stockées [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) et [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) pour récupérer des métadonnées. Ces procédures stockées présentent des limitations (par exemple, elles échouent lors de l’utilisation de tables temporaires). L' **utilisation de FMTONLY** avec la valeur « true » indique au pilote d’utiliser à la place [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) pour la récupération des métadonnées.|  
|**ID d'utilisateur**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
<b id="table3_1">[1] :</b> Pour améliorer la sécurité, le chiffrement et le comportement de validation de certificat sont modifiés lorsque vous utilisez les propriétés d’initialisation de jeton d’authentification/d’accès ou les mots clés de chaîne de connexion correspondants. Pour plus d’informations, consultez [chiffrement et validation des certificats](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 **Remarque** Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe actuel (éventuellement périmé) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
