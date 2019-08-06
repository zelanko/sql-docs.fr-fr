---
title: Héberger une base de données sur une instance gérée | Microsoft Docs
description: Décrit comment configurer une base de données MDS sur une instance gérée.
ms.custom: ''
ms.date: 07/01/2019
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19519697-c219-44a8-9339-ee1b02545445
author: v-redu
ms.author: lle
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b4ca791a1a0ce46929f4d409d234f8dbc7efdec3
ms.sourcegitcommit: bcc3b2c7474297aba17b7a63b17c103febdd0af9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68794864"
---
# <a name="host-database-on-managed-instance"></a>Base de données hôte sur une instance gérée

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cet article explique comment configurer une base de données MDS sur Managed instance.
  
## <a name="preparation"></a>Préparation

Nous devons terminer les étapes suivantes de la préparation.
- Terminer la création et la configuration d’une instance gérée. Incluez le réseau virtuel et le VPN de point à site.
- Terminer la configuration de l’ordinateur d’application Web.
  - Incluez le VPN de point à site d’installation.
  - Installer des rôles et des fonctionnalités.

**Côté base de données:**

1. Créer une instance gérée Azure SQL Database inclure le réseau virtuel. [Démarrage rapide : Créer une instance gérée Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started)
2. Configurez une connexion de point à site. [Configurez une connexion de point à site à un réseau virtuel à l’aide de l’authentification par certificat Azure Native: Portail Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
3. Configurez l’authentification Azure Active Directory avec SQL Database Managed instance. [Configurer et gérer l’authentification Azure Active Directory avec SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)

**Côté de l’ordinateur d’application Web:**

1. Installez un certificat de connexion de point à site et un VPN pour vous assurer que l’ordinateur peut accéder à SQL Database Managed instance. [Configurez une connexion de point à site à un réseau virtuel à l’aide de l’authentification par certificat Azure Native: Portail Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
2. Installer un rôle et des fonctionnalités. Les fonctionnalités suivantes sont requises.

- Rôles :

      Internet Information Services
      Web Management Tools
      IIS Management Console
      World Wide Web Services
      Application Development
      .NET Extensibility 3.5
      .NET Extensibility 4.5
      ASP.NET 3.5
      ASP.NET 4.5
      ISAPI Extensions
      ISAPI Filters
      Common HTTP Features
      Default Document
      Directory Browsing
      HTTP Errors
      Static Content
      [Note: Do not install WebDAV Publishing]
      Health and Diagnostics
      HTTP Logging
      Request Monitor
      Performance
      Static Content Compression
      Security
      Request Filtering
      Windows Authentication

- Fonctionnalités :

      .NET Framework 3.5 (includes .NET 2.0 and 3.0)
      .NET Framework 4.5 Advanced Services
      ASP.NET 4.5
      WCF Services
      HTTP Activation [Note: This is required.]
      TCP Port Sharing
      Windows Process Activation Service
      Process Model
      .NET Environment
      Configuration APIs
      Dynamic Content Compression

## <a name="install-and-configure-includessmdsshort_mdincludesssmdsshort-mdmd-web-application"></a>Installer et configurer [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] une application Web

Nous devons terminer les étapes suivantes pour installer et [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]configurer.

1. Installez SQL Server fonctionnalité include [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] 2019.
2. Créer une [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] base de données sur l’instance de gestion.
3. Créez et configurez l' [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]application Web pour.
  
**Installer SQL Server 2019**

Vous utilisez l’Assistant Installation de SQL Server ou une invite de commandes pour [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]installer.

1. Double-cliquez sur Setup.exe et suivez les étapes de l’Assistant Installation.

2. Sélectionnez [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] dans la page sélection de fonctionnalités sous fonctionnalités partagées.
Cette opération installe [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], des assemblys, un composant logiciel enfichable Windows PowerShell et des dossiers et fichiers pour les applications et services web.

    ![MDS-SQLServer2019-config-mi-SQLFeatureSelection](../master-data-services/media/mds-sqlserver2019-config-mi-sqlfeatureselection.png "MDS-SQLServer2019-config-MI_SQLFeatureSelection")  

**Configuration de la base de données et du site Web**

1. Connectez le réseau virtuel Windows Azure pour vous assurer que vous pouvez vous connecter à l’instance gérée.

    ![MDS-SQLServer2019-config-mi-P2SVPNConnect](../master-data-services/media/mds-sqlserver2019-config-mi-p2svpnconnect.png "MDS-SQLServer2019-config-MI_P2SVPNConnect")  

2. Lancez le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Puis, dans le volet gauche, cliquez sur **configuration de la base de données** .

3. Cliquez sur **créer une base de données**, puis cliquez sur suivant dans l’Assistant Création d’une **base de données** .

4. Dans la page **serveur de base de données** , renseignez l' **instance de SQL Server** et sélectionnez le **type d’authentification** , puis cliquez sur **tester la connexion** pour confirmer que vous pouvez vous connecter à la base de données en utilisant les informations d’identification du type d’authentification que vous avez sélectionné. Cliquez sur Suivant.

   > [!NOTE]
   > - SQL Server instance pour Managed instance comme «xxxxxxx.xxxxxxx.database.windows.net»
   > - Pour Managed instance, nous prenons en charge le type d’authentification **«Account SQL Server»** et **«Current User-Active Directory Integrated»** .
   > - Lorsque vous sélectionnez **utilisateur actuel: Active Directory intégré** comme type d’authentification, la zone **nom d’utilisateur** est en lecture seule et affiche le nom du compte d’utilisateur Windows qui a ouvert une session sur l’ordinateur. Si vous exécutez SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] sur une machine virtuelle Azure, la zone nom d' **utilisateur** affiche le nom de la machine virtuelle et le nom d’utilisateur du compte d’administrateur local sur la machine virtuelle.

    Vérifiez que votre authentification contient la règle **«sysadmin»** pour Managed instance.
![MDS-SQLServer2019-config-mi-CreateDBConnect](../master-data-services/media/mds-sqlserver2019-config-mi-createdbconnect.png "MDS-SQLServer2019-config-MI_CreateDBConnect")  

5. Tapez un nom dans le champ **Nom de la base de données** . (Facultatif) Pour sélectionner un classement Windows, décochez la case **Classement par défaut de SQL Server**, puis cliquez sur une ou plusieurs des options disponibles comme **Respecter la casse**. Cliquez sur **Suivant**.

    ![MDS-SQLServer2019-config-mi-CreatedDBName](../master-data-services/media/mds-sqlserver2019-config-mi-createddbname.png "MDS-SQLServer2019-config-MI_CreatedDBName")  

6. Dans le champ **nom d’utilisateur** , spécifiez le compte Windows de l’utilisateur pour [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]lequel sera le super utilisateur par défaut. Un Super utilisateur a accès à toutes les zones fonctionnelles et peut ajouter, supprimer et mettre à jour tous les modèles.

    ![MDS-SQLServer2019-config-mi-CreateDBUserName](../master-data-services/media/mds-sqlserver2019-config-mi-createdbusername.png "MDS-SQLServer2019-config-MI_createDBUserName")

7. Cliquez sur **Suivant** pour afficher un récapitulatif des paramètres de la base de données [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] , puis cliquez de nouveau sur **Suivant** pour créer la base de données. La page **État d’avancement et fin** s’affiche.

8. Quand la base de données est créée et configurée, cliquez sur **Terminer**.

    Pour plus d’informations sur les paramètres de l' **Assistant Création d’une base de données**, consultez [ &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Assistant Création d’une base de données Configuration Manager&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).

9. Sur la page **configuration de la base de données** dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], cliquez sur Sélectionner une **base de données**.

10. Cliquez sur **se connecter**, [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] sélectionnez la base de données que vous avez créée à l’étape 8, puis cliquez sur **OK**.

    ![MDS-SQLServer2019-config-mi-connectDBName](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_connectDBName")

11. Dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], cliquez sur **Configuration web** dans le volet gauche.

12. Dans la zone de liste **Site web** , cliquez sur **Site web par défaut**, puis cliquez sur **Créer** pour créer une application web.
![MDS-SQLServer2019-config-mi-Webconfiguration](../master-data-services/media/mds-sqlserver2019-config-mi-webconfiguration.png "MDS-SQLServer2019-config-MI_WebConfiguration")

   > [!NOTE] 
   > Lorsque vous sélectionnez **Site web par défaut**, vous devez créer une application web. Si vous sélectionnez **Créer un nouveau site web** dans la zone de liste, l’application est créée automatiquement.

    

13. Dans la section **pool d’applications** , entrez un autre nom d’utilisateur, entrez le mot de passe, puis cliquez sur OK.
![MDS-SQLServer2019-config-mi-CreateWebApplication](../master-data-services/media/mds-sqlserver2019-config-mi-createwebapplication.png "MDS-SQLServer2019-config-MI_CreateWebApplication")

   > [!NOTE]
   > Vous devez vous assurer que l’utilisateur peut accéder à la base de données avec Active Directory authentification intégrée que vous venez de créer. Vous pouvez aussi modifier la connexion dans Web. config ultérieurement.

    

14. Pour plus d’informations sur la boîte de dialogue **créer une application Web** , consultez boîte de [ &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] dialogue&#41;créer une application Web Configuration Manager](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).

15. Sur la page **configuration Web** de la zone **application Web** , cliquez sur l’application que vous avez créée, puis cliquez sur **Sélectionner** dans la section **associer une application à une base de données** .

16. Cliquez sur **Se connecter**, sélectionnez la base de données [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] que vous souhaitez associer à l’application web, puis cliquez sur **OK**.

    Vous avez terminé la configuration du site web. La page **configuration Web** affiche maintenant le site Web que vous avez sélectionné, l’application Web que [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] vous avez créée et la base de données associée à l’application.

    ![MDS-SQLServer2019-config-mi-WebConfigSelectDB](../master-data-services/media/mds-sqlserver2019-config-mi-webconfigselectdb.png "MDS-SQLServer2019-config-MI_WebConfigSelectDB")

17. Cliquez sur **Appliquer**. La boîte de message **Configuration terminée** s’affiche. Cliquez sur **OK** dans la boîte de message pour lancer l’application web. L’adresse du site Web http://server est nom/application Web/.

## <a name="other-authentication-type-to-connect-managed-instance-database-on-web-application"></a>Autre type d’authentification pour la connexion à la base de données d’instance managée sur l’application Web

Nous pouvons accéder au fichier **Web. config** sous C:\Program Files\Microsoft SQL Server\150\Master Data Services\WebApplication. Nous pouvons modifier la chaîne de connexion pour changer d’autre type d’authentification pour connecter la base de données d’instance gérée.

Le type d’authentification par défaut est «**Active Directory intégré**», à la suite de l’exemple de chaîne de connexion.

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Integrated&quot;" />
```

Nous prenons également en charge l’authentification par mot de passe Active Directory et l’authentification SQL Server, à la suite de l’exemple de chaîne de connexion.

Authentification par mot de passe Active Directory

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Password&quot; ; UID=bob@contoso.onmicrosoft.com; PWD=MyPassWord!" />
```

Authentification SQL Server

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;User ID=UserName;Password=MyPassword!;" />
```

## <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd-and-database-version"></a>Mise [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] à niveau et version de la base de données

**Installation[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]**

Installer la **mise à jour cumulative**de SQL Server [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] 2019, le sera automatiquement mis à jour.

**Mettre à niveau la version de base de données**

Si vous recevez le problème «la version du client est incompatible avec la version de la base de données» après l’installation de SQL Server **mise à jour Cumulative**2019, vous devez mettre à niveau la version de la base de données.

![MDS-SQLServer2019-config-mi-UpgradeDBPage](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbpage.png "MDS-SQLServer2019-config-MI_UpgradeDBPage")

1. Lancez le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Puis, dans le volet gauche, cliquez sur **configuration de la base de données** .

2. Sur la page **configuration de la base de données** dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], cliquez sur Sélectionner une **base de données**.

3. Cliquez sur **se connecter**, [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] sélectionnez la base de données que vous avez associée à l’application Web, puis cliquez sur **OK**.

    ![MDS-SQLServer2019-config-mi-ConnectDBName](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_ConnectDBName")

4. Cliquez sur **mettre à niveau la base de données...** Bouton

    ![MDS-SQLServer2019-config-mi-SelectUpgradeDB](../master-data-services/media/mds-sqlserver2019-config-mi-selectupgradedb.png "MDS-SQLServer2019-config-MI_SelectUpgradeDB")

5. Dans l’Assistant Mise à niveau de la base de données, cliquez sur le bouton **suivant** dans la page d' **Accueil** et la page de **révision** .

    ![MDS-SQLServer2019-config-mi-UpgradeDBWizard](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbwizard.png "MDS-SQLServer2019-config-MI_UpgradeDBWizard")

6. Cliquez sur le bouton **Terminer** lorsque toutes les tâches sont terminées.

## <a name="see-also"></a>Voir aussi

 [Base de données Master Data Services](../master-data-services/master-data-services-database.md) [Application Web Data Manager maître](../master-data-services/master-data-manager-web-application.md) [Page &#40;configuration de la&#41; base de données Gestionnaire de configuration Master Data Services](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md) [Nouveautés de Master Data Services &#40;MDS&#41; ](../master-data-services/what-s-new-in-master-data-services-mds.md)
