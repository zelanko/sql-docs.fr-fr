---
title: Noms de Principal du service (SPN) dans les connexions clientes (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e212010e-a5b6-4ad1-a3c0-575327d3ffd3
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 556845b5ea0e393ecc50da610f1951e746c74c71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053279"
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Noms de principaux du service (SPN) dans les connexions clientes (OLE DB)
  Cette rubrique décrit les propriétés et fonctions membres OLE DB qui prennent en charge les noms de principaux du service (SPN) dans les applications clientes. Pour plus d’informations sur les SPN dans les applications clientes, consultez [nom Principal de Service &#40;SPN&#41; prise en charge dans les connexions clientes](../features/service-principal-name-spn-support-in-client-connections.md). Pour obtenir un exemple, consultez [l’authentification Kerberos intégrée &#40;OLE DB&#41;](../../native-client-ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Mots clés de chaîne d'initialisation du fournisseur  
 Les mots clés de chaîne d'initialisation du fournisseur suivants prennent en charge les SPN dans les applications OLE DB. Dans le tableau suivant, les valeurs dans la colonne de mot clé sont utilisées pour la chaîne du fournisseur de IDBInitialize::Initialize. Les valeurs dans la colonne description sont utilisées dans les chaînes d’initialisation lors de la connexion à l’aide d’ADO ou à IDataInitialize::GetDataSource.  
  
|Mot clé|Description|Valeur|  
|-------------|-----------------|-----------|  
|ServerSPN|SPN du serveur|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
|FailoverPartnerSPN|SPN du partenaire de basculement|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
  
## <a name="data-source-initialization-properties"></a>Propriétés d'initialisation de la source de données  
 Les propriétés suivantes du jeu de propriétés `DBPROPSET_SQLSERVERDBINIT` permettent aux applications de spécifier des SPN.  
  
|Nom   |Type|Utilisation|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, lecture/écriture|Spécifie le nom principal de service du serveur. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, lecture/écriture|Spécifie le nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
  
## <a name="data-source-properties"></a>Propriétés de Source de données  
 Les propriétés suivantes du jeu de propriétés `DBPROPSET_SQLSERVERDATASOURCEINFO` permettent aux applications d'identifier la méthode d'authentification.  
  
|Nom   |Type|Utilisation|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, lecture seule|Retourne la méthode d'authentification utilisée pour la connexion. La valeur retournée à l'application est la valeur que Windows renvoie à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Les valeurs possibles sont les suivantes :<br /><br /> -« NTLM », qui est retourné lorsqu’une connexion est ouverte à l’aide de l’authentification NTLM.<br />-« Kerberos », qui est retourné lorsqu’une connexion est ouverte à l’aide de l’authentification Kerberos.<br /><br /> Si une connexion a été ouverte et si la méthode d'authentification ne peut pas être déterminée, VT_EMPTY est retourné.<br /><br /> Cette propriété ne peut être lue que lorsqu'une source de données a été initialisée. Si vous tentez de lire la propriété avant d’une source de données a été initialisée, IDBProperties::GetProperies retourne DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, selon le cas, et DBPROPSTATUS_NOTSUPPORTED est défini dans DBPROPSET_PROPERTIESINERROR pour cette propriété. Ce comportement est conforme à la spécification principale OLE DB.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, lecture seule|Retourne VARIANT_TRUE si les serveurs de la connexion ont été authentifiés mutuellement ; sinon, retourne VARIANT_FALSE.<br /><br /> Cette propriété ne peut être lue que lorsqu'une source de données a été initialisée. En l’absence d’une tentative de lecture de la propriété avant d’une source de données a été initialisée, IDBProperties::GetProperies retourne DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, selon le cas, et DBPROPSTATUS_NOTSUPPORTED est défini dans DBPROPSET_ PROPERTIESINERROR pour cette propriété. Ce comportement est conformément à la spécification principale OLE DB<br /><br /> Si cet attribut est interrogé pour une connexion n'ayant pas utilisé l'authentification Windows, VARIANT_FALSE est retourné.|  
  
## <a name="ole-db-api-support-for-spns"></a>Prise en charge des SPN par l'API OLE DB  
 Le tableau suivant décrit les fonctions membres OLE DB qui prennent en charge les SPN dans les connexions clientes :  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString* peut contenir les nouveaux mots clés `ServerSPN` et `FailoverPartnerSPN`.|  
|IDataInitialize::GetInitializationString|Si SSPROP_INIT_SERVERSPN et ssprop_init_failoverpartnerspn n’ont des valeurs non définies par défaut, ils seront inclus dans la chaîne d’initialisation via *ppwszInitString* en tant que valeurs de mot clé pour `ServerSPN` et `FailoverPartnerSPN`. Sinon, ces mots clés ne sont pas inclus dans la chaîne d'initialisation.|  
|IDBInitialize::Initialize|Si l'invite est activée en définissant DBPROP_INIT_PROMPT dans les propriétés d'initialisation de la source de données, la boîte de dialogue de connexion OLE DB s'affiche. Celle-ci vous permet d'entrer des SPN à la fois pour le serveur principal et pour le partenaire de basculement.<br /><br /> La chaîne du fournisseur dans DPPROP_INIT_PROVIDERSTRING, si la valeur, reconnaît les nouveaux mots clés `ServerSPN` et `FailoverPartnerSPN` et utilise leurs valeurs, le cas échéant, pour initialiser SSPROP_INIT_SERVER_SPN et SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> IDBProperties::SetProperties peut être appelée pour définir les propriétés SSPROP_INIT_SERVER_SPN et SSPROP_INIT_FAILOVER_PARTNER_SPN avant l’appel IDBInitialize::Initialize. Il s'agit d'une alternative à l'utilisation d'une chaîne de fournisseur.<br /><br /> Si une propriété est définie à plusieurs emplacements, une valeur définie par programme est prioritaire sur un jeu de valeurs dans la chaîne du fournisseur. Une valeur définie dans une chaîne d'initialisation est prioritaire sur une valeur définie dans la boîte de dialogue de connexion.<br /><br /> Si le même mot clé apparaît plus d'une fois dans la chaîne du fournisseur, la valeur de la première occurrence est prioritaire.|  
|IDBProperties::GetProperties|IDBProperties::GetProperties peut être appelée pour obtenir les valeurs des nouvelle propriétés source de données d’initialisation SSPROP_INIT_SERVERSPN et ssprop_init_failoverpartnerspn n’et des nouvelles propriétés de source de données SSPROP_AUTHENTICATIONMETHOD et SSPROP_ MUTUALLYAUTHENTICATED.|  
|IDBProperties::GetPropertyInfo|IdbProperties::GetPropertyInfo inclut les nouvelles propriétés source de données d’initialisation SSPROP_INIT_SERVERSPN et ssprop_init_failoverpartnerspn n’ou les nouvelles propriétés de source de données SSPROP_AUTHENTICATION_METHOD et SSPROP_MUTUALLYAUTHENTICATED.|  
|IDBProperties::SetProperties|IDBProperties::SetProperties peut être appelée pour définir des propriétés d’initialisation SSPROP_INITSERVERSPN et SSPROP_INIT_FAILOVERPARTNERSPN les valeurs de la nouvelle source de données.<br /><br /> Ces propriétés peuvent être définies à tout moment, mais si la source de données est déjà ouverte, l'erreur suivante est retournée : DB_E_ERRORSOCCURRED, « Une opération OLE DB en plusieurs étapes a généré des erreurs. Vérifiez chaque valeur d'état OLE DB disponible. Aucun travail n'a été effectué. »|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)  
  
  