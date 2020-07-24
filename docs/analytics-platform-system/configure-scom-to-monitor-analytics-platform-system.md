---
title: Configurer System Center Operations Manager pour surveiller les points d’accès
description: Procédez comme suit pour configurer les packs d’administration System Center Operations Manager (SCOM) pour Analytics Platform System. Les packs d’administration sont requis pour analyser le système de plateforme d’analyse à partir de SCOM.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 0786cbc8230ecf29dd377a35fefc6969072512b3
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942211"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Configurer System Center Operations Manager (SCOM) pour surveiller Analytics Platform System
Procédez comme suit pour configurer les packs d’administration System Center Operations Manager (SCOM) pour Analytics Platform System. Les packs d’administration sont requis pour analyser le système de plateforme d’analyse à partir de SCOM.  
  
## <a name="before-you-begin"></a><a name="BeforeBegin"></a>Avant de commencer  
**Composants requis**  
  
System Center Operations Manager 2007 R2 doit être installé et en cours d’exécution.  
  
Les packs d’administration doivent être installés et configurés. Consultez [installation des packs d’administration scom &#40;Analytics Platform system&#41;](install-the-scom-management-packs.md) et [importez le pack d’administration SCOM pour le système d’administration de plateforme PDW &#40;Analytics&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="configure-run-as-profile-in-system-center"></a><a name="ConfigureRunAsProfile"></a>Configurer un profil d’identification dans System Center  
Pour configurer System Center, vous devez effectuer les étapes suivantes :  
  
-   Créez un compte d’identification pour l’utilisateur de domaine de l' **Observateur APS** et mappez-le au **compte Microsoft APS Watcher.**  
  
-   Créez un compte d’identification pour l’utilisateur **monitoring_user** APS et mappez-le au **compte d’action Microsoft APS**.  
  
Voici des instructions détaillées sur la façon d’effectuer les tâches :  
  
1.  Créez le compte d’identification de l' **Observateur APS** avec le type de compte **Windows** pour l’utilisateur de domaine de l' **Observateur APS** .  
  
    1.  Accédez au volet **administration** , cliquez avec le bouton droit sur **exécuter en tant que**  ->  **comptes** de configuration, puis sélectionnez créer un compte d’identification **...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  La boîte de dialogue de l' **Assistant Création** d’un compte d’identification s’ouvre. Dans la page **Introduction**, cliquez sur **Suivant**.  
  
    3.  Sur la page **Propriétés générales** , sélectionnez **Windows** à partir du **type de compte** d’identification et spécifiez « observateur APS » comme nom d' **affichage**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  Dans la page **informations d’identification** , ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  Sur la page sécurité de la **distribution** , sélectionnez **moins sécurisé** , puis cliquez sur le bouton **créer** pour terminer.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Si vous décidez d’utiliser l’option la **plus sécurisée** , vous devez spécifier manuellement les ordinateurs sur lesquels les informations d’identification seront distribuées. Pour ce faire, après avoir créé le compte d’identification, cliquez dessus avec le bouton droit et sélectionnez **Propriétés**.  
  
        2.  Accédez à l’onglet **distribution** et **Ajoutez** les ordinateurs souhaités.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Définissez le profil de **compte Microsoft APS Watcher** pour utiliser le compte d’identification d' **Observateur APS** .  
  
    1.  Accédez à **administration**  ->  **exécuter en tant que**  ->  **profils**de configuration.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Cliquez avec le bouton droit sur le **compte Microsoft APS Watcher** dans la liste et sélectionnez **Propriétés**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  La boîte de dialogue de l' **Assistant Profil** d’identification s’ouvre. Ignorez la page **Introduction** en cliquant sur **suivant**.  
  
    4.  Sur la page **Propriétés générales** , cliquez sur **Suivant**.  
  
    5.  Sur la page **comptes** d’identification, cliquez sur le bouton **Ajouter...** , puis sélectionnez le compte d’identification d' **Observateur APS** créé précédemment.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Cliquez sur **Enregistrer** pour terminer l’affectation du profil.  
  
3.  Attendez la fin de la découverte des appliances APS.  
  
    1.  Accédez au volet **analyse** et ouvrez l' **SQL Server Appliance**  ->  **Microsoft Analytics Platform System**  ->  affichage État des**appareils** Microsoft Analytics Platform System de l’appliance SQL Server.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Attendez que l’appliance apparaisse dans la liste. Le nom de l’appliance doit être le même que celui spécifié dans le registre. Une fois la détection terminée, vous devez voir toutes les appliances qui ne sont pas analysées. Pour activer l’analyse, suivez les étapes suivantes.  
  
    > [!NOTE]  
    > Les étapes suivantes peuvent être effectuées en parallèle pendant que vous attendez la fin de la découverte de l’appliance initiale.  
  
4.  Créez un autre compte d’identification pour interroger les points d’accès pour la récupération des données d’intégrité.  
  
    1.  Commencez à créer un nouveau compte d’identification comme décrit à l’étape 1.  
  
    2.  Sur la page **Propriétés générales** , sélectionnez type de compte **authentification de base** .  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  Dans la page **informations d’identification** , fournissez des informations d’identification valides pour accéder aux DMV d’état d’intégrité APS.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Configurez le profil de **compte d’action Microsoft APS** pour utiliser le compte d’identification nouvellement créé pour l’instance APS.  
  
    1.  Accédez aux propriétés du **compte d’action APS Microsoft** , comme décrit à l’étape 2.  
  
    2.  Sur la page **comptes** d’identification, cliquez sur **Ajouter...** et 
    3.  Sélectionnez le compte d’identification que vous venez de créer.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>étape suivante  
Maintenant que vous avez configuré les packs d’administration, vous êtes prêt à démarrer l’analyse de l’appliance. Pour plus d’informations, consultez [surveiller l’appliance à l’aide de System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
