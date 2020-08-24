---
title: Inscrire un nom de principal du service pour les connexions Kerberos
description: Découvrez comment inscrire un nom de principal du service auprès d’Active Directory. Cette inscription est requise pour l’utilisation de l’authentification Kerberos avec SQL Server.
ms.prod: sql
ms.prod_service: high-availability
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SPNs
- network connections [SQL Server], SPNs
- registering SPNs
- Server Principal Names
- SPNs [SQL Server]
ms.assetid: e38d5ce4-e538-4ab9-be67-7046e0d9504e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 08/12/2020
ms.openlocfilehash: 242b87166035c8ffc0e01272b5910f85a66620e7
ms.sourcegitcommit: bf5acef60627f77883249bcec4c502b0205300a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88200680"
---
# <a name="register-a-service-principal-name-for-kerberos-connections"></a>Inscrire un nom de principal du service pour les connexions Kerberos

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 Pour utiliser l’authentification Kerberos avec SQL Server, les deux conditions suivantes doivent être remplies :  

- Les ordinateurs clients et serveurs doivent faire partie du même domaine Windows ou appartenir à des domaines approuvés.  

- Un nom de principal du service (SPN, Service Principal Name) doit être inscrit dans Active Directory, qui joue le rôle de centre de distribution de clés dans un domaine Windows. Une fois inscrit, le SPN est mappé au compte Windows qui a démarré le service de l'instance de SQL Server. Si l'inscription du SPN n'a pas été effectuée ou échoue, la couche de sécurité Windows ne peut pas déterminer le compte associé au SPN et l'authentification Kerberos n’est pas utilisée.

    > [!NOTE]  
    >  Si le serveur ne parvient pas à inscrire automatiquement le SPN, celui-ci doit être inscrit manuellement. Consultez [Inscription manuelle des SPN](#Manual).  

Vous pouvez vérifier qu'une connexion utilise Kerberos en interrogeant la vue de gestion dynamique sys.dm_exec_connections. Exécutez la requête suivante et vérifiez la valeur de la colonne auth_scheme, qui sera « KERBEROS » si Kerberos est activé.

```sql
SELECT auth_scheme FROM sys.dm_exec_connections WHERE session_id = @@spid ;
```

> [!TIP]
>  **[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager pour SQL Server** est un outil de diagnostic qui permet de dépanner les problèmes de connexion que rencontre Kerberos avec SQL Server. Pour plus d'informations, consultez [Gestionnaire de configuration de Microsoft Kerberos pour SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  

##  <a name="the-role-of-the-spn-in-authentication"></a><a name="Role"></a> Rôle du SPN dans l'authentification  

Lorsqu'une application ouvre une connexion et utilise l'authentification Windows, SQL Server Native Client transmet le nom de l'ordinateur SQL Server , le nom de l'instance et, éventuellement, un SPN. Si la connexion transmet un SPN, il est utilisé sans aucune modification.  

Si la connexion ne transmet pas de SPN, un SPN par défaut est construit à partir du protocole utilisé, du nom de serveur et du nom de l'instance.  

Dans les deux scénarios précédents, le SPN est envoyé au centre de distribution de clés pour obtenir un jeton de sécurité en vue d'authentifier la connexion. Si un jeton de sécurité ne peut pas être obtenu, l'authentification utilise le protocole NTLM.  

Le nom de principal du service (SPN) est le nom par lequel un client identifie de manière unique l'instance d'un service. Le service d'authentification Kerberos peut utiliser le nom principal d'un service pour authentifier un service. Pour se connecter à un service, le client localise une instance du service, compose le nom principal du service pour cette instance, se connecte au service et présente le nom principal de service pour que le service s'authentifie.  
  
> [!NOTE]  
>  Les informations fournies dans cette rubrique s'appliquent également aux configurations SQL Server qui utilisent le clustering.  
  
L'Authentification Windows est la méthode recommandée pour authentifier les utilisateurs sur SQL Server. Les clients qui utilisent l'Authentification Windows sont authentifiés à l'aide de NTLM ou Kerberos. Dans un environnement Active Directory, l'authentification Kerberos est toujours tentée en premier. L'authentification Kerberos n'est pas disponible pour les clients [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] utilisant des canaux nommés.  

##  <a name="permissions"></a><a name="Permissions"></a> Autorisations

Lorsque le service Database Engine démarre, il tente d'enregistrer le nom de principal du service (SPN). Supposons que le compte démarrant SQL Server ne dispose pas de l’autorisation d’inscrire un nom SPN dans Active Directory Domain Services. Dans ce cas, cet appel échoue et un message d’avertissement est enregistré dans le journal des événements de l’application, ainsi que dans le journal des erreurs SQL Server. Pour inscrire le SPN, le moteur de base de données doit s'exécuter sous un compte intégré, tel que Système local (non recommandé) ou SERVICE RÉSEAU, ou sous un compte qui a l'autorisation d'inscrire un SPN. Vous pouvez inscrire un SPN à l’aide d’un compte d’administrateur de domaine, mais cela n’est pas recommandé dans un environnement de production. Lorsque SQL Server s’exécute sur le système d’exploitation Windows 7 ou Windows Server 2008 R2, vous pouvez exécuter SQL Server à l’aide d’un compte virtuel ou d’un compte de service administré (MSA). Les comptes virtuels et les comptes de service administré peuvent inscrire un SPN. Si SQL Server ne s’exécute pas sous l’un de ces comptes, le SPN n’est pas inscrit lors du démarrage et l’administrateur de domaine doit l’inscrire manuellement.

> [!NOTE]  
>  Lorsque le domaine Windows est configuré pour s'exécuter à un niveau fonctionnel inférieur à celui de Windows Server 2008 R2, le compte de service administré n'a pas les autorisations nécessaires pour inscrire le SPN pour le service [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Si l'authentification Kerberos est requise, l'administrateur de domaine doit inscrire manuellement les SPN SQL Server le compte de service administré.

Des informations supplémentaires sont disponibles dans l’article [How to Implement Kerberos Constrained Delegation with SQL Server 2008 (Procédure d’implémentation de la délégation contrainte Kerberos à l’aide de SQL Server 2008)](https://technet.microsoft.com/library/ee191523.aspx).  

##  <a name="spn-formats"></a><a name="Formats"></a> Formats de SPN

À compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], le format des SPN est modifié afin de prendre en charge l'authentification Kerberos sur le protocole TCP/IP, les canaux nommés et la mémoire partagée. Les formats de SPN pris en charge pour les instances nommées et par défaut sont les suivants.  
  
**Instance nommée**  
  
-   **MSSQLSvc/\<FQDN>:[\<port> | \<instancename>]** , où :  
  
    -   **MSSQLSvc** est le service en cours d’inscription.  
  
    -   **\<FQDN>** est le nom de domaine complet du serveur.  
  
    -   **\<port>** est le numéro de port TCP.  
  
    -   **\<instancename>** représente le nom de l'instance SQL Server.  
  
**Instance par défaut**  
  
-   **MSSQLSvc/\<FQDN>:\<port>**  | **MSSQLSvc/\<FQDN>** , où :  
  
    -   **MSSQLSvc** est le service en cours d’inscription.  
  
    -   **\<FQDN>** est le nom de domaine complet du serveur.  
  
    -   **\<port>** est le numéro de port TCP.  
  
    > [!NOTE]
    > Le nouveau format SPN ne requiert pas de numéro de port. Cela signifie qu'un serveur à port multiple ou un protocole qui n'utilise pas de numéro de port peut utiliser l'authentification Kerberos.  
   
|Format de SPN|Description|  
|-|-|  
|MSSQLSvc/\<FQDN>:\<port>|Nom principal de service par défaut, généré par le fournisseur, lorsque le protocole TCP est utilisé. \<port> est un numéro de port TCP.|  
|MSSQLSvc/\<FQDN>|Nom principal de service par défaut, généré par le fournisseur, pour une instance par défaut lorsqu'un autre protocole que TCP est utilisé. \<FQDN> est un nom de domaine complet.|  
|MSSQLSvc/\<FQDN>:\<instancename>|Nom principal de service par défaut, généré par le fournisseur, pour une instance nommée lorsqu'un autre protocole que TCP est utilisé. \<instancename> est le nom d'une instance de SQL Server.|  

> [!NOTE]  
> Dans le cas d'une connexion TCP/IP, où le port TCP est inclus dans le SPN, SQL Server doit activer le protocole TCP afin de permettre à un utilisateur de se connecter à l'aide de l'authentification Kerberos. 

##  <a name="automatic-spn-registration"></a><a name="Auto"></a> Inscription automatique des SPN  

Lors du démarrage d’une instance [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], SQL Server tente d’inscrire le nom SPN du service SQL Server. Lors de l’arrêt de l’instance, SQL Server tente d’annuler l’inscription du nom SPN. Pour une connexion TCP/IP, le SPN est inscrit au format *MSSQLSvc/\<FQDN>* : *\<tcpport>* . Les instances nommées et l’instance par défaut sont inscrites en tant que *MSSQLSvc*. La valeur *\<tcpport>* est utilisée pour différencier les instances.  
  
Pour les autres connexions qui prennent en charge Kerberos, le SPN est inscrit au format *MSSQLSvc/\<FQDN>* / *\<instancename>* pour une instance nommée. Le format *MSSQLSvc/\<FQDN>* est utilisé pour l’inscription de l’instance par défaut.  

Une intervention manuelle peut être requise pour inscrire ou annuler l'inscription du SPN si le compte de service ne possède pas les autorisations requises pour ces actions.  

##  <a name="manual-spn-registration"></a><a name="Manual"></a> Inscription manuelle des SPN  

Pour inscrire le SPN manuellement, l'administrateur doit utiliser l'outil Setspn.exe fourni avec les Outils de support de Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] . Pour plus d’informations, consultez l’article de la Base de connaissances [Outils de support de Windows Server 2003 Service Pack 1](https://support.microsoft.com/kb/892777) .  

Setspn.exe est un outil de ligne de commande qui vous permet de lire, modifier et supprimer la propriété du répertoire des Noms de principaux du service (SPN). Cet outil vous permet également d'afficher les SPN actuels, de réinitialiser les SPN par défaut du compte et d'ajouter ou de supprimer des SPN supplémentaires.  

L’exemple suivant illustre la syntaxe utilisée pour inscrire manuellement un SPN pour une connexion TCP/IP à l’aide d’un compte d’utilisateur de domaine :  

```
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:1433 redmond\accountname  
```

> [!NOTE]
> S’il existe déjà un nom SPN, il doit être supprimé avant de pouvoir être réinscrit. Pour cela, utilisez la commande `setspn` avec le commutateur `-D` . Les exemples suivants illustrent comment inscrire manuellement un nouveau SPN basé sur une instance. Pour une instance par défaut utilisant un compte d’utilisateur de domaine, utilisez :  

```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com redmond\accountname  
```  
  
Pour une instance nommée, utilisez :  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:instancename redmond\accountname  
```  
  
##  <a name="client-connections"></a><a name="Client"></a> Connexions clientes  

Les SPN spécifiés par l'utilisateur sont pris en charge dans les pilotes clients. Toutefois, si aucun SPN n'est fourni, il est généré automatiquement en fonction du type de connexion cliente. Pour une connexion TCP, un nom SPN au format *MSSQLSvc*/*FQDN*:[*port*] est utilisé à la fois pour les instances nommées et par défaut.  
  
Pour les connexions par canaux nommés et mémoire partagée, un SPN au format *MSSQLSvc/\<FQDN>:\<instancename>* est utilisé pour une instance nommée et *MSSQLSvc/\<FQDN>* est utilisé pour l’instance par défaut.  
  
**Utilisation d'un compte de service comme SPN**  
  
Les comptes de service peuvent être utilisés comme SPN. Ils sont spécifiés par le biais de l'attribut de connexion pour l'authentification Kerberos et assument les formats suivants :  
  
- **nom_utilisateur\@domaine** ou **domaine\nom_utilisateur** pour un compte d’utilisateur de domaine  

- **ordinateur$\@domaine** ou **hôte\FQDN** pour un compte de domaine d’ordinateur tel que Système Local ou SERVICES RÉSEAU.  

Pour déterminer la méthode d'authentification d'une connexion, exécutez la requête suivante.  
  
```sql  
SELECT net_transport, auth_scheme   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
``` 

##  <a name="authentication-defaults"></a><a name="Defaults"></a> Paramètres par défaut de l'authentification  

Le tableau suivant décrit les paramètres d'authentification par défaut utilisés selon les scénarios d'inscription de SPN.  
  
|Scénario|Méthode d'authentification|  
|--------------|---------------------------|  
|Le SPN est mappé au compte de domaine, au compte virtuel, au compte de service administré ou au compte intégré approprié. Par exemple, Système local ou SERVICE RÉSEAU.|Les connexions locales utilisent NTLM, les connexions distantes utilisent Kerberos.|  
|Le SPN est le compte de domaine, le compte virtuel, le compte de service administré ou le compte intégré approprié.|Les connexions locales utilisent NTLM, les connexions distantes utilisent Kerberos.|  
|Le SPN est mappé à un compte de domaine, un compte virtuel, un compte de service administré ou un compte intégré erroné.|L'authentification échoue.|  
|La recherche du SPN échoue ou ne mappe pas à un compte de domaine, un compte virtuel, un compte de service administré ou un compte intégré correct, ou n'est pas un compte de domaine, un compte virtuel, un compte de service administré ou un compte intégré correct.|Les connexions locales et distantes utilisent NTLM.|  

> [!NOTE]
> « Correct » signifie que le compte mappé par le SPN inscrit est le compte sous lequel s’exécute le service SQL Server.  

##  <a name="comments"></a><a name="Comments"></a> Commentaires  

La connexion administrateur dédiée utilise un SPN basé sur un nom d'instance. L'authentification Kerberos peut être utilisée avec une connexion DAC si l'inscription de ce SPN réussit. En guise d'alternative, un utilisateur peut spécifier le nom du compte comme SPN.

Si l’inscription du nom SPN échoue au démarrage, cet échec est consigné dans le journal des erreurs de SQL Server et le démarrage se poursuit.  

Si l'annulation de l'inscription du SPN échoue pendant l'arrêt, cet échec est consigné dans le journal des erreurs de SQL Server et l'arrêt se poursuit.  

## <a name="see-also"></a>Voir aussi  
- [Prise en charge des noms de principal du service &#40;SPN&#41; dans les connexions clientes](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)
- [Noms de principaux du service &#40;noms SPN&#41; dans les connexions clientes &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)
- [Noms de principaux du service &#40;noms SPN&#41; dans les connexions clientes &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)
- [Fonctionnalités de SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)
- [Gérer les problèmes d’authentification Kerberos dans un environnement Reporting Services](https://technet.microsoft.com/library/ff679930.aspx)
