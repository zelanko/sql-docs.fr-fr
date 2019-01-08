---
title: Configurer SCOM pour surveiller Analytique Platform System | Microsoft Docs
description: Suivez ces étapes pour configurer les packs d’administration de System Center Operations Manager (SCOM) pour l’Analytique Platform System. Les packs d’administration sont requises pour analyser le système de plateforme Analytique à partir de SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2dae92263d7be76490a51ea7027f79ab5fcd6118
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52532569"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Configurer System Center Operations Manager (SCOM) pour surveiller le système de plateforme d’Analytique
Suivez ces étapes pour configurer les packs d’administration de System Center Operations Manager (SCOM) pour l’Analytique Platform System. Les packs d’administration sont requises pour analyser le système de plateforme Analytique à partir de SCOM.  
  
## <a name="BeforeBegin"></a>Avant de commencer  
**Conditions préalables**  
  
System Center Operations Manager 2007 R2 doit être installé et en cours d’exécution.  
  
Les packs d’administration doivent être installés et configurés. Consultez [installer les Packs d’administration SCOM &#40;Analytique Platform System&#41; ](install-the-scom-management-packs.md) et [importer le Pack d’administration SCOM pour PDW &#40;Analytique Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Configurer le profil d’identification dans System Center  
Pour configurer System Center, vous devez procédez comme suit :  
  
-   Créer le compte d’identification pour le **APS Watcher** utilisateur de domaine et mappez-le à le **compte de l’Observateur de points d’accès de Microsoft.**  
  
-   Créer le compte d’identification pour le **monitoring_user** utilisateur des points d’accès et mappez-le à le **compte d’Action Microsoft APS**.  
  
Voici des instructions détaillées sur la façon d’effectuer les tâches :  
  
1.  Créer le **APS Watcher** compte d’identification avec **Windows** type de compte le **APS Watcher** utilisateur de domaine.  
  
    1.  Accédez à la **Administration** volet, avec le bouton droit sur **Configuration d’identification** -> **comptes** et sélectionnez **créer un compte d’identification...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  Le **créer Assistant compte d’identification** boîte de dialogue s’ouvre. Sur le **Introduction** , cliquez sur **suivant**.  
  
    3.  Sur le **propriétés générales** page, sélectionnez **Windows** de **type de compte d’identification** et spécifiez « Observateur APS » en tant que le **nom d’affichage**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  Sur le **informations d’identification** page, ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  Sur le **Distribution sécurité** page, sélectionnez **moins sécurisée** et cliquez sur le **créer** bouton pour terminer.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Si vous décidez d’utiliser le **plus sécurisé** option, vous devez spécifier manuellement les ordinateurs vers lesquels les informations d’identification seront distribuées. Pour ce faire, après avoir créé le compte d’identification, avec le bouton droit dessus et sélectionnez **propriétés**.  
  
        2.  Accédez à la **Distribution** onglet et **ajouter** souhaité des ordinateurs.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Définir le **Microsoft APS observateur compte** profil à utiliser **APS Watcher** compte d’identification.  
  
    1.  Accédez à **Administration** -> **exécuter en tant que Configuration** -> **profils**.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Cliquez avec le bouton droit sur **Microsoft APS observateur compte** à partir de la liste et sélectionnez **propriétés**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  Le **Assistant profil d’identification** boîte de dialogue s’ouvre. Ignorer le **Introduction** page en cliquant sur **suivant**.  
  
    4.  Sur le **propriétés générales** , cliquez sur **suivant**.  
  
    5.  Sur le **comptes d’identification** , cliquez sur le **ajouter...**  bouton et sélectionnez l’élément précédemment créé **APS Watcher** compte d’identification.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Cliquez sur **enregistrer** pour terminer l’affectation de profil.  
  
3.  Attendez que la détection des appliances de points d’accès est terminée.  
  
    1.  Accédez à la **surveillance** volet et ouvrez le **SQL Server Appliance** -> **Microsoft Analytique Platform System**  ->   **Appliances** affichage des États.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Attendez que l’appliance apparaît dans la liste. Le nom de l’appliance doit être égal à celle spécifiée dans le Registre. Une fois la détection terminée, vous devriez voir tous les appareils répertoriés mais ne pas analysé. Pour activer la surveillance, suivez les étapes suivantes.  
  
    > [!NOTE]  
    > Les étapes suivantes peuvent être effectuées en parallèle pendant que vous attendez la détection initiale d’appliance terminer.  
  
4.  Créer un autre compte d’identification pour les points d’accès de requête pour récupérer des données d’intégrité.  
  
    1.  Commencer à créer un nouveau compte d’identification, comme décrit à l’étape 1.  
  
    2.  Sur le **propriétés générales** page, sélectionnez **l’authentification de base** type de compte.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  Sur le **informations d’identification** page, fournissez les informations d’identification valides pour accéder à l’état d’intégrité APS DMV.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Configurer le **compte d’Action Microsoft APS** profil à utiliser le compte d’identification nouvellement créé pour l’instance de points d’accès.  
  
    1.  Accédez à la **compte d’Action Microsoft APS** propriétés comme décrit à l’étape 2.  
  
    2.  Sur le **comptes d’identification** , cliquez sur **ajouter...**  et 
    3.  Sélectionnez le compte d’identification nouvellement créé.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Étape suivante  
Maintenant que vous avez configuré les packs d’administration, vous êtes prêt à démarrer la surveillance de l’appliance. Pour plus d’informations, consultez [surveiller l’Appliance à l’aide de System Center Operations Manager &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
