---
title: Configurer l’accès au Générateur de rapports | Microsoft Docs
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.openlocfilehash: 724fac17abf7f5da45101a6ff22d3185a7ade93b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68255170"
---
# <a name="configure-report-builder-access"></a>Configurer l'accès au Générateur de rapports
Le Générateur de rapports est un outil de génération d’états ad hoc qui s’installe avec un serveur de rapports [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuré pour le mode natif ou pour le mode intégré SharePoint.  

L'accès au Générateur de rapports dépend des facteurs suivants :  

- Propriétés de serveur déterminant si le Générateur de rapports est disponible ou non sur le serveur de rapports.  

- Attributions ou autorisations de rôles permettant de rendre le Générateur de rapports disponible pour des utilisateurs individuels ou des groupes.  

- Paramètres d'authentification qui déterminent si les informations d'identification de l'utilisateur peuvent être transmises au serveur de rapports ou si l'accès anonyme est configuré sur les fichiers d'application.

## <a name="prerequisites"></a>Conditions préalables requises

Le Générateur de rapports n’est pas disponible dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  

[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 ou 4.6.1 doit être installé sur l’ordinateur client pour SSRS 2016 et 2017, respectivement. Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit l’infrastructure permettant d’exécuter les applications [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] .  

Vous devez utiliser [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 11 ou version ultérieure, ou un autre navigateur moderne.  

Le Générateur de rapports s'exécute toujours en confiance totale ; vous ne pouvez pas le configurer pour qu'il s'exécute en confiance partielle. Dans les versions antérieures, il était possible d'exécuter le Générateur de rapports en mode de confiance partielle, mais cette option n'est pas prise en charge dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures.  

## <a name="enabling-and-disabling-report-builder"></a>Activation et désactivation du Générateur de rapports  

Le Générateur de rapports est activé par défaut. Les administrateurs du serveur de rapports ont la possibilité de désactiver la fonctionnalité du Générateur de rapports en définissant la propriété système **ShowDownloadMenu** de ce serveur sur la valeur **false**. Les téléchargements du Générateur de rapports, de l’Éditeur de rapports mobiles et de Power BI Mobile effectués pour ce serveur de rapports sont ainsi désactivés.  

 Pour définir les propriétés système du serveur de rapports, vous pouvez utiliser Management Studio ou un script :   

 - Pour utiliser Management Studio, connectez-vous au serveur de rapports et utilisez la page de propriétés avancées du serveur pour affecter **ShowDownloadMenu** à **false**. Pour plus d’informations sur l’ouverture de cette page, consultez [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md).      

 - Pour voir un exemple de script qui définit une propriété du serveur de rapports, consultez [Écrire des scripts pour les tâches d’administration et de déploiement](../../reporting-services/tools/script-deployment-and-administrative-tasks.md).  

## <a name="role-assignments-granting-report-builder-access-on-a-native-mode-report-server"></a>Attributions de rôles qui octroient l'accès au Générateur de rapports sur un serveur de rapports en mode natif  

Sur un serveur de rapports en mode natif, créez des attributions de rôles d'utilisateur qui incluent des tâches pour l'utilisation du Générateur de rapports. Vous devez être Gestionnaire de contenu et Administrateur système pour créer ou modifier des définitions de rôles et des attributions de rôles sur les éléments et au niveau du site.  

Les instructions suivantes supposent que vous utilisez des rôles prédéfinis. Si vous avez modifié les définitions de rôle ou si vous avez effectué une mise à niveau de SQL Server 2000, examinez les rôles pour vérifier s'ils contiennent les tâches nécessaires. Pour plus d’informations sur la création d’attributions de rôles, consultez [Accorder à un utilisateur l'accès à un serveur de rapports](../../reporting-services/security/grant-user-access-to-a-report-server.md).

Une fois les attributions de rôles créées, les utilisateurs seront autorisés à effectuer les opérations suivantes :  

- Les utilisateurs affectés aux rôles Utilisateur système et Visiteur peuvent afficher des rapports publiés du Générateur de rapports sur un serveur de rapports, sans qu'il soit nécessaire de lancer le Générateur de rapports.  

- Les utilisateurs affectés aux rôles Utilisateur système et Générateur de rapports peuvent générer des modèles, démarrer le Générateur de rapports et créer des rapports, ainsi qu'enregistrer des rapports sur le serveur de rapports.  

- Les utilisateurs attribués aux rôles Utilisateur système et Serveur de publication peuvent publier des modèles du Générateur de modèles sur le serveur de rapports. Les modèles sont utilisés comme des sources de données dans le Générateur de rapports.  

- Les utilisateurs attribués aux rôles Administrateur système et Gestionnaire de contenu disposent de toutes les autorisations nécessaires pour créer, afficher et gérer les rapports du Générateur de rapports.  

### <a name="to-verify-required-tasks-are-in-the-role-definitions"></a>Pour vérifier que des tâches requises se trouvent dans les définitions de rôles  

1. Démarrez Management Studio et connectez-vous au serveur de rapports.  

2. Ouvrez le dossier **Sécurité** .  

3. Ouvrez le dossier **Rôles système** .  

4. Cliquez avec le bouton droit sur **Administrateur système**, puis sélectionnez **Propriétés**.  

5. Sélectionnez **Exécuter les définitions de rapport** , puis cliquez sur **OK**.  

6. Cliquez avec le bouton droit sur **Utilisateur système**, puis sélectionnez **Propriétés**.  

7. Sélectionnez **Exécuter les définitions de rapport** , puis cliquez sur **OK**.  

8. Ouvrez le dossier **Rôles** .  

9. Cliquez avec le bouton droit sur **Navigateur**, puis sélectionnez **Propriétés**.  

10. Sélectionnez **Afficher les modèles** , puis cliquez sur **OK**.  

11. Cliquez avec le bouton droit sur **Gestionnaire de contenu**, puis sélectionnez **Propriétés**.  

12. Sélectionnez **Afficher les modèles**, **Gérer les modèles**, **Lire les rapports**, puis cliquez sur **OK**.  

13. Cliquez avec le bouton droit sur **Serveur de publication**, puis sélectionnez **Propriétés**.  

14. Sélectionnez **Gérer les modèles** , puis cliquez sur **OK**.  

15. Créez le rôle Générateur de rapports s’il n'existe pas :  

    1. Ouvrez le dossier **Sécurité** .  

    2. Cliquez avec le bouton droit sur le dossier **Rôles**, puis sélectionnez **Nouveau rôle**.  

    3. Dans Nom, tapez **Générateur de rapports**.  

    4. Dans Description, entrez une description du rôle afin que les utilisateurs du portail web connaissent la fonction du rôle.  

    5. Ajoutez les tâches suivantes : **Lire les rapports**, **Afficher les rapports**, **Afficher les modèles**, **Afficher les ressources**, **Afficher les dossiers**et **Gérer les abonnements individuels**.  

    6. Cliquez sur **OK** pour enregistrer le rôle.  

#### <a name="to-create-role-assignments-that-grant-access-to-report-builder"></a>Pour créer des attributions de rôles qui octroient l'accès au Générateur de rapports  

1. Démarrer le portail web.  

2. Cliquez sur l’icône en forme d’engrenage en haut à droite de la page d’accueil du portail web, puis sélectionnez **Paramètres du site** dans le menu déroulant.  
![menu et icône en forme d’engrenage du portail web](../../reporting-services/report-builder/media/configure-report-builder-access/ssrswebportal-site-settings-gear-icon-and-menu.png)

3. Cliquez sur **Sécurité**.  

4. Si une attribution de rôle existe déjà pour l’utilisateur ou le groupe pour lequel vous voulez configurer l’accès au Générateur de rapports, cliquez sur **Modifier**.  
Sinon, cliquez sur **Nouvelle attribution de rôle**. Dans Groupe ou utilisateur, entrez un compte d’utilisateur ou de groupe d’un domaine Windows au format suivant : \<domaine>\\<compte\>. Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.  

5. Sélectionnez **Utilisateur système**, puis cliquez sur **OK**.  

6. Cliquez sur **Accueil**.  

7. Cliquez sur l’onglet **Paramètres du dossier** .  

8. Cliquez sur l’onglet **Security** .  

9. Si une attribution de rôle existe déjà pour l’utilisateur ou le groupe pour lequel vous voulez configurer l’accès au Générateur de rapports, cliquez sur **Modifier**.  

    Sinon, cliquez sur **Nouvelle attribution de rôle**. Dans Groupe ou utilisateur, entrez un compte d’utilisateur ou de groupe d’un domaine Windows au format suivant : \<domaine>\\<compte\>. Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.  

10. Sélectionnez **Générateur de rapports**, puis cliquez sur **Appliquer**.  

11. Répétez ces étapes pour créer ou modifier des attributions de rôles pour des utilisateurs ou des groupes supplémentaires.  

## <a name="permissions-granting-report-builder-access-on-a-sharepoint-integrated-mode-report-server"></a>Autorisations octroyant l’accès au Générateur de rapports sur un serveur de rapports en mode intégré SharePoint  

Sur un serveur de rapports en mode intégré SharePoint, l'accès au Générateur de rapports est octroyé aux utilisateurs SharePoint qui disposent de niveaux d'autorisation Collaboration ou Contrôle total.  

Si vous utilisez des niveaux d'autorisation personnalisés, vous devez inclure Ajouter les éléments et Modifier les éléments dans le niveau d'autorisation. Pour plus d’informations sur l’accès au Générateur de rapports par l’intermédiaire de niveaux d’autorisation prédéfinis, consultez [Utiliser la sécurité intégrée dans Windows SharePoint Services pour les éléments de serveur de rapports](../../reporting-services/security/use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md). Pour plus d’informations sur les conditions requises pour les niveaux d’autorisation personnalisés, consultez [Définir des autorisations pour les opérations de serveur de rapports dans une application web SharePoint](../../reporting-services/security/set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md).  

## <a name="authentication-considerations-and-credential-reuse"></a>Considérations relatives à l’authentification et réutilisation des informations d’identification  

- Le Générateur de rapports ouvre sa propre connexion à un serveur de rapports. Si vous n'utilisez pas la sécurité intégrée de Windows avec une authentification unique, les utilisateurs doivent retaper leurs informations d'identification pour la connexion du Générateur de rapports au serveur de rapports.  

Le tableau suivant décrit les types d'authentifications pris en charge par le serveur de rapports, et indique si une configuration supplémentaire est requise pour accéder au Générateur de rapports.  

## <a name="see-also"></a>Voir aussi  

- [Authentification avec le serveur de rapports](../../reporting-services/security/authentication-with-the-report-server.md)
- [Prise en charge des navigateurs pour Reporting Services et Power View](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)
- [Démarrer le Générateur de rapports](../../reporting-services/report-builder/start-report-builder.md)
- [Le portail web d’un serveur de rapports (Mode natif SSRS)](../web-portal-ssrs-native-mode.md)
- [Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)
- [Propriétés système du serveur de rapports](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)
