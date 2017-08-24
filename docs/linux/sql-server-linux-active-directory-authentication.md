---
title: Authentification Active Directory avec SQL Server sur Linux | Documents Microsoft
description: "Étapes de configuration pour l’authentification AAD pour SQL Server sur Linux"
author: tmullaney
ms.date: 07/17/2017
ms.author: thmullan;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, AAD authentication
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9e6d1afdfa7b7d4ef1bfec4461badca746651c44
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="active-directory-authentication-with-sql-server-on-linux"></a>Authentification Active Directory avec SQL Server sur Linux  
[!INCLUDE[tsql-appliesto-sslinx-only_md](../../docs/includes/tsql-appliesto-sslinx-only_md.md)]


Ce document explique comment configurer [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] sur Linux pour prendre en charge l’authentification Active Directory (AD), également appelée authentification. L’authentification Active Directory permet appartenant au domaine des clients sur Windows ou Linux s’authentifier auprès de [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] à l’aide de leurs informations d’identification de domaine et le protocole Kerberos. L’authentification Active Directory offre les avantages suivants sur [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] l’authentification :  
• Les utilisateurs s’authentifient via l’authentification unique, sans être invité à entrer un mot de passe.   
• En créant des comptes de connexion des groupes Active Directory, vous pouvez gérer l’accès et les autorisations dans [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] à l’aide d’appartenances Active Directory.  
• Chaque utilisateur possède une identité unique de votre organisation, donc vous n’êtes pas obligé d’effectuer le suivi de qui [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] connexions correspondent aux personnes.   
• AD vous permet d’appliquer une stratégie de mot de passe centralisée de votre organisation.   

## <a name="prerequisites"></a>Configuration requise
Avant de configurer l’authentification Active Directory, vous devez :
- Configurer un contrôleur de domaine Active Directory (Windows) sur votre réseau  
- Installation de [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)].
  - [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  - [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  - [Ubuntu](quickstart-install-connect-ubuntu.md)

>  [!IMPORTANT]  
>   À ce stade, la seule méthode d’authentification pris en charge pour le point de terminaison de mise en miroir de base de données est le certificat. Méthode d’authentification WINDOWS est activée dans une version ultérieure

## <a name="step-1-join-includessnoversiondocsincludesssnoversion-mdmd-host-to-ad-domain"></a>Étape 1 : Joindre [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] hôte de domaine Active Directory.
Existent de nombreux outils pour vous aider à joindre le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] ordinateur hôte pour votre domaine Active Directory. Cette procédure pas à pas utilise  **[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)**, un package open source populaires. Si vous n’avez pas encore, installer les packages du client Kerberos et realmd sur la [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] ordinateur hôte à l’aide du Gestionnaire de package de votre distribution Linux :  
```bash  
# RHEL
sudo yum install realmd krb5-workstation

# SUSE
sudo zypper install realmd krb5-client

# Ubuntu
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```  

Si l’installation du package client Kerberos vous invite à entrer un nom de domaine, entrez votre nom de domaine en majuscules.  

>  [!NOTE]  
>  Cette procédure pas à pas utilise « contoso.com » et « CONTOSO.COM » en tant qu’exemples de noms de domaine et le domaine, respectivement. Vous devez remplacer par vos propres valeurs. Ces commandes respectent la casse, par conséquent, assurez-vous que vous utilisez majuscules partout où il est utilisé dans cette procédure pas à pas.  

Exécutez la commande suivante pour vérifier que le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] ordinateur hôte est configuré pour utiliser le contrôleur de domaine Active Directory pour comme un serveur de noms DNS :
```bash  
sudo realm discover contoso.com -v
```  
Si votre domaine n’est trouvé, vous devez configurer votre [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] ordinateur hôte à utiliser l’adresse de votre contrôleur de domaine Active Directory en tant qu’un serveur de noms DNS. Les étapes spécifiques à suivre dépendent de votre configuration réseau de l’appareil, la configuration de domaine et la distribution de Linux. Voici certaines approches d’exemple.

### <a name="example-dns-configuration-ubuntu"></a>Exemple de configuration DNS : Ubuntu
Modifier la `/etc/network/interfaces` de fichiers afin que l’adresse de votre contrôleur de domaine Active Directory est répertorié comme un serveur de noms dns. Par exemple : 
 
```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```  
>  [!NOTE]  
>  L’interface réseau (eth0) peut-être différer pour les ordinateurs de différente. Pour déterminer l’application que vous utilisez, exécutez ifconfig et copier l’interface qui possède une adresse IP et les octets transmis et reçus.

Après avoir modifié ce fichier, redémarrez le service réseau :
```bash
sudo ifdown eth0 && sudo ifup eth0
```
Ensuite, vérifier que votre `/etc/resolv.conf` fichier contient une ligne semblable à la suivante :  
```Code  
nameserver **<AD domain controller IP address>**
```  

### <a name="example-dns-configuration-rhel"></a>Exemple de configuration DNS : RHEL
Modifier la `/etc/sysconfig/network-scripts/ifcfg-eth0` fichier (ou autres config de l’interface de fichiers selon le cas) afin que l’adresse de votre contrôleur de domaine Active Directory est répertorié comme un serveur DNS :

 ```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```
Après avoir modifié ce fichier, redémarrez le service réseau :
```bash
sudo systemctl restart network
```
Ensuite, vérifier que votre `/etc/resolv.conf` fichier contient une ligne semblable à la suivante :  
```Code  
nameserver **<AD domain controller IP address>**
```  

### <a name="join-the-domain"></a>Joindre le domaine
Une fois que vous avez vérifié que votre serveur DNS est correctement configuré, joindre le domaine en exécutant la commande ci-dessous. Vous devez vous authentifier à l’aide d’un compte Active Directory qui dispose de privilèges suffisants dans Active Directory pour joindre un ordinateur au domaine. Plus précisément, cette commande sera créer un nouveau compte d’ordinateur dans Active Directory, créez le `/etc/krb5.keytab` héberger le fichier keytab et configurer le domaine dans `/etc/sssd/sssd.conf`:
```bash                                     
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
 * Successfully enrolled machine in realm
```    

>  [!NOTE]  
>   Si vous voyez une erreur, « les packages nécessaires ne sont pas installés », puis vous devez installer ces packages à l’aide du Gestionnaire de package de votre distribution Linux avant d’exécuter le `realm join` réexécutez la commande. 
>  
>  Si vous recevez une erreur, « Autorisations insuffisantes pour joindre le domaine, » vous devez vérifier avec un administrateur de domaine que vous disposez des autorisations suffisantes pour joindre des ordinateurs Linux à votre domaine.

 
Vérifiez que vous pouvez maintenant collecter des informations relatives à un utilisateur du domaine, et que vous pouvez obtenir un ticket Kerberos en tant qu’utilisateur. 

We will use **id**, **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)** and **[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** commands for this.

```bash  
id user@contoso.com
uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

kinit user@CONTOSO.COM
Password for user@CONTOSO.COM:

klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: user@CONTOSO.COM
<...>
```   

>  [!NOTE]  
>   Si `id user@contoso.com` retourne, « Utilisateur inexistant, » assurez-vous que le service SSSD a démarré en exécutant la commande `sudo systemctl status sssd`. Si le service est en cours d’exécution et que vous rencontrez l’erreur « Aucun utilisateur », essayez d’activer la journalisation documentée pour SSSD. Pour plus d’informations, consultez la documentation de Red Hat pour [SSSD de résolution des problèmes](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).  
>  
>  Si `kinit user@CONTOSO.COM` retourne, « réponse du contrôleur de domaine Kerberos ne correspond pas à attentes lors de l’obtention des informations d’identification initiales, » vérifiez que vous avez spécifié le domaine en majuscules.

Pour plus d’informations, consultez la documentation de Red Hat pour [découverte et la jointure de domaines d’identité](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html). 

## <a name="step-2-create-ad-user-for-includessnoversiondocsincludesssnoversion-mdmd-and-set-spn"></a>Étape 2 : Créer l’utilisateur Active Directory pour [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] et définissez le nom principal de service  

>  [!NOTE]  
>  Dans les étapes suivantes, nous allons utiliser votre [nom de domaine complet](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Si vous êtes sur **Azure**, vous devrez  **[créer un](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/portal-create-fqdn)**  avant de continuer. 

Sur votre contrôleur de domaine, exécutez le [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) commande PowerShell pour créer un nouvel utilisateur AD avec un mot de passe n’expire jamais. Cet exemple montre comment le nom du compte « mssql », mais le nom du compte peut être comme vous le souhaitez. Vous devrez entrer un mot de passe pour le compte :  
```PowerShell   
Import-Module ActiveDirectory

New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
```   

>  [!NOTE]  
>  Il est recommandé d’avoir un compte Active Directory dédié pour SQL Server, afin que les informations d’identification de SQL Server ne sont pas partagées avec d’autres services utilisant le même compte. Toutefois, vous pouvez réutiliser un compte Active Directory existant si vous préférez, si vous connaissez le mot de passe (requis pour générer un fichier keytab à l’étape suivante).

Maintenant définir le nom principal de service (SPN) pour ce compte en utilisant le `setspn.exe` outil. Le SPN doit être formaté exactement comme indiqué dans l’exemple suivant : vous pouvez trouver le nom de domaine complet de le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] ordinateur hôte en exécutant `hostname --all-fqdns` sur la [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] hôte et le port TCP doivent être 1433, sauf si vous avez configuré [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] d’utiliser un numéro de port différent.  
```PowerShell   
setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
```   

>  [!NOTE]  
>  Si vous recevez une erreur, « droits d’accès insuffisants », vous devez vérifier avec un administrateur de domaine que vous disposez des autorisations suffisantes pour définir un nom SPN sur ce compte.
>  
>  Si vous modifiez le port TCP à l’avenir, vous devrez exécuter de nouveau la commande setspn avec le nouveau numéro de port. Vous devrez également ajouter le nouveau nom SPN pour le fichier keytab service de SQL Server en suivant les étapes décrites dans la section suivante.

Pour plus d’informations, consultez [Inscrire un nom de principal du service pour les connexions Kerberos](/sql/database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).  

## <a name="step-3-configure-includessnoversiondocsincludesssnoversion-mdmd-service-keytab"></a>Étape 3 : Configurer [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] keytab de service  
Vérifiez tout d’abord, le numéro de Version de clé (kvno) pour le compte AD créé à l’étape précédente. Généralement, il sera 2, mais il peut être un autre entier si vous avez modifié le mot de passe plusieurs fois. Sur le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] ordinateur hôte, exécutez la commande suivante :

```bash
kinit user@CONTOSO.COM

kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
```

Maintenant, créez un fichier keytab pour l’utilisateur Active Directory que vous avez créé à l’étape précédente. Pour ce faire, nous utiliserons  **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)**. Lorsque vous y êtes invité, entrez le mot de passe pour ce compte Active Directory. 
```bash  
sudo ktutil

ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

quit
```  

>  [!NOTE]  
>  L’outil ktutil ne pas valider le mot de passe, par conséquent, assurez-vous que vous l’entrez correctement.

Toute personne ayant accès à ce `keytab` fichier peut emprunter l’identité [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] sur le domaine, assurez-vous donc vous restreigniez l’accès au fichier tels que seuls les `mssql` compte a accès en lecture :  
```bash  
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```  
Ensuite, configurez [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] d’utiliser cette `keytab` fichier pour l’authentification Kerberos :  
```bash  
sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```  

## <a name="step-4-create-ad-based-logins-in-transact-sql"></a>Étape 4 : Créer des connexions d’accès basée sur Active Directory dans Transact-SQL  
Se connecter à [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] et créer une nouvelle connexion basée sur Active Directory :  
```Transact-SQL  
CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
```   

Vérifiez que la connexion est maintenant répertoriée dans le [sys.server_principals](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql.mc) affichage catalogue système :  
```Transact-SQL  
SELECT name FROM sys.server_principals;
```  

## <a name="step-5-connect-to-includessnoversiondocsincludesssnoversion-mdmd-using-ad-authentication"></a>Étape 5 : Se connecter à [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] à l’aide de l’authentification Active Directory  
Connectez-vous à un ordinateur client à l’aide de vos informations d’identification de domaine. Maintenant vous pouvez vous connecter à [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] sans devoir entrer de nouveau votre mot de passe, à l’aide de l’authentification Active Directory. Si vous créez une connexion pour un groupe AD, tout utilisateur d’Active Directory qui est un membre de ce groupe peut se connecter de la même façon.  
Le paramètre de chaîne de connexion spécifique pour les clients à utiliser l’authentification Active Directory varie selon le pilote que vous utilisez. Voici quelques exemples figurent ci-dessous.  

## <a name="examples"></a>Exemples  
### <a name="example-1-sqlcmd-on-a-domain-joined-linux-client"></a>Exemple 1 : `sqlcmd` sur un client Linux appartenant au domaine  
Se connecter à un client Linux appartenant au domaine à l’aide de `ssh` et vos informations d’identification de domaine :  
```bash  
ssh -l user@contoso.com client.contoso.com
```  

Vérifiez que vous avez installé le [mssql-tools](sql-server-linux-setup-tools.md) du package, puis se connecter à l’aide de `sqlcmd` sans spécifier d’informations d’identification :  
```bash  
sqlcmd -S mssql.contoso.com
```  

### <a name="example-2-ssms-on-a-domain-joined-windows-client"></a>Exemple 2 : Les SSMS sur un client Windows appartenant au domaine  
Connectez-vous à un client Windows appartenant au domaine à l’aide de vos informations d’identification de domaine. Assurez-vous que [!INCLUDE[ssmanstudiofull-md](../../docs/includes/ssmanstudiofull-md.md)] est installé, puis vous connecter à votre [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] instance en spécifiant **l’authentification Windows** dans les **se connecter au serveur** boîte de dialogue.  

### <a name="ad-authentication-using-other-client-drivers"></a>Authentification d’Active Directory à l’aide d’autres pilotes de clients  
• JDBC : [à l’aide de Kerberos intégré à l’authentification de connexion SQL Server](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server])  
• ODBC : [à l’aide de l’authentification intégrée](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)  
• ADO.NET : [syntaxe de chaîne de connexion](https://msdn.microsoft.com/library/ms254500.aspx)   


