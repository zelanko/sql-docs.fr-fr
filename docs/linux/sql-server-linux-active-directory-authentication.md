---
title: 'Tutoriel : Utiliser l’authentification AD pour SQL Server sur Linux'
titleSuffix: SQL Server
description: Ce didacticiel fournit les étapes de configuration pour l’authentification Active Directory pour SQL Server sur Linux.
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 5e9d7ee2c086f188041fbf6c42448d21953b008d
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822787"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Tutoriel : Utiliser l’authentification Active Directory avec SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel explique comment configurer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux pour prendre en charge l’authentification Active Directory (AD), également appelée authentification intégrée. Pour une vue d’ensemble, consultez [l’authentification Active Directory pour SQL Server sur Linux](sql-server-linux-active-directory-auth-overview.md).

Ce didacticiel se compose des tâches suivantes :

> [!div class="checklist"]
> * Joindre un hôte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à un domaine Active Directory.
> * Créer un utilisateur Active Directory pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et définir le nom principal de service
> * Configurer le service keytab de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
> * Sécuriser le fichier keytab
> * Configurer SQL Server pour utiliser le fichier keytab pour l’authentification Kerberos
> * Créer des connexions basées sur Active Directory dans Transact-SQL
> * Se connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de l’authentification Active Directory

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’authentification Active Directory, vous devez :

* Configurer un contrôleur de domaine Active Directory (Windows) sur votre réseau  
* Installer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Joindre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hôte au domaine AD

Vous devez joindre votre hôte de SQL Server Linux avec un contrôleur de domaine Active Directory. Pour plus d’informations sur la façon de joindre un domaine active directory, consultez [jointure SQL Server sur un hôte Linux à un domaine Active Directory](sql-server-linux-active-directory-join-domain.md).

## <a id="createuser"></a> Créer utilisateur AD (ou MSA) pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et définir des SPN

> [!NOTE]
> Les étapes suivantes utilisent votre [nom de domaine complet](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Si vous êtes sur **Azure**, vous devez **[créez-le](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** avant de continuer.

1. Sur votre contrôleur de domaine, exécutez le [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) commande PowerShell pour créer un nouvel utilisateur Active Directory avec un mot de passe n’expire jamais. L’exemple suivant le nom du compte `mssql`, mais le nom du compte peut être comme vous le souhaitez. Vous êtes invité à entrer un nouveau mot de passe pour le compte.

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Il est recommandé d’avoir un compte AD dédié pour SQL Server, afin que les informations d’identification de SQL Server ne sont pas partagées avec d’autres services utilisant le même compte. Toutefois, vous pouvez éventuellement réutiliser un compte AD existant si vous connaissez le mot de passe (qui est requis pour générer un fichier keytab à l’étape suivante).

2. Définir le ServicePrincipalName (SPN) pour ce compte à l’aide de la **setspn.exe** outil. Le SPN doit être mis en forme exactement comme indiqué dans l’exemple suivant. Vous pouvez trouver le nom de domaine complet de le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ordinateur hôte en exécutant `hostname --all-fqdns` sur la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hôte. Le port TCP doit être 1433, sauf si vous avez configuré [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à utiliser un autre numéro de port.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Si vous recevez une erreur, `Insufficient access rights`, contactez votre administrateur de domaine que vous disposez des autorisations suffisantes pour définir un SPN sur ce compte.
   >
   > Si vous modifiez le port TCP à l’avenir, vous devez exécuter le **setspn** commande à nouveau avec le nouveau numéro de port. Vous devez également ajouter le nouveau SPN pour le fichier keytab service de SQL Server en suivant les étapes décrites dans la section suivante.

Pour plus d’informations, consultez [Inscrire un nom de principal du service pour les connexions Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Configurer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab de service

Il existe deux façons de configurer des fichiers keytab de service SQL Server. La première option consiste à utiliser un compte d’ordinateur (UPN), alors que la deuxième option utilise un compte de Service administré (MSA) dans la configuration de fichier keytab. Les deux mécanismes sont tout aussi fonctionnels, et vous pouvez choisir la méthode qui convient le mieux à votre environnement.

Dans les deux cas, le SPN créé à l’étape précédente est requis, et le SPN doit être inscrit dans le fichier keytab.

Pour configurer le fichier keytab du service SQL Server :

1. Configurer le [entrées de fichier keytab SPN](#spn) dans la section suivante.

1. Puis soit [ajouter UPN](#upn) (option 1) ou [MSA](#msa) entrées (option 2) dans le fichier keytab en suivant les étapes décrites dans leurs sections respectives.

> [!IMPORTANT]
> Si le mot de passe pour l’UPN/MSA est modifié ou le mot de passe pour le compte que les SPN sont affectés à est modifié, vous devez mettre à jour le fichier keytab avec le nouveau mot de passe et le numéro de Version de clé (KVNO). Certains services peuvent également faire pivoter les mots de passe automatiquement. Passez en revue les stratégies de rotation de mot de passe pour les comptes en question et de les aligner avec les activités de maintenance planifiée afin d’éviter les temps d’arrêt imprévus.

### <a id="spn"></a> Entrées de fichier keytab SPN

1. Vérifiez le numéro de Version de clé (KVNO) pour le compte AD créé à l’étape précédente. Il se situe généralement 2, mais il peut être un autre entier si vous avez modifié le mot de passe plusieurs fois. Sur l’ordinateur hôte SQL Server, exécutez les commandes suivantes :

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

   > [!NOTE]
   > SPN peuvent prendre plusieurs minutes pour se propager via votre domaine, en particulier si le domaine est grand. Si vous recevez l’erreur, `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM`, veuillez patienter quelques minutes et essayez à nouveau.  

1. Démarrer **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Ajoutez les entrées de fichier keytab pour chaque nom de principal de service utilisant les commandes suivantes :

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. Écrire le fichier keytab dans un fichier et quittez ktutil :

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > Le **ktutil** outil ne vérifie pas le mot de passe, veillez donc à vous entrez correctement lorsque vous y êtes invité.

### <a id="upn"></a> Option 1 : À l’aide du nom UPN pour configurer le fichier keytab

Ajouter le compte d’ordinateur à votre fichier keytab avec **ktutil**. Le compte d’ordinateur (également appelé un UPN) est présent dans **/etc/krb5.keytab** sous la forme `<hostname>$@<realm.com>` (par exemple, `sqlhost$@CONTOSO.COM`). Copiez ces entrées de **/etc/krb5.keytab** à **mssql.keytab**.

1. Démarrer **ktuil** avec la commande suivante :

   ```bash
   sudo ktutil
   ```

1. Utilisez le **rkt** commande à lire toutes les entrées de **/etc/krb5.keytab**.

   ```bash
   rkt /etc/krb5.keytab
   ```

1. Ensuite, répertoriez les entrées.

   ```bash
   list
   ```

1. Supprimez toutes les entrées par leur numéro d’emplacement qui ne sont pas l’UPN. Procéder à la fois en répétant la commande suivante :

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > Quand une entrée est supprimée, comme l’emplacement 1, toutes les valeurs déroulant par une pour prendre sa place. Cela signifie que l’entrée dans l’emplacement 2 se déplace vers l’emplacement 1 lors de l’entrée de l’emplacement de 1 est supprimée.

1. Répertorier les entrées à nouveau jusqu'à ce que seules les entrées UPN sont conservées.

   ```bash
   list
   ```

1. Lorsque seules les entrées UPN restent, ajouter ces valeurs à **mssql.keytab**:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. Quittez **ktutil**.

   ```bash
   quit
   ```

### <a id="msa"></a> Option 2 :  À l’aide de compte de service administré pour configurer le fichier keytab

Pour l’option de compte de service administré, vous devez créer le fichier keytab Kerberos de SQL Server. Il doit contenir tous les [SPN inscrits dans la première étape](#spn) et les informations d’identification pour le compte de service administré avec lequel les SPN sont enregistrés. 

1. Une fois le fichier keytab SPN entrées sont créées, exécutez les commandes suivantes à partir d’une machine Linux qui est joint au domaine :

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   Cette étape affiche la KVNO du compte d’utilisateur détient le SPN. Pour cette étape fonctionne, le SPN doit disposer au compte MSA lors de sa création. Si le SPN n’a pas été affecté au compte de service administré, le KVNO affiché sera être SPN propriétaire compte d’actuel et incorrect à utiliser pour la configuration.  

1. Démarrer **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Ajoutez le compte de service administré avec les deux commandes suivantes :

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. Écrire le fichier keytab dans un fichier et quittez ktutil :

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. Lorsque vous utilisez l’approche MSA, une option de configuration doit être définie avec la **mssql-conf** outil pour spécifier le compte de service administré à utiliser lors de l’accès au fichier keytab. Vérifiez les valeurs ci-dessous sont dans **/var/opt/mssql/mssql.conf**.

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > Inclure uniquement le nom de compte de service administré et pas le nom de domaine\compte.

## <a id="securekeytab"></a> Sécuriser le fichier keytab

Toute personne ayant accès à ce fichier keytab peut emprunter l’identité de SQL Server sur le domaine, par conséquent, assurez-vous que vous restreindre l’accès au fichier de sorte que seul le compte mssql ait un accès en lecture :

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Configurer SQL Server pour utiliser le fichier keytab pour l’authentification Kerberos

Utiliser comme suit pour configurer le serveur SQL pour commencer à utiliser le fichier keytab pour l’authentification Kerberos.

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

La possibilité de désactiver les connexions UDP au contrôleur de domaine pour améliorer les performances. Dans de nombreux cas, les connexions UDP échouent systématiquement lors de la connexion à un contrôleur de domaine, vous pouvez définir des options de configuration **/etc/krb5.conf** à ignorer les appels d’UDP. Modifier **/etc/krb5.conf** et définir les options suivantes :

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

À ce stade, vous êtes prêt à utiliser des connexions basées sur Active Directory dans SQL Server comme suit.

## <a id="createsqllogins"></a> Créer des connexions basées sur Active Directory dans Transact-SQL

1. Se connecter à SQL Server et créez une connexion de nouveau, basée sur Active Directory :

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. Vérifiez que la connexion est maintenant répertoriée dans l' affichage de catalogue système [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) :

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Se connecter à SQL Server à l’aide de l’authentification Active Directory

Connectez-vous à un ordinateur client à l’aide de vos informations d’identification de domaine. Vous pouvez désormais connecter à SQL Server sans avoir à retaper votre mot de passe à l’aide de l’authentification Active Directory. Si vous créez une connexion pour un groupe AD, tout utilisateur d’Active Directory qui est un membre de ce groupe peut se connecter de la même façon.

Le paramètre de chaîne de connexion spécifique pour les clients à utiliser l’authentification Active Directory varie selon le pilote que vous utilisez. Prenons les exemples dans les sections suivantes.

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>SQLCMD sur un client Linux joints au domaine

Se connecter à un client Linux joints au domaine à l’aide de **ssh** et vos informations d’identification de domaine :

```bash
ssh -l user@contoso.com client.contoso.com
```

Assurez-vous que vous avez installé le [mssql-tools](sql-server-linux-setup-tools.md) du package, puis se connecter à l’aide de **sqlcmd** sans spécifier d’informations d’identification :

```bash
sqlcmd -S mssql-host.contoso.com
```

### <a name="ssms-on-a-domain-joined-windows-client"></a>SSMS sur un client Windows joints à un domaine

Connectez-vous à un client Windows appartenant au domaine à l’aide de vos informations d’identification de domaine. Assurez-vous que SQL Server Management Studio est installé, puis connectez-vous à votre instance de SQL Server (par exemple, `mssql-host.contoso.com`) en spécifiant **l’authentification Windows** dans le **se connecter au serveur** boîte de dialogue.

### <a name="ad-authentication-using-other-client-drivers"></a>Authentification d’Active Directory à l’aide d’autres pilotes clients

Le tableau suivant décrit les recommandations pour les autres pilotes de client :

| Pilote du client | Recommandation |
|---|---|
| **JDBC** | Utiliser l’authentification intégrée Kerberos pour se connecter à SQL Server. |
| **ODBC** | Utiliser l’authentification intégrée. |
| **ADO.NET** | Syntaxe de chaîne de connexion. |

## <a id="additionalconfig"></a> Options de configuration supplémentaires

Si vous utilisez des utilitaires tiers tel que [pbi](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), ou [Centrify](https://www.centrify.com/) pour joindre l’ordinateur hôte Linux AD domaine et que vous souhaitez forcer SQL server à l’aide de l’openldap bibliothèque directement, vous pouvez configurer le **disablesssd** option avec **mssql-conf** comme suit :

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> Il existe des utilitaires tels que **realmd** lequel paramétrer SSSD, tandis que des autres outils tels que le backlog de produit, VAS et Centrify ne pas installer SSSD. Si l’utilitaire utilisé pour joindre le domaine Active Directory n’est pas configuré SSSD, il est recommandé de configurer **disablesssd** option `true`. Il n’est pas obligatoire que SQL Server va tenter d’utiliser SSSD pour AD avant de revenir au mécanisme d’openldap, il serait plus performant à configurer pour que SQL Server effectue des appels openldap directement en contournant le mécanisme SSSD.

Si votre contrôleur de domaine prend en charge le protocole LDAPS, vous pouvez forcer toutes les connexions à partir de SQL Server pour les contrôleurs de domaine sur LDAPS. Pour vérifier votre client peut contacter le contrôleur de domaine via le protocole ldaps, exécutez la commande bash suivante, `ldapsearch -H ldaps://contoso.com:3269`. Pour définir SQL Server à utiliser uniquement le protocole LDAPS, exécutez la commande suivante :

```bash
sudo mssql-conf set network.forcesecureldap true
systemctl restart mssql-server
```

Cette opération utilise LDAPS sur SSSD si AD domain join sur hôte a été effectué via le package SSSD et **disablesssd** n’est pas définie sur true. Si **disablesssd** est défini sur true avec **forcesecureldap** définie sur true, puis il utilisera les protocole LDAPS sur les appels de bibliothèque openldap effectués par SQL Server.

### <a name="post-sql-server-2017-cu14"></a>Publication SQL Server 2017 CU14

En commençant par SQL Server 2017 CU14, si SQL Server a été joint à un contrôleur de domaine Active Directory à l’aide de fournisseurs tiers et est configuré pour utiliser des appels d’openldap pour la recherche AD générale en définissant **disablesssd** à true, vous pouvez également utiliser **enablekdcfromkrb5** option pour forcer SQL Server à utiliser la bibliothèque de krb5 pour la recherche de contrôleur de domaine Kerberos au lieu de la recherche DNS inversée pour le serveur KDC.

Cela peut être utile pour le scénario dans lequel vous souhaitez configurer manuellement les contrôleurs de domaine SQL Server tente de communiquer avec. Et que vous utilisez le mécanisme de bibliothèque openldap à l’aide de la liste KDC dans **krb5.conf**.

Tout d’abord, définissez **disablessd** et **enablekdcfromkrb5conf** à true, puis redémarrez SQL Server :

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

Puis configurez la liste KDC dans **/etc/krb5.conf** comme suit :

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> S’il n’est pas recommandé, il est possible d’utiliser les utilitaires, tels que **realmd**, qui définies lors de la jointure de l’hôte Linux au domaine, lors de la configuration SSSD **disablesssd** sur true pour que SQL Server utilise OpenLDAP appels à la place de SSSD pour Active Directory d’appels associés.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, nous avons vu comment configurer l’authentification Active Directory avec SQL Server sur Linux. Vous avez appris à :
> [!div class="checklist"]
> * Joindre un hôte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à un domaine Active Directory.
> * Créer un utilisateur Active Directory pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et définir le nom principal de service
> * Configurer le service keytab de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
> * Créer des connexions basées sur Active Directory dans Transact-SQL
> * Se connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de l’authentification Active Directory

Ensuite, explorez les autres scénarios de sécurité pour SQL Server sur Linux.

> [!div class="nextstepaction"]
> [Chiffrement des connexions à SQL Server sur Linux](sql-server-linux-encrypted-connections.md)
