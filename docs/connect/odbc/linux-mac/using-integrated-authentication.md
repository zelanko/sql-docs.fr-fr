---
title: Utilisation de l’authentification intégrée | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 27bfc5a5654042be3dde68a2a03c1dd4e6a6d4a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801758"
---
# <a name="using-integrated-authentication"></a>Utilisation de l’authentification intégrée
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS prend en charge les connexions qui utilisent l’authentification intégrée Kerberos. Il prend en charge le centre de distribution de clés (KDC) MIT Kerberos et fonctionne avec l’interface GSSAPI (Generic Security Services Application Program Interface) et les bibliothèques Kerberos v5.
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversion-mdmd-from-an-odbc-application"></a>Utilisation de l’authentification intégrée pour se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir d’une application ODBC  

Vous pouvez activer l’authentification intégrée Kerberos en spécifiant **Trusted_Connection=yes** dans la chaîne de connexion **SQLDriverConnect** ou **SQLConnect**. Par exemple :  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
Quand vous vous connectez avec un nom de source de données, vous pouvez également ajouter **Trusted_Connection=yes** à l’entrée de ce dernier dans `odbc.ini`.
  
Vous pouvez également utiliser l’option `-E` de `sqlcmd` et l’option `-T` de `bcp` pour spécifier l’authentification intégrée ; pour plus d’informations, consultez [Connexion avec **sqlcmd**](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md) et [Connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md).

Vérifiez que le principal de client qui va se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est déjà authentifié auprès du centre KDC Kerberos.
  
**ServerSPN** et **FailoverPartnerSPN** ne sont pas pris en charge.  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>Déploiement d’une application de pilote ODBC Linux ou macOS conçue pour s’exécuter en tant que service

Un administrateur système peut déployer une application pour qu’elle s’exécute en tant que service qui utilise l’authentification Kerberos pour se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
Vous devez d’abord configurer Kerberos sur le client, puis vous assurer que l’application peut utiliser les informations d’identification Kerberos du principal par défaut.

Vérifiez que vous utilisez `kinit` ou PAM (Pluggable Authentication Module) pour obtenir et mettre en cache le ticket TGT pour le principal utilisé par la connexion avec l’une des méthodes suivantes :  
  
-   Exécutez `kinit`, en passant un nom et un mot de passe de principal.  
  
-   Exécutez `kinit`, en passant un nom de principal et l’emplacement du fichier keytab contenant la clé du principal créée par `ktutil`.  
  
-   Vérifiez que la connexion au système a été effectuée à l’aide du module PAM Kerberos.

Quand une application s’exécute en tant que service, comme les informations d’identification Kerberos expirent de par leur conception, vous devez renouveler les informations d’identification pour garantir une disponibilité continue du service. Le pilote ODBC ne renouvelle pas les informations d’identification lui-même ; vérifiez qu’un script ou une tâche `cron` s’exécute régulièrement pour renouveler les informations d’identification avant leur expiration. Pour éviter d’exiger le mot de passe à chaque renouvellement, vous pouvez utiliser un fichier keytab.  
  
L’article[Kerberos Configuration and Use](https://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) fournit des détails sur l’implémentation de Kerberos pour les services sur Linux.
  
## <a name="tracking-access-to-a-database"></a>Suivi de l’accès à une base de données

Un administrateur de base de données peut créer une piste d’audit de l’accès à une base de données lors de l’utilisation des comptes système pour accéder à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide de l’authentification intégrée.  
  
La connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le compte système et il n’existe aucune fonctionnalité sur Linux pour emprunter l’identité du contexte de sécurité. Ainsi, des opérations supplémentaires sont nécessaires pour déterminer l’utilisateur.
  
Pour auditer les activités dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour le compte d’utilisateurs autres que le compte système, l’application doit utiliser [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE AS**.  
  
Pour améliorer ses performances, une application peut utiliser le regroupement de connexions avec l’authentification intégrée et l’audit. Toutefois, le fait de combiner le regroupement de connexions, l’authentification intégrée et l’audit crée un risque de sécurité, car le Gestionnaire de pilotes unixODBC permet à différents utilisateurs de réutiliser les connexions regroupées. Pour plus d’informations, consultez [ODBC Connection Pooling](http://www.unixodbc.org/doc/conn_pool.html).  

Avant d’être réutilisée, une application doit réinitialiser les connexions regroupées en exécutant `sp_reset_connection`.  

## <a name="using-active-directory-to-manage-user-identities"></a>Utilisation d’Active Directory pour gérer les identités des utilisateurs

Un administrateur système n’a pas besoin de gérer des ensembles distincts d’informations d’identification de connexion pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il est possible de configurer Active Directory comme Centre de distribution de clés pour l’authentification intégrée. Pour plus d’informations, consultez [Microsoft Kerberos](/windows/desktop/SecAuthN/microsoft-kerberos).

## <a name="using-linked-server-and-distributed-queries"></a>Utilisation de serveur lié et de requêtes distribuées

Les développeurs peuvent déployer une application qui utilise un serveur lié ou des requêtes distribuées sans qu’un administrateur de base de données ait à tenir à jour des ensembles distincts d’informations d’identification SQL. Dans ce cas, un développeur doit configurer une application pour qu’elle utilise l’authentification intégrée :  
  
-   L’utilisateur se connecte à un ordinateur client et s’authentifie auprès du serveur d’applications.  
  
-   Le serveur d’applications s’authentifie en tant qu’autre base de données et se connecte à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s’authentifie en tant qu’utilisateur de base de données pour une autre base de données ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
Une fois l’authentification intégrée configurée, les informations d’identification sont transmises au serveur lié.  
  
## <a name="integrated-authentication-and-sqlcmd"></a>Authentification intégrée et sqlcmd
Pour accéder à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide de l’authentification intégrée, utilisez l’option `-E` de `sqlcmd`. Assurez-vous que le compte qui exécute `sqlcmd` est associé au principal de client Kerberos par défaut.

## <a name="integrated-authentication-and-bcp"></a>Authentification intégrée et bcp
Pour accéder à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide de l’authentification intégrée, utilisez l’option `-T` de `bcp`. Assurez-vous que le compte qui exécute `bcp` est associé au principal de client Kerberos par défaut. 
  
L’utilisation de `-T` avec l’option `-U` ou `-P` constitue une erreur.
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversion-mdmd"></a>Syntaxe prise en charge pour un SPN inscrit par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]

La syntaxe que les noms de principal du service utilisent dans la chaîne de connexion ou les attributs de connexion est la suivante :  

|Syntaxe|Description|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|Nom principal de service par défaut, généré par le fournisseur, lorsque le protocole TCP est utilisé. *port* est un numéro de port TCP. *fqdn* est un nom de domaine complet.|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Authentification d’un ordinateur Linux ou macOS avec Active Directory

Pour configurer Kerberos, entrez des données dans le fichier `krb5.conf`. `krb5.conf` se trouve dans `/etc/`, mais vous pouvez faire référence à un autre fichier, par exemple à l’aide de la syntaxe `export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`. Voici un exemple de fichier `krb5.conf` :  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
```  
  
Si votre ordinateur Linux ou macOS est configuré pour utiliser le protocole DHCP (Dynamic Host Configuration Protocol) avec un serveur DHCP Windows fournissant les serveurs DNS à utiliser, vous pouvez faire appel à **dns_lookup_kdc=true**. À présent, vous pouvez utiliser Kerberos pour vous connecter à votre domaine en exécutant la commande `kinit alias@YYYY.CORP.CONTOSO.COM`. Les paramètres passés à `kinit` sont sensibles à la casse, et vous devez ajouter `alias@YYYY.CORP.CONTOSO.COM` à l’ordinateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuré pour être dans le domaine pour la connexion. À présent, vous pouvez utiliser des connexions approuvées (**Trusted_Connection=YES** dans une chaîne de connexion, **bcp -T** ou **sqlcmd -E**).  
  
L’heure sur l’ordinateur Linux ou macOS et l’heure sur le centre de distribution de clés Kerberos (KDC) doivent être proches. Vérifiez que l’heure système est correctement définie, par exemple en utilisant le protocole NTP (Network Time Protocol).  

Si l’authentification Kerberos échoue, le pilote ODBC sur Linux ou macOS n’utilise pas l’authentification NTLM.  

Pour plus d’informations sur l’authentification des ordinateurs Linux ou macOS avec Active Directory, consultez [Authentifier les clients Linux avec Active Directory](https://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048) et [Bonnes pratiques pour intégrer OS X à Active Directory](https://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Pour plus d’informations sur la configuration de Kerberos, consultez la [documentation MIT Kerberos](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html).

## <a name="see-also"></a>Voir aussi  
[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)

[Utilisation d’Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md)
