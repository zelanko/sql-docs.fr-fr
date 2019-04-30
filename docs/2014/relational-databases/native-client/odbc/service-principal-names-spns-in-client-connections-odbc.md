---
title: Noms de principal du service (SPN) dans les connexions clientes (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 1d60cb30-4c46-49b2-89ab-701e77a330a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f45e6124dbbad79802e290f935ccc6f3f45cee0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63144401"
---
# <a name="service-principal-names-spns-in-client-connections-odbc"></a>Noms de principaux du service (SPN) dans les connexions clientes (ODBC)
  Cette rubrique décrit les attributs et fonctions ODBC qui prennent en charge les noms de principaux du service (SPN) dans les applications clientes. Pour plus d’informations sur les SPN dans les applications clientes, consultez [nom Principal de Service &#40;SPN&#41; prise en charge dans les connexions clientes](../features/service-principal-name-spn-support-in-client-connections.md) et [obtenir une authentification mutuelle Kerberos](../../native-client-odbc-how-to/get-mutual-kerberos-authentication.md).  
  
## <a name="connection-string-keywords"></a>Mots clés de chaîne de connexion  
 Les mots clés de chaîne de connexion suivants permettent aux applications clientes de spécifier un nom principal de service.  
  
|Mot clé|Value|  
|-------------|-----------|  
|`ServerSPN`|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le pilote.|  
|`FailoverPartnerSPN`|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le pilote.|  
  
## <a name="connection-attributes"></a>Attributs de connexion  
 Les attributs de connexion suivants permettent aux applications clientes de spécifier un nom principal de service et d'interroger la méthode d'authentification.  
  
|Nom|Type|Utilisation|  
|----------|----------|-----------|  
|SQL_COPT_SS_SERVER_SPN<br /><br /> SQL_COPT_SS_FAILOVER_PARTNER_SPN|SQLTCHAR, lecture/écriture|Spécifie le nom principal de service du serveur. La valeur par défaut est une chaîne vide, ce qui force [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à utiliser le nom principal de service par défaut, généré par le pilote.<br /><br /> Cet attribut peut être interrogé uniquement après avoir été défini par programme ou après l'ouverture d'une connexion. Si une tentative d'interrogation de cet attribut sur une connexion qui n'est pas ouverte est effectuée et que l'attribut n'a pas été défini par programme, SQL_ERROR est retournée et un enregistrement de diagnostic est enregistré avec SQLState 08003 et le message « Connexion non ouverte ».<br /><br /> Si une tentative de définition de cet attribut est effectuée lorsqu'une connexion est ouverte, SQL_ERROR est retournée et un enregistrement de diagnostic est consigné avec SQLState HY011 et le message « Opération actuellement non valide ».|  
|SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD|SQLTCHAR, lecture seule|Retourne la méthode d'authentification utilisée pour la connexion. La valeur retournée à l'application est la valeur que Windows renvoie à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Les valeurs possibles sont :<br /><br /> -« NTLM », qui est retourné lorsqu’une connexion est ouverte à l’aide de l’authentification NTLM.<br />-« Kerberos », qui est retourné lorsqu’une connexion est ouverte à l’aide de l’authentification Kerberos.<br /><br /> Cet attribut peut être lu uniquement pour une connexion ouverte ayant utilisé l'authentification Windows. Si une tentative de lecture de cet attribut est effectuée avant qu'une connexion ait été ouverte, SQL_ERROR est retournée et une erreur est enregistrée avec SQLState 08003 et le message « Connexion non ouverte ».<br /><br /> Si cet attribut est interrogé sur une connexion qui n'a pas utilisé l'authentification Windows, SQL_ERROR est retournée, une erreur est enregistrée avec SQLState HY092 et le message « Identificateur d'option/attribut non valide (SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD n'est disponible que pour les connexions approuvées) ».<br /><br /> Si la méthode d'authentification ne peut pas être déterminée, SQL_ERROR est retournée et une erreur est enregistrée avec SQLState HY000 et le message « Erreur générale »|  
|SQL_COPT_SS_MUTUALLY_AUTHENTICATED|SQLSMALLINT, lecture seule|Retourne SQL_TRUE si le serveur dans la connexion a été authentifié mutuellement ; sinon, retourne SQL_FALSE.<br /><br /> Cet attribut peut être lu uniquement pour une connexion ouverte. Si une tentative de lecture de cet attribut est effectuée avant qu'une connexion ait été ouverte, SQL_ERROR est retournée et une erreur est enregistrée avec SQLState 08003 et le message « Connexion non ouverte ».<br /><br /> Si cet attribut est interrogé pour une connexion n'ayant pas utilisé l'authentification Windows, SQL_FALSE est retournée.|  
  
## <a name="odbc-function-support-for-specifying-spns"></a>Prise en charge de fonction ODBC pour la spécification des SPN  
 Les fonctions ODBC suivantes prennent en charge les applications clientes et les noms principaux de service :  
  
-   [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
-   [SQLConnect](../../native-client-odbc-api/sqlconnect.md)  
  
-   [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)  
  
-   [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)  
  
-   [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
