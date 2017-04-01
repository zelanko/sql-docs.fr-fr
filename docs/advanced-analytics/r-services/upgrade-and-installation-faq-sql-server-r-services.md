---
title: "FAQ d’installation et de mise &#224; niveau (services SQL Server R) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 58
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 47
---
# FAQ d’installation et de mise &#224; niveau (services SQL Server R)
  Cette rubrique fournit des réponses aux questions courantes sur l’installation et sur les mises à niveau à partir des versions préliminaires de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
 Si vous installez [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pour la première fois, suivez les procédures suivantes de configuration de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et des composants R telles que décrites ici : [Configurer SQL Server R Services &#40;dans la base de données&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  

   
## <a name="important-changes-from-pre-releae-versions"></a>Modifications importantes par rapport aux versions préliminaires  
 Si vous avez installé une version préliminaire de SQL Server 2016, ou si vous utilisez des instructions de configuration publiées avant la commercialisation de SQL Server 2016, il est important que vous sachiez que le processus de configuration est complètement différent entre les versions préliminaires et les versions RTM. Ces modifications concernent les options disponibles dans l’Assistant de configuration de SQL Server et les étapes de post-installation. 
   
> [!WARNING] Les nouvelles installations de versions préliminaires de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ne sont plus prises en charge. Nous vous recommandons d’effectuer la mise à niveau dès que possible.  
+ Si vous avez installé [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] dans CTP3, CTP3.1, CTP3.2, RC0 ou RC1, vous devrez réexécuter le script d’installation post-configuration pour désinstaller les versions précédentes des composants R et de R Services. 
+ Le script d’installation post-configuration est fourni uniquement pour aider les clients à désinstaller les versions préliminaires.  Ne l’exécutez pas lors de l’installation d’une version plus récente.

## <a name="how-to-uninstall-previous-versions-of-r-services"></a>Comment désinstaller les versions antérieures de R Services

Il est important que vous désinstalliez les versions précédentes de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] et leurs composants R associés dans le bon ordre.

### <a name="1-run-script-to-deregister-windows-user-group-and-components-before-uninstalling-previous-components"></a>1. Exécutez le script pour annuler l’inscription du groupe d’utilisateurs Windows et des composants avant de désinstaller les composants précédents
Si vous avez installé une version préliminaire de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], commencez par exécuter le script `RegisteREext.exe` avec l’argument `/uninstall`.

Ce faisant, vous annulez l’inscription des anciens composants et supprimez le groupe d’utilisateurs Windows associé à Launchpad. Si vous ne le faites pas, vous ne pourrez pas créer le groupe d’utilisateurs Windows requis pour toutes les nouvelles instances que vous installez.
  
Par exemple, si vous avez installé R Services sur l’instance par défaut, exécutez cette commande à partir du répertoire dans lequel le script est installé :  
  
~~~~
    RegisterRExt.exe /UNINSTALL  
~~~~ 
  
Si vous avez installé R Services sur une instance nommée, spécifiez le nom de l’instance après *INSTANCE :*  
  
~~~~ 
RegisterRExt.exe /UNINSTALL /INSTANCE:<instancename>   
~~~~  

Vous devrez peut-être exécuter le script plusieurs fois pour supprimer tous les composants.

> [!NOTE]
> L’emplacement par défaut de ce script est différent, selon la version préliminaire que vous installez. Si vous essayez d’exécuter une version incorrecte du script, vous pouvez obtenir une erreur. 
> 
>  + Si vous disposez de CTP 3.1, 3.2 ou 3.3, avant de pouvoir désinstaller les composants, vous devez télécharger une version mise à jour du script de configuration post-installation à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkId=723194). Le script mis à jour prend en charge la désinscription de composants plus anciens. Cliquez sur le lien et sélectionnez **Enregistrer sous** pour enregistrer le script dans un dossier local. Renommez le script existant, puis copiez le nouveau script dans le dossier dans lequel le script sera exécuté. 
>  + Pour RC0, le fichier de script correct a été installé et se trouve dans ce dossier : `C:\Program Files\Microsoft\MRO-for-RRE\8.0\R-3.2.2\library\RevoScaleR\rxLibs\x64`  
>  + Pour les versions publiées (13.0.1601.5 ou version ultérieure), aucun script n’est nécessaire pour installer ou configurer des composants. Le script doit être utilisé uniquement pour la suppression de composants plus anciens. 


### <a name="2-uninstall-any-older-versions-of-the-revolution-enterprise-tools-including-components-installed-with-ctp-releases"></a>2. Désinstallez les anciennes versions des outils Revolution Enterprise, notamment les composants installés avec les versions CTP.

L’ordre de désinstallation des composants R est essentiel. Désinstallez toujours [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)] en premier. Ensuite, désinstallez [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)].  

 Si vous désinstallez d’abord R Open par inadvertance et obtenez un message d’erreur lorsque vous essayez de désinstaller Revolution R Enterprise, vous pouvez réinstaller Revolution R Open ou Microsoft R Open, puis désinstaller les deux composants dans le bon ordre.  

### <a name="3-uninstall-any-other-version-of-microsoft-r-open"></a>3. Désinstallez toute autre version de Microsoft R Open.

Enfin, désinstallez toutes les autres versions de Microsoft R Open.
 
### <a name="4-upgrade-sql-server"></a>4. Mise à niveau vers SQL Server  
  
Une fois que tous les composants préliminaires ont été désinstallés, redémarrez l’ordinateur. Il s’agit d’une exigence de configuration de SQL Server ; vous ne pourrez pas procéder à une installation à jour jusqu’à ce qu’un redémarrage soit terminé.     

Une fois que cette opération effectuée, exécutez la configuration de SQL Server et suivez ces instructions pour installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] : [Configurer SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
Aucun composant supplémentaire n’est requis. Les packages R et les packages de connectivité sont installés lors de la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 


## <a name="upgrading-r-components"></a>Mise à niveau des composants R

À mesure que des correctifs ou améliorations à SQL Server 2016 sont publiés, les composants R sont mis à niveau ou actualisés, si votre instance comprend déjà la fonctionnalité R Services. 

Toutefois, lors de la mise à niveau ou de la correction de serveurs qui ne sont pas connectés à Internet, vous devez télécharger manuellement une version mise à jour des composants R avant de lancer l’actualisation. Pour plus d’informations, consultez [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).

## <a name="problems-uninstalling-older-versions-of-r"></a>Problèmes de désinstallation des versions anciennes de R  
Dans certains cas, les anciennes versions de Revolution R Open ou de Revolution R Enterprise ne sont pas complètement supprimées par le processus de désinstallation.  
  
 Si vous rencontrez des problèmes de suppression d’une version antérieure, vous pouvez également modifier le Registre pour supprimer les clés associées.  
  
 Ouvrez le Registre Windows et recherchez cette clé : `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.  
  
 Supprimez toutes les entrées suivantes, le cas échéant, et si la clé contient uniquement une seule valeur `sEstimatedSize2` :  
  
-   E0B2C29E-B8FC-490B-A043-2CAE75634972        (pour 8.0.2)  
  
-   46695879-954E-4072-9D32-1CC84D4158F4        (pour 8.0.1)  
  
-   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (pour 8.0.0)  
  
-   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (pour 7.5.0)  


## <a name="new-license-agreement-for-r-components-required-for-unattended-installs"></a>Nouveau contrat de licence pour les composants R requis pour les installations sans assistance  
 Si vous utilisez la ligne de commande pour mettre à niveau une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur laquelle [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est déjà installé, vous devez modifier la ligne de commande pour utiliser le nouveau paramètre de contrat de licence, */IACCEPTROPENLICENSEAGREEMENT*. 
 
 Si vous n’utilisez pas l’argument approprié, la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risque d’échouer.  
  
## <a name="after-running-setup-includersqlproductnametokenrsqlproductnamemdmd-is-still-not-enabled"></a>Après avoir exécuté la configuration, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] n’est pas encore activé  
 La fonctionnalité qui prend en charge l’exécution de scripts externes est désactivée par défaut, même si elle est installée. Il s’agit d’un paramètre par défaut, pour la réduction de la surface d’exposition.  
  
 Pour activer les scripts R, un administrateur peut exécuter l’instruction suivante dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] :  
  
1.  Sur l’instance [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] où vous souhaitez utiliser R, exécutez cette instruction.  
  
    ```  
    sp_configure 'external scripts enabled',1 
    reconfigure with override  
    ```  
  
2.  Redémarrez l’instance.  
  
3.  Après avoir redémarré l’instance, ouvrez **SQL Server Configuration Manager** ou le panneau **Services** et vérifiez que le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] est en cours d’exécution.  

> [!TIP] Pour installer une instance R Services préconfigurée, utilisez l’image de machine virtuelle Azure qui inclut Enterprise Edition avec R Services activés. Pour plus d’informations, voir [Installation de SQL Server R Services sur une machine virtuelle Azure](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md).
 

## <a name="setup-of-includersqlproductnametokenrsqlproductnamemdmd-not-available-in-a-failover-cluster"></a>Configuration de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non disponible dans un cluster de basculement  
 Actuellement, il n’est pas possible d’installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un cluster de basculement.  
    
 Toutefois, vous pouvez installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un ordinateur autonome qui utilise Always On et fait partie d’un groupe de disponibilité. Pour plus d’informations sur l’utilisation de R Services dans un groupe de disponibilité Always On, consultez [Groupes de disponibilité Always On : interopérabilité](../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md).  

Une autre option consiste à configurer un réplica sur une autre instance de SQL Server pour exécuter des scripts R. Le réplica peut être créé à l’aide de la réplication ou de la copie des journaux de transaction.
 
## <a name="launchpad-service-cannot-be-started"></a>Le service Launchpad ne peut pas être démarré  

Il existe plusieurs problèmes qui peuvent empêcher le démarrage de LaunchPad.
+ **Notation 8dot3 non activée**.  Pour installer R Services (dans la base de données), le lecteur où est installé le composant doit prendre en charge la création de noms de fichiers courts avec la notation **8dot3**.  Un nom de fichier 8.3 est également appelé nom de fichier court et est utilisé pour la compatibilité avec les versions antérieures de Microsoft Windows ou en tant que substitution du nom de fichier long. 

  Si le volume sur lequel vous installez [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ne prend pas en charge les noms de fichiers courts, les processus qui lancent R à partir de SQL Server peuvent ne pas être en mesure de localiser le fichier exécutable correct et [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ne démarre pas.  
  
   Pour résoudre ce problème, vous devez activer la notation 8dot3 sur le volume où SQL Server et R Services sont installés. Vous devez ensuite fournir le nom court pour le répertoire de travail dans le fichier de configuration de R Services. 

    1. Pour activer la notation 8dot3, exécutez l’utilitaire **fsutil** avec l’argument *8dot3name* comme indiqué ici : [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).
    2. Après l’activation de la notation 8dot3, ouvrez le fichier RLauncher.config. Dans une installation par défaut, le fichier RLauncher.config se trouve sous C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn
    3. Notez la propriété pour WORKING_DIRECTORY.
    4. Utilisez l’utilitaire fsutil avec l’argument *file* pour spécifier un chemin d’accès de fichier court pour le dossier spécifié dans WORKING_DIRECTORY.
    5. Modifiez le fichier de configuration pour utiliser le nom court pour WORKING_DIRECTORY.   
     
Vous pouvez également spécifier un répertoire différent pour WORKING_DIRECTORY ayant un chemin d’accès compatible avec la notation 8dot3.     
   
   > [!NOTE] Cette restriction sera supprimée dans une version ultérieure. 
 
+ **Le compte qui exécute Launchpad a été modifié ou des autorisations nécessaires ont été supprimées.** Par défaut, au démarrage, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] utilise le compte suivant qui est configuré par la configuration [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] pour disposer de toutes les autorisations nécessaires : NT Service\MSSQLLaunchpad

  Par conséquent, si vous assignez un autre compte au Launchpad ou si le droit est supprimé par une stratégie sur l’ordinateur SQL Server, le compte ne dispose peut-être pas des autorisations nécessaires. Il est possible que vous voyiez cette erreur : *Échec d’ouverture de session ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) : l’utilisateur ne bénéficie pas du type d’ouverture de session demandé sur cet ordinateur.*

  Pour accorder les autorisations nécessaires au nouveau compte de service, utilisez l’application de **stratégie de sécurité locale** et mettez à jour les autorisations sur le compte pour inclure ces autorisations :
  + Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
  + Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
  + Ouvrir une session en tant que service (SeServiceLogonRight)
  + Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

  Pour plus d’informations sur les autorisations d’exécution des services SQL Server, consultez [Configurer les comptes de service Windows et les autorisations](https://msdn.microsoft.com/library/ms143504.aspx#Windows).
  
## <a name="side-by-side-installation-not-supported"></a>Installation côte à côte non prise en charge  
 Ne créez pas une installation côte à côte en utilisant une autre version de R ou d’autres versions de Revolution Analytics.  

## <a name="offline-installation-of-r-components-for-localized-version-of-sql-server"></a>Installation hors connexion des composants R pour la version localisée de SQL Server 
Si vous installez R Services sur un ordinateur qui n’a pas accès à Internet, deux étapes supplémentaires s’imposent : vous devez télécharger le programme d’installation du composant R vers un dossier local avant d’exécuter la configuration SQL Server, et vous devez modifier le fichier du programme d’installation pour vous assurer que la langue correcte est installée. 

L’identificateur de langue utilisé pour les composants R doit être le même que la langue de configuration de SQL Server en cours d’installation, sinon le bouton **Suivant** est désactivé et vous ne pouvez pas terminer la configuration.

Pour plus d’informations, consultez [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md). 
  
## <a name="unable-to-launch-runtime-for-r-script"></a>Impossible de lancer le runtime pour le script R
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] crée un groupe d’utilisateurs Windows qui est utilisé par le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] pour exécuter les tâches R. Ce groupe d’utilisateurs doit avoir la possibilité de se connecter à l’instance qui exécute R Services afin d’exécuter R pour le compte d’utilisateurs distants qui utilisent l’authentification intégrée Windows.
  
 Dans un environnement dans lequel le groupe Windows pour les utilisateurs R (**SQLRUsers**) n’a pas cette autorisation, vous pouvez rencontrer les erreurs suivantes :  
  
-   Quand vous tentez d’exécuter des scripts R :  
  
     *Impossible de lancer le runtime pour le script « R ». Vérifiez la configuration du runtime « R ».*  
  
     *Une erreur de script externe s’est produite. Impossible de lancer le runtime.*  
  
-   Erreurs générées par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] :  
  
     *Impossible d’initialiser le lanceur RLauncher.dll*  
  
     *Aucune DLL de lanceur n’a été enregistrée.*  
  
-   Les journaux de sécurité indiquent que le compte NT SERVICE\MSSQLLAUNCHPAD n’a pas pu se connecter.  
  
Pour plus d’informations sur l’attribution des autorisations nécessaires à ce groupe d’utilisateurs, consultez [Configurer SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md). 

> [!NOTE]
> 
> Cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante. 

  
## <a name="remote-execution-via-odbc"></a>Exécution à distance via ODBC   
 Si vous utilisez une station de travail de science des données et que vous vous connectez à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter des commandes R à l’aide des fonctions **RevoScaleR**, vous pouvez obtenir une erreur lors de l’utilisation d’appels ODBC qui écrivent des données sur le serveur. 
 
 La raison est identique à celle décrite dans la section précédente : lors de la configuration, R Services crée un groupe de comptes de travail utilisés pour exécuter des tâches R. Toutefois, si ces comptes ne peuvent pas se connecter au serveur, les appels ODBC ne peuvent pas être passés pour votre compte. 
 
 Notez que cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante, car les informations d’identification de connexion SQL sont transmises explicitement du client R vers l’instance SQL Server, puis vers ODBC.
  
Pour activer l’authentification implicite, vous devez attribuer à ce groupe de comptes de travail des autorisations comme suit :  
    
1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en tant qu’administrateur sur l’instance où vous exécuterez le code R. 

2. Exécutez le script suivant. Veillez à modifier le nom du groupe d’utilisateurs, si vous avez modifié la valeur par défaut, ainsi que le nom de l’ordinateur et de l’instance.
    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO  
    ```

Pour plus d’informations et pour connaître la procédure avec l’interface utilisateur [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez [Configurer SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).

    
## <a name="errors-during-setup-because-r-components-cannot-be-installed"></a>Erreurs lors de la configuration, car les composants R ne peuvent pas être installés  
 Lorsque vous installez R Services (dans la base de données) à l’aide de la configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], lorsque vous cliquez sur **Accepter** sur la page contenant les termes de licence Microsoft R Open, la configuration doit rechercher les composants et commencer l’installation lorsque les autres composants sont installés. Toutefois, dans les cas suivants, l’installation des composants risque d’échouer :  
  
-   Vous effectuez une installation hors connexion et les composants ne peuvent pas être téléchargés.  
  
     [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)  
  
-   Vous utilisez l’option de recherche des mises à jour et le service de mise à jour renvoie une erreur, car il ne trouve pas la version correcte du composant.  
  
  Il s’agit d’un problème connu qui a été corrigé dans RC3.  
  
 
  
## <a name="upgrade-of-r-server-standalone-to-rc3-requires-uninstallation-using-the-rc2-setup-utility"></a>La mise à niveau de R Server (autonome) à RC3 nécessite la désinstallation à l’aide de l’utilitaire de configuration RC2
 Microsoft R Server (autonome) a été introduit dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2. Pour mettre à niveau vers la version RC3 de Microsoft R Server, vous devez d’abord désinstaller à l’aide de la configuration [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2, puis réinstaller à l’aide de la configuration [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC3.  
  
1.  Désinstallez R Server R (autonome) pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2 à l’aide de la configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Mettez à niveau [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers RC3 et sélectionnez l’option d’installation de R Services (dans la base de données). Cela met à niveau l’instance de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vers RC3 ; aucune configuration supplémentaire n’est nécessaire.  
  
3.  Exécutez la configuration [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour RC3 une fois de plus, et installez Microsoft R Server (autonome).  

Cette solution de contournement n’est pas obligatoire lors de la mise à niveau vers la version RTM de Microsoft R Server.

## <a name="see-also"></a>Voir aussi  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [Bien démarrer avec Microsoft R Server &#40;autonome&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  