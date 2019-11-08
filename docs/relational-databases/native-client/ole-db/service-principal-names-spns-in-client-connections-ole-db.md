---
title: Noms de principaux du service (SPN) dans les connexions clientes (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e212010e-a5b6-4ad1-a3c0-575327d3ffd3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 83356cd14155daba742f78fe37ba7c903226e5cf
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73759516"
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>Noms de principaux du service (SPN) dans les connexions clientes (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit les propriétés et fonctions membres OLE DB qui prennent en charge les noms de principaux du service (SPN) dans les applications clientes. Pour plus d’informations sur les SPN dans les applications clientes, voir [Prise en charge des noms de principal du service &#40;SPN&#41; dans les connexions clientes](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md). Pour obtenir un exemple, consultez [OLE DB &#40;&#41;d’authentification Kerberos intégrée](../../../relational-databases/native-client-ole-db-how-to/integrated-kerberos-authentication-ole-db.md).  
  
## <a name="provider-initialization-string-keywords"></a>Mots clés de chaîne d'initialisation du fournisseur  
 Les mots clés de chaîne d'initialisation du fournisseur suivants prennent en charge les SPN dans les applications OLE DB. Dans le tableau suivant, les valeurs de la colonne de mot clé sont utilisées dans la chaîne du fournisseur de IDBInitialize::Initialize. Les valeurs de la colonne de description sont utilisées dans les chaînes d’initialisation lors de la connexion avec ADO ou IDataInitialize::GetDataSource.  
  
|Mot clé|Description|Value|  
|-------------|-----------------|-----------|  
|ServerSPN|SPN du serveur|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
|FailoverPartnerSPN|SPN du partenaire de basculement|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
  
## <a name="data-source-initialization-properties"></a>Propriétés d'initialisation de la source de données  
 Les propriétés suivantes du jeu de propriétés **DBPROPSET_SQLSERVERDBINIT** permettent aux applications de spécifier des noms de principal du service.  
  
|Créer une vue d’abonnement|Type|Utilisation|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR, lecture/écriture|Spécifie le nom principal de service du serveur. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR, lecture/écriture|Spécifie le nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le fournisseur.|  
  
## <a name="data-source-properties"></a>Propriétés de la source de données  
 Les propriétés suivantes dans le jeu de propriétés **DBPROPSET_SQLSERVERDATASOURCEINFO** permettent aux applications de découvrir la méthode d’authentification.  
  
|Créer une vue d’abonnement|Type|Utilisation|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR, lecture seule|Retourne la méthode d'authentification utilisée pour la connexion. La valeur retournée à l'application est la valeur que Windows renvoie à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Les valeurs possibles sont les suivantes : <br />« NTLM », lorsqu'une connexion est ouverte à l'aide de l'authentification NTLM.<br />« Kerberos », lorsqu'une connexion est ouverte à l'aide de l'authentification Kerberos.<br /><br /> Si une connexion a été ouverte et si la méthode d'authentification ne peut pas être déterminée, VT_EMPTY est retourné.<br /><br /> Cette propriété ne peut être lue que lorsqu'une source de données a été initialisée. Si vous essayez de lire la propriété avant qu’une source de données ait été initialisée, IDBProperties::GetProperies retourne DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, selon le cas, et DBPROPSTATUS_NOTSUPPORTED est défini dans DBPROPSET_PROPERTIESINERROR pour cette propriété. Ce comportement est conforme à la spécification principale OLE DB.|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL, lecture seule|Retourne VARIANT_TRUE si les serveurs de la connexion ont été authentifiés mutuellement ; sinon, retourne VARIANT_FALSE.<br /><br /> Cette propriété ne peut être lue que lorsqu'une source de données a été initialisée. Si une tentative de lecture de la propriété est faite avant qu’une source de données ait été initialisée, IDBProperties::GetProperies retourne DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, selon le cas, et DBPROPSTATUS_NOTSUPPORTED est défini dans DBPROPSET_PROPERTIESINERROR pour cette propriété. Ce comportement est conforme à la spécification principale d’OLE DB.<br /><br /> Si cet attribut est interrogé pour une connexion n'ayant pas utilisé l'authentification Windows, VARIANT_FALSE est retourné.|  
  
## <a name="ole-db-api-support-for-spns"></a>Prise en charge des SPN par l'API OLE DB  
 Le tableau suivant décrit les fonctions membres OLE DB qui prennent en charge les SPN dans les connexions clientes :  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString* peut contenir les nouveaux mots clés **ServerSPN** et **FailoverPartnerSPN ne**.|  
|IDataInitialize::GetInitializationString|Si SSPROP_INIT_SERVERSPN et SSPROP_INIT_FAILOVERPARTNERSPN ont des valeurs autres que la valeur par défaut, ils sont inclus dans la chaîne d’initialisation via *ppwszInitString* comme valeurs de mot clé pour **ServerSPN** et **FailoverPartnerSPN**. Sinon, ces mots clés ne sont pas inclus dans la chaîne d'initialisation.|  
|IDBInitialize::Initialize|Si l'invite est activée en définissant DBPROP_INIT_PROMPT dans les propriétés d'initialisation de la source de données, la boîte de dialogue de connexion OLE DB s'affiche. Celle-ci vous permet d'entrer des SPN à la fois pour le serveur principal et pour le partenaire de basculement.<br /><br /> Si elle est définie, la chaîne du fournisseur dans DPPROP_INIT_PROVIDERSTRING reconnaît les nouveaux mots clés **ServerSPN** et **FailoverPartnerSPN**, et utilise leurs valeurs, si elles sont présentes, pour initialiser SSPROP_INIT_SERVER_SPN et SSPROP_INIT_FAILOVER_PARTNER_SPN.<br /><br /> IDBProperties :: SetProperties peut être appelé pour définir les propriétés SSPROP_INIT_SERVER_SPN et SSPROP_INIT_FAILOVER_PARTNER_SPN avant l’appel de IDBInitialize :: Initialize. Il s'agit d'une alternative à l'utilisation d'une chaîne de fournisseur.<br /><br /> Si une propriété est définie à plusieurs emplacements, une valeur définie par programme est prioritaire sur un jeu de valeurs dans la chaîne du fournisseur. Une valeur définie dans une chaîne d'initialisation est prioritaire sur une valeur définie dans la boîte de dialogue de connexion.<br /><br /> Si le même mot clé apparaît plus d'une fois dans la chaîne du fournisseur, la valeur de la première occurrence est prioritaire.|  
|IDBProperties::GetProperties|IDBProperties::GetProperties peut être appelé pour obtenir les valeurs des propriétés d’initialisation de la nouvelle source de données (SSPROP_INIT_SERVERSPN et SSPROP_INIT_FAILOVERPARTNERSPN) et des propriétés de la nouvelle source de données (SSPROP_AUTHENTICATIONMETHOD et SSPROP_MUTUALLYAUTHENTICATED).|  
|IDBProperties::GetPropertyInfo|IdbProperties::GetPropertyInfo inclut les propriétés d’initialisation de la nouvelle source de données (SSPROP_INIT_SERVERSPN et SSPROP_INIT_FAILOVERPARTNERSPN) ou les propriétés de la nouvelle source de données (SSPROP_AUTHENTICATION_METHOD et SSPROP_MUTUALLYAUTHENTICATED).|  
|IDBProperties::SetProperties|IDBProperties::SetProperties peut être appelé pour définir les valeurs des propriétés d’initialisation de la nouvelle source de données (SSPROP_INITSERVERSPN et SSPROP_INIT_FAILOVERPARTNERSPN).<br /><br /> Ces propriétés peuvent être définies à tout moment, mais si la source de données est déjà ouverte, l'erreur suivante est retournée : DB_E_ERRORSOCCURRED, « Une opération OLE DB en plusieurs étapes a généré des erreurs. Vérifiez chaque valeur d'état OLE DB disponible. Aucun travail n'a été effectué. »|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
