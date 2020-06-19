---
title: Activer et désactiver les groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936850"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a>Activer et désactiver les groupes de disponibilité AlwaysOn (SQL Server)
  L'activation de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] est indispensable pour qu'une instance de serveur utilise des groupes de disponibilité. Avant de pouvoir créer et configurer un groupe de disponibilité, la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] doit avoir été activée sur chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui hébergera un réplica de disponibilité pour un ou plusieurs groupes de disponibilité.  
  
> [!IMPORTANT]  
>  Si vous supprimez et recréez un cluster WSFC, vous devez désactiver puis réactiver la fonctionnalité [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui hébergeait un réplica de disponibilité sur le cluster WSFC d'origine.  
  
-   **Avant de commencer :**  
  
     [Composants requis](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Comment:**  
  
    -   [Déterminer si l'option Groupes de disponibilité AlwaysOn est activée](#IsEnabled)  
  
    -   [Activation des groupes à haute disponibilité AlwaysOn](#EnableAOAG)  
  
    -   [Désactiver les groupes de disponibilité AlwaysOn](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a>Conditions préalables à l’activation de groupes de disponibilité AlwaysOn  
  
-   L'instance de serveur doit résider sur un nœud de Clustering de basculement Windows Server (WSFC).  
  
-   L'instance du serveur doit exécuter une édition de SQL Server qui prend en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Pour plus d’informations, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   Activez les groupes de disponibilité AlwaysOn sur une seule instance de serveur à la fois. Après avoir activé les groupes de disponibilité AlwaysOn, attendez le redémarrage du service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avant de passer à une autre instance de serveur.  
  
 Pour plus d’informations sur les conditions préalables supplémentaires pour la création et la configuration des groupes de disponibilité, consultez [conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Lorsque les groupes de disponibilité AlwaysOn sont activés sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'instance de serveur a le contrôle total sur le cluster WSFC.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au groupe **Administrateur** sur l'ordinateur local et le contrôle total sur le cluster WSFC. Pour activer AlwaysOn à l'aide de PowerShell, ouvrez la fenêtre d'invite de commandes en utilisant l'option **Exécuter en tant qu'administrateur** .  
  
 Requiert des autorisations de création et de gestion d'objets Active Directory.  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a>Déterminer si groupes de disponibilité AlwaysOn est activé  
  
-   [SQL Server Management Studio](#SSMS1Procedure)  
  
-   [Transact-SQL](#Tsql1Procedure)  
  
-   [PowerShell](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> Utilisation de SQL Server Management Studio  
 **Pour déterminer si l'option Groupes de disponibilité AlwaysOn est activée**  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur l’instance de serveur, puis sélectionnez **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés du serveur** , cliquez sur la page **Général** . La propriété **Is HADR Enabled** affiche une des valeurs suivantes :  
  
    -   **True**, si l'option Groupes de disponibilité AlwaysOn est activée  
  
    -   **False**, si l'option Groupes de disponibilité AlwaysOn est désactivée.  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> Utilisation de Transact-SQL  
 **Pour déterminer si l'option Groupes de disponibilité AlwaysOn est activée**  
  
1.  Utilisez l'instruction [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) suivante :  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     Le paramètre de la propriété de serveur `IsHadrEnabled` indique si une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est activée pour les groupes de disponibilité AlwaysOn, comme suit :  
  
    -   Si `IsHadrEnabled` = 1, l'option Groupes de disponibilité AlwaysOn est activée.  
  
    -   Si `IsHadrEnabled` = 0, l'option Groupes de disponibilité AlwaysOn est désactivée.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la `IsHadrEnabled` propriété de serveur, consultez [ServerProperty &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql).  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a> Utilisation de PowerShell  
 **Pour déterminer si l'option Groupes de disponibilité AlwaysOn est activée**  
  
1.  Définissez la valeur par défaut ( `cd` ) sur l’instance de serveur (par exemple `\SQL\NODE1\DEFAULT` ,) sur laquelle vous souhaitez déterminer si [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] est activé.  
  
2.  Entrez la commande PowerShell `Get-Item` suivante :  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a>Activer groupes de disponibilité AlwaysOn  
 **Pour activer AlwaysOn, utilisez :**  
  
-   [Gestionnaire de configuration SQL Server](#SQLCM2Procedure)  
  
-   [PowerShell](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a>Utilisation de Gestionnaire de configuration SQL Server  
 **Pour activer les groupes de disponibilité AlwaysOn**  
  
1.  Connectez-vous au nœud de clustering de basculement Windows Server (WSFC) qui héberge l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur laquelle vous souhaitez activer les groupes de disponibilité AlwaysOn.  
  
2.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
3.  Dans **Gestionnaire de configuration SQL Server**, cliquez sur **services SQL Server**, cliquez avec le bouton droit sur SQL Server (** < *`instance name`*>)**, où **<*`instance name`*>** est le nom d’une instance de serveur local pour laquelle vous souhaitez activer groupes de disponibilité AlwaysOn, puis cliquez sur **Propriétés.**  
  
4.  Sélectionnez l’onglet **haute disponibilité AlwaysOn** .  
  
5.  Vérifiez que le champ **Nom du cluster de basculement Windows** contient le nom du cluster de basculement local. Si ce champ est vide, cette instance de serveur ne prend pas en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]pour le moment. L'ordinateur local n'est pas un nœud de cluster, le cluster WSFC a été arrêté, ou cette édition de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ne prend pas en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
6.  Activez la case à cocher **activer la groupes de disponibilité AlwaysOn** , puis cliquez sur **OK**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enregistre votre modification. Ensuite, vous devez redémarrer manuellement le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Cela vous permet de choisir l'heure de redémarrage la plus adaptée aux besoins de l'entreprise. Lorsque le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] redémarre, AlwaysOn est activé, et la propriété de serveur `IsHadrEnabled` a la valeur 1.  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> Utilisation de PowerShell SQL Server  
 **Pour activer AlwaysOn**  
  
1.  Changez de répertoire (`cd`) pour accéder à une instance de serveur pour laquelle vous voulez activer les groupes de disponibilité AlwaysOn.  
  
2.  Utilisez l'applet de commande `Enable-SqlAlwaysOn` pour activer les groupes de disponibilité AlwaysOn.  
  
     Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la façon de contrôler si l’applet de commande redémarre le `Enable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, consultez à [quel moment une applet de commande redémarre-t-elle le service SQL Server ?](#WhenCmdletRestartsSQL), plus loin dans cette rubrique.  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a>Exemple : Enable-SqlAlwaysOn  
 La commande PowerShell suivante active [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sur une instance de SQL Server (instance de l'*ordinateur* \\ *Instance*).  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a>Désactiver les groupes de disponibilité AlwaysOn  
  
-   **Avant de désactiver AlwaysOn :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour désactiver AlwaysOn, utilisez :**  
  
    -   [Gestionnaire de configuration SQL Server](#SQLCM3Procedure)  
  
    -   [PowerShell](#PScmd3Procedure)  
  
-   **Suivi :**  [Après la désactivation d'AlwaysOn](#FollowUp)  
  
> [!IMPORTANT]  
>  Désactivez AlwaysOn sur une seule instance de serveur à la fois. Après avoir désactivé les groupes de disponibilité AlwaysOn, attendez le redémarrage du service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avant de passer à une autre instance de serveur.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
 Avant de désactiver AlwaysOn sur une instance de serveur, nous vous recommandons d'effectuer les opérations suivantes :  
  
1.  Si l'instance de serveur héberge actuellement le réplica principal d'un groupe de disponibilité que vous souhaitez conserver, nous recommandons de basculer manuellement le groupe de disponibilité vers un réplica secondaire synchronisé, si possible. Pour plus d’informations, consultez [Effectuer un basculement manuel planifié d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
2.  Supprimez tous les réplicas secondaires locaux. Pour plus d’informations, consultez [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md).  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a>Utilisation de Gestionnaire de configuration SQL Server  
 **Pour désactiver AlwaysOn**  
  
1.  Connectez-vous au nœud de clustering de basculement Windows Server (WSFC) qui héberge l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur laquelle vous souhaitez désactiver les groupes de disponibilité AlwaysOn.  
  
2.  Dans le menu **Démarrer** , pointez sur **tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] , sur **outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
3.  Dans **Gestionnaire de configuration SQL Server**, cliquez sur **services SQL Server**, cliquez avec le bouton droit sur SQL Server (** < *`instance name`*>)**, où **<*`instance name`*>** est le nom d’une instance de serveur local pour laquelle vous souhaitez désactiver groupes de disponibilité AlwaysOn, puis cliquez sur **Propriétés**.  
  
4.  Sur l’onglet**Haute disponibilité AlwaysOn**, décochez la case **Activer les groupes de disponibilité AlwaysOn** , puis cliquez sur **OK**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enregistre votre modification et redémarre le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Lorsque le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] redémarre, AlwaysOn est désactivé, et la propriété de serveur `IsHadrEnabled` a la valeur 0, pour indiquer que l'option Groupes de disponibilité AlwaysOn est désactivée.  
  
5.  Nous vous recommandons de lire les informations de la section [Suivi : Après la désactivation d'AlwaysOn](#FollowUp), plus loin dans cette rubrique.  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> Utilisation de PowerShell SQL Server  
 **Pour désactiver AlwaysOn**  
  
1.  Remplacez le répertoire ( `cd` ) par une instance de serveur actuellement activée que vous souhaitez désactiver pour groupes de disponibilité AlwaysOn.  
  
2.  Utilisez l'applet de commande `Disable-SqlAlwaysOn` pour activer les groupes de disponibilité AlwaysOn.  
  
     Par exemple, la commande suivante désactive groupes de disponibilité AlwaysOn sur une instance de SQL Server (instance de l'*ordinateur* \\ *Instance*).  Cette commande nécessite le redémarrage de l'instance et vous serez invité à confirmer ce redémarrage.  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  Pour plus d’informations sur la façon de contrôler si l’applet de commande redémarre le `Disable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, consultez à [quel moment une applet de commande redémarre-t-elle le service SQL Server ?](#WhenCmdletRestartsSQL), plus loin dans cette rubrique.  
  
     Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a>Suivi : après la désactivation d’AlwaysOn  
 Après avoir désactivé des groupes de disponibilité AlwaysOn, l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit être redémarrée. Le Gestionnaire de configuration SQL redémarre l'instance de serveur automatiquement. Toutefois, si vous avez utilisé l'applet de commande `Disable-SqlAlwaysOn`, vous devez redémarrer l'instance de serveur manuellement. Pour plus d’informations, consultez [sqlservr Application](../../../tools/sqlservr-application.md).  
  
 Sur l'instance de serveur redémarrée :  
  
-   Les bases de données de disponibilité ne démarrent pas au démarrage de SQL Server, ce qui les rend inaccessibles.  
  
-   La seule instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] AlwaysOn prise en charge est [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql). Les options CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP et SET HADR de ALTER DATABASE ne sont pas prises en charge.  
  
-   Les métadonnées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et les données de configuration [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans WSFC ne sont pas affectées par la désactivation des groupes de disponibilité AlwaysOn.  
  
 Si vous désactivez définitivement des groupes de disponibilité AlwaysOn sur chaque instance de serveur qui héberge un réplica de disponibilité pour un ou plusieurs groupes de disponibilité, nous recommandons de procéder comme suit :  
  
1.  Si vous ne supprimez pas les réplicas de disponibilité locaux avant de désactiver AlwaysOn, supprimez (avec l'instruction Drop) chaque groupe de disponibilité pour lequel l'instance de serveur héberge un réplica de disponibilité. Pour plus d’informations sur la suppression d’un groupe de disponibilité, consultez [Supprimer un groupe de disponibilité &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md).  
  
2.  Pour supprimer les métadonnées restantes, supprimez (avec l'instruction Drop) chaque groupe de disponibilité affecté sur une instance de serveur qui fait partie du cluster WSFC d'origine.  
  
3.  Toutes les bases de données primaires restent accessibles à toutes les connexions, mais la synchronisation des données entre les bases de données primaires et secondaires est arrêtée.  
  
4.  Les bases de données secondaires passent à l'état RESTORING. Vous pouvez les supprimer ou les restaurer à l'aide de RESTORE WITH RECOVERY. Toutefois, les bases de données restaurées ne participent plus à la synchronisation des données des groupes de disponibilité.  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a>Quand une applet de commande redémarre-t-elle le service SQL Server ?  
 Sur une instance de serveur en cours d'exécution, l'utilisation de `Enable-SqlAlwaysOn` ou de `Disable-SqlAlwaysOn` pour modifier le paramètre actuel d'AlwaysOn peut entraîner le redémarrage du service SQL Server. Le comportement de redémarrage dépend des conditions suivantes :  
  
|Paramètre -NoServiceRestart spécifié|Paramètre -Force spécifié|Le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a-t-il été redémarré ?|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|Non|Non|Par défaut. Mais l'applet de commande vous invite à agir comme suit :<br /><br /> **Pour effectuer cette action, vous devez redémarrer le service SQL Server pour l’instance de serveur « <instance_name> ». Voulez-vous continuer ?**<br /><br /> **[Y] Oui [N] Non [S] Suspendre [?] Aide (la valeur par défaut est « Y ») :**<br /><br /> Si vous spécifiez **N** ou **S**, le service n'est pas redémarré.|  
|Non|Oui|Le service est redémarré.|  
|Oui|No|Le service n'est pas redémarré.|  
|Yes|Yes|Le service n'est pas redémarré.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)  
