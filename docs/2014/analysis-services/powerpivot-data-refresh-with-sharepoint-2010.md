---
title: Actualisation des données PowerPivot avec SharePoint 2010 | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 01b54e6f-66e5-485c-acaa-3f9aa53119c9
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2809ee4ed18ce4f1735bbdc2b99ae5490c7e4046
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051613"
---
# <a name="powerpivot-data-refresh-with-sharepoint-2010"></a>Actualisation des données PowerPivot avec SharePoint 2010
  L'actualisation des données [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] est une opération côté serveur planifiée qui interroge des sources de données externes pour mettre à jour les données incorporées [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] dans un classeur Excel 2010 stocké dans la bibliothèque de contenus.  
  
 L'actualisation des données est une fonctionnalité intégrée de [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint, mais pour l'utiliser, vous devez exécuter des services spécifiques et des travaux de minuteur dans votre batterie SharePoint 2010. Des étapes administratives supplémentaires, comme installer des fournisseurs de données et vérifier les autorisations des bases de données, sont souvent requises pour que l'actualisation des données réussisse.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et SharePoint Server 2013 Excel Services utilisent une architecture différente pour l’actualisation des données de [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] des modèles de données. La nouvelle architecture utilise Excel Services en tant que composant principal pour charger les modèles de données PowerPivot. L'architecture d'actualisation des données précédente reposait sur un serveur exécutant le service système PowerPivot et [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en mode SharePoint afin de charger les modèles de données. Pour plus d’informations, consultez [d’actualisation des données PowerPivot avec SharePoint 2013](power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md).  
  
 **Dans cette rubrique :**  
  
 [Étape 1 : Activer le Service de banque d’informations sécurisé et générer une clé principale](#bkmk_services)  
  
 [Étape 2 : Désactiver les options d’informations d’identification que vous ne souhaitez pas prendre en charge](#bkmk_creds)  
  
 [Étape 3 : Créer des applications cibles pour stocker les informations d’identification utilisées dans l’actualisation des données](#bkmk_stored)  
  
 [Étape 4 : Configurer le serveur pour l’actualisation des données évolutive](#bkmk_scale)  
  
 [Étape 5 : Installer les fournisseurs de données utilisés pour importer des données PowerPivot](#bkmk_installdp)  
  
 [Étape 6 : Octroyer des autorisations pour créer des planifications et accéder aux sources de données externes](#bkmk_accounts)  
  
 [Étape 7 : Activer la mise à niveau du classeur pour l’actualisation des données](#bkmk_upgradewrkbk)  
  
 [Étape 8 : Vérifier la configuration de l’actualisation de données](#bkmk_verify)  
  
 [Modifier les paramètres de Configuration pour l’actualisation des données](#bkmk_config)  
  
 [Replanifier le travail du minuteur d’actualisation des données PowerPivot](#configTimerJob)  
  
 [Désactiver le travail du minuteur d’actualisation des données](#bkmk_disableDR)  
  
 Une fois l'environnement de serveur et les autorisations configurés, vous pouvez utiliser l'actualisation des données. Pour utiliser l'actualisation des données, un utilisateur SharePoint crée une planification sur un classeur PowerPivot qui spécifie quand et à quelle fréquence elle se produira. C'est généralement le propriétaire du classeur qui crée la planification, ou bien l'auteur qui a publié le fichier sur SharePoint. Cette personne crée et gère les planifications d'actualisation des données pour les classeurs dont elle est propriétaire. Pour plus d’informations, consultez [planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
##  <a name="bkmk_services"></a> Étape 1 : Activer le Service de banque d’informations sécurisé et générer une clé principale  
 L'actualisation des données PowerPivot dépend du Service Banque d'informations sécurisé pour fournir les informations d'identification utilisées pour exécuter des travaux d'actualisation des données et se connecter aux sources de données externes qui utilisent les informations d'identification stockées.  
  
 Si vous avez installé PowerPivot pour SharePoint à l'aide de l'option Nouveau serveur, le Service Banque d'informations sécurisé est automatiquement configuré. Pour tous les autres scénarios d'installation, vous devez créer et configurer une application de service et générer une clé de chiffrement principale pour le Service Banque d'informations sécurisé.  
  
> [!NOTE]  
>  Vous devez être administrateur de batterie de serveurs pour configurer le service Banque d'informations sécurisé ou pour déléguer l'administration du service Banque d'informations sécurisé à un autre utilisateur. Vous devez être administrateur d'application de service pour configurer ou modifier des paramètres après leur activation.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Dans le ruban Applications de Service, de créer, cliquez sur **nouveau**.  
  
3.  Sélectionnez **Service de magasin sécurisé**.  
  
4.  Dans le **créer l’Application du magasin sécurisé** , entrez un nom pour l’application.  
  
5.  Dans **base de données**, spécifiez l’instance de SQL Server qui hébergera la base de données pour cette application de service. La valeur par défaut est l'instance du moteur de base de données SQL Server qui héberge les bases de données de configuration de la batterie de serveurs.  
  
6.  Dans **nom de la base de données**, entrez le nom de la base de données. La valeur par défaut est Secure_Store_Service_DB_\<guid >. Le nom par défaut correspond au nom par défaut de l'application de service. Si vous avez entré un nom d'application de service unique, suivez une convention d'affectation des noms similaire pour la base de données afin de pouvoir les gérer ensemble.  
  
7.  Dans **Authentification de la base de données**, la valeur par défaut est Authentification Windows. Si vous choisissez Authentification SQL, reportez-vous au guide de l'administrateur SharePoint pour des recommandations concernant l'utilisation de ce type d'authentification dans votre batterie de serveurs.  
  
8.  Dans le Pool d’applications, sélectionnez **créer le nouveau pool d’applications.** Spécifiez un nom descriptif qui permettra aux autres administrateurs de serveurs d'identifier la manière dont le pool d'applications est utilisé.  
  
9. Sélectionnez un compte de sécurité pour le pool d'applications. Spécifiez un compte géré pour utiliser un compte d'utilisateur de domaine.  
  
10. Acceptez les valeurs par défaut restantes, puis cliquez sur **OK.** . L'application de service apparaît avec les autres services gérés dans la liste des applications de service de la batterie de serveurs.  
  
11. Cliquez sur l'application de service Banque d'informations sécurisé dans la liste.  
  
12. Dans le ruban Applications de Service, cliquez sur **gérer**.  
  
13. Dans la gestion de clés, cliquez sur **générer une nouvelle clé**.  
  
14. Entrez une phrase secrète et confirmez-la. Elle sera utilisée pour ajouter d'autres applications de service Banque d'informations sécurisé partagé.  
  
15. Cliquez sur **OK**.  
  
 L'enregistrement de l'audit des opérations du Service Banque d'informations, utile à des fins de résolution des problèmes, doit être activé avant de pouvoir être utilisé. Pour plus d’informations sur la façon d’activer la journalisation, consultez [configurer Service de magasin sécurisé (SharePoint 2010)](http://go.microsoft.com/fwlink/p/?LinkID=223294).  
  
##  <a name="bkmk_creds"></a> Étape 2 : Désactiver les options d’informations d’identification que vous ne souhaitez pas prendre en charge  
 L'actualisation des données PowerPivot fournit trois options d'informations d'identification dans une planification d'actualisation des données. Lorsqu'un propriétaire de classeur planifie l'actualisation des données, il choisit l'une de ces options, en déterminant le compte sous lequel le travail d'actualisation des données s'exécute. En tant qu'administrateur, vous pouvez déterminer quelles options d'informations d'identification sont disponibles pour les propriétaires de planification.  
  
 Vous devez avoir au moins une option disponible pour que l'actualisation des données fonctionne.  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 Option 1, **utilisation de l’actualisation des données configuré par l’administrateur de compte**, apparaît toujours sur la page de définition de planification, mais ne fonctionne que si vous configurez le compte d’actualisation des données sans assistance. Pour plus d’informations sur la façon de créer le compte, consultez [configurer le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
 Option 2, **se connecter en utilisant les informations d’identification windows suivant**, apparaît toujours sur la page, mais ne fonctionne que lorsque vous activez le **autoriser les utilisateurs à entrer des informations d’identification Windows personnalisées** option dans le service page de configuration d’application. Cette option est activée par défaut, mais vous pouvez la désactiver si les inconvénients liés à son utilisation l'emportent sur les avantages (voir ci-dessous).  
  
 Option 3, **se connecter en utilisant les informations d’identification enregistrées dans le Service de magasin sécurisé**, apparaît toujours sur la page, mais ne fonctionne que quand un propriétaire de planification fournit une application cible valide. Un administrateur doit créer ces applications cibles à l'avance, puis fournir le nom de l'application à ceux qui créent les planifications d'actualisation des données. Pour plus d’informations sur la création d’une application cible pour les données des opérations d’actualisation, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
 **Configuration de l’option informations d’identification 2, « Se connecter à l’aide des informations d’identification utilisateur Windows suivantes »**  
  
 Une application de service PowerPivot inclut une option d'informations d'identification qui permet aux propriétaires de planification d'entrer un nom d'utilisateur Windows arbitraire et un mot de passe pour l'exécution d'un travail d'actualisation des données. Il s'agit de la deuxième option d'informations d'identification dans la page de définition de la planification :  
  
 ![SSAS_PPS_ScheduleDataRefreshCreds](media/ssas-pps-scheduledatarefreshcreds.gif "SSAS_PPS_ScheduleDataRefreshCreds")  
  
 Cette option d'identification est activée par défaut. Lorsque cette option d'informations d'identification est activée, le service système PowerPivot génère une application cible dans le Service Banque d'informations sécurisé pour stocker le nom d'utilisateur et le mot de passe entrés par le propriétaire de la planification. Une application cible générée est créée à l’aide de cette convention d’affectation de noms : PowerPivotDataRefresh_\<guid >. Une application de cible est créée pour chaque ensemble d'informations d'identification Windows. Si une application cible existe déjà, détenue par le service système PowerPivot, et stocke le nom d'utilisateur et le mot de passe entrés par la personne qui définit la planification, le service système PowerPivot utilisera cette application cible au lieu d'en créer une.  
  
 Le principal avantage de l'utilisation de cette option d'informations d'identification est la facilité d'utilisation et la simplicité. Le travail préalable est minime, car les applications cibles sont créées pour vous. En outre, l'exécution de l'actualisation des données sous les informations d'identification du propriétaire de la planification (qui est très probablement la personne qui a créé le classeur) simplifie les autorisations requises en aval. Très probablement, cet utilisateur dispose déjà des autorisations nécessaires sur la base de données cible. Lorsque l'actualisation des données s'exécute sous l'identité d'utilisateur Windows de cette personne, toutes les connexions de données qui spécifient l'« utilisateur actuel » fonctionnent automatiquement.  
  
 L'inconvénient est la fonction de gestion limitée. Bien que les applications cibles soient créées automatiquement, elles ne sont pas supprimées ou mises à jour automatiquement à mesure que les informations sur le compte changent. Avec les stratégies d'expiration des mots de passe, ces applications cibles risquent de devenir obsolètes. Les travaux d'actualisation des données qui utilisent des informations d'identification arrivées à expiration commenceront à échouer. Lorsque cela se produit, les propriétaires de planification doivent mettre à jour leurs informations d'identification en fournissant des valeurs de nom d'utilisateur et de mot de passe actuelles dans une planification d'actualisation des données. Une nouvelle application cible sera créée à ce stade. Avec le temps, comme les utilisateurs ajoutent et modifient les informations d'identification dans leurs planifications d'actualisation des données, vous pouvez constater que vous avez un grand nombre d'applications cibles générées automatiquement sur votre système.  
  
 Actuellement, il n'existe aucune méthode pour déterminer lesquelles de ces applications cibles sont actives ou inactives, ni pour suivre une application cible spécifique jusqu'aux planifications d'actualisation des données qui l'utilisent. En général, vous devez vous abstenir de toucher aux applications cibles, car leur suppression peut entraver des planifications d'actualisation des données existantes. La suppression d'une application cible qui est encore en cours d'utilisation provoquera un échec de l'actualisation des données avec le message suivant : « Application cible introuvable », qui s'affiche dans la page d'historique d'actualisation des données du classeur.  
  
 Si vous devez choisir de désactiver cette option d'informations d'identification, vous pouvez supprimer sans risque toutes les applications cibles générées pour l'actualisation des données PowerPivot.  
  
 **La désactivation de l’utilisation des informations d’identification Windows arbitraires dans les planifications d’actualisation des données**  
  
1.  Dans Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de l'application de service PowerPivot. Le Tableau de bord de gestion PowerPivot apparaît.  
  
3.  Dans Actions, cliquez sur **configurer les paramètres d’application de service** pour ouvrir la page Paramètres d’Application de Service de PowerPivot  
  
4.  Dans la section actualisation des données, désactivez le **autoriser les utilisateurs à entrer des informations d’identification Windows personnalisées** case à cocher.  
  
     ![SSAS_PowerPivotDatarefreshOptions_AllowUser](media/ssas-powerpivotdatarefreshoptions-allowuser.gif "SSAS_PowerPivotDatarefreshOptions_AllowUser")  
  
##  <a name="bkmk_stored"></a> Étape 3 : Créer des applications cibles pour stocker les informations d’identification utilisées dans l’actualisation des données  
 Une fois le service Banque d'informations sécurisé configuré, les administrateurs SharePoint peuvent créer des applications cibles pour rendre les informations d'identification stockées disponibles à des fins d'actualisation des données, notamment le compte d'actualisation des données PowerPivot sans assistance ou tout autre compte utilisé pour exécuter le travail ou se connecter aux sources de données externes.  
  
 Nous avons vu dans la section précédente que vous devez créer des applications cibles de façon à pouvoir utiliser certaines options d'informations d'identification. Spécifiquement, vous devez créer des applications cibles pour le compte d'actualisation des données PowerPivot sans assistance, plus toutes les informations d'identification stockées supplémentaires dont vous pensez qu'elles seront utilisées dans les opérations d'actualisation des données.  
  
 Pour plus d’informations sur la création d’applications cibles qui contiennent des informations d’identification stockées, consultez [configurer le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41; ](configure-unattended-data-refresh-account-powerpivot-sharepoint.md) et [ Configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="bkmk_scale"></a> Étape 4 : Configurer le serveur pour l’actualisation des données évolutive  
 Par défaut, chaque installation PowerPivot pour SharePoint prend en charge à la fois des requêtes à la demande et l'actualisation des données planifiée.  
  
 Pour chaque installation, vous pouvez spécifier si l'instance de serveur Analysis Services prend en charge les requêtes et l'actualisation des données planifiée, ou est dédiée à un type d'opération spécifique. Si vous avez plusieurs installations de PowerPivot pour SharePoint dans votre batterie, vous pouvez envisager de consacrer un serveur uniquement aux opérations d'actualisation des données si vous constatez que les travaux sont différés ou échouent.  
  
 En outre, si le matériel sous-jacent prend en charge cette opération, vous pouvez augmenter le nombre de travaux d'actualisation des données qui s'exécutent en parallèle. Par défaut, le nombre de travaux qui peuvent s'exécuter en parallèle est calculé selon la mémoire système, mais vous pouvez augmenter ce nombre si vous disposez d'une capacité d'UC supplémentaire pour prendre en charge la charge de travail.  
  
 Pour plus d’informations, consultez [configurer l’actualisation des données dédié ou du traitement de Query-Only &#40;PowerPivot pour SharePoint&#41;](configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md).  
  
##  <a name="bkmk_installdp"></a> Étape 5 : Installer les fournisseurs de données utilisés pour importer des données PowerPivot  
 Une opération d'actualisation des données est essentiellement une répétition d'une opération d'importation ayant récupéré les données d'origine. Cela signifie que les mêmes fournisseurs de données utilisés pour importer les données dans l'application cliente PowerPivot doivent également être installés sur le serveur PowerPivot.  
  
 Vous devez être un administrateur local pour installer des fournisseurs de données sur un serveur Windows. Si vous installez des pilotes supplémentaires, veillez à les installer sur chaque ordinateur dans la batterie de serveurs SharePoint qui possède une installation de PowerPivot pour SharePoint. Si vous avez plusieurs serveurs PowerPivot dans la batterie, vous devez installer les fournisseurs sur chacun.  
  
 n'oubliez pas que les serveurs SharePoint sont des applications 64 bits. Assurez-vous d'avoir installé la version 64 bits des fournisseurs de données que vous utilisez pour prendre en charge les opérations d'actualisation des données.  
  
##  <a name="bkmk_accounts"></a> Étape 6 : Octroyer des autorisations pour créer des planifications et accéder aux sources de données externes  
 Les propriétaires ou auteurs de classeurs doivent avoir l'autorisation **Collaboration** pour planifier des actualisation de données sur un classeur. Avec ce niveau d'autorisation, l'utilisateur peut ouvrir et modifier la page de configuration de l'actualisation des données pour spécifier les informations d'identification et de planification utilisées pour actualiser les données.  
  
 En plus des autorisations SharePoint, les autorisations relatives à la base de données sur les sources de données externes doivent également être examinées pour vérifier que les comptes utilisés pendant l'actualisation des données ont des droits d'accès suffisants aux données. La détermination des autorisations requises nécessite une évaluation prudente de votre part, car les autorisations que vous devez accorder varieront selon la chaîne de connexion dans le classeur et l'identité de l'utilisateur sous laquelle le travail d'actualisation des données s'exécute.  
  
 **Pourquoi les chaînes de connexion existantes dans un classeur PowerPivot a d’importance pour les opérations d’actualisation des données PowerPivot**  
  
 Lorsque l'actualisation des données s'exécute, le serveur envoie une demande de connexion à la source de données externe à l'aide de la chaîne de connexion créée lors de l'importation d'origine des données. L'emplacement du serveur, le nom de la base de données et les paramètres d'authentification spécifiés dans cette chaîne de connexion sont maintenant réutilisés pendant l'actualisation des données de façon à accéder aux mêmes sources de données. La chaîne de connexion et sa construction globale ne peuvent pas être modifiées à des fins d'actualisation des données. Elle est simplement réutilisée tel quel pendant l'actualisation des données. Dans certains cas, si vous utilisez une authentification autre que l'authentification Windows pour vous connecter à une source de données, vous pouvez remplacer le nom d'utilisateur et le mot de passe dans la chaîne de connexion. Vous trouverez plus d'informations à ce sujet plus loin dans cette rubrique.  
  
 Pour la plupart des classeurs, l'option d'authentification par défaut sur la connexion consiste à utiliser des connexions approuvées ou la sécurité intégrée de Windows, provoquant des chaînes de connexion qui incluent `SSPI=IntegratedSecurity` ou `SSPI=TrustedConnection`. Lorsque cette chaîne de connexion est utilisée pendant l'actualisation des données, le compte utilisé pour exécuter le travail d'actualisation des données devient l'« utilisateur actuel ». En tant que tel, ce compte a besoin d'autorisations de lecture sur toute source de données externe à laquelle il a accès via une connexion approuvée.  
  
 **Avez-vous activé le PowerPivot compte d’actualisation des données sans assistance ?**  
  
 Dans l'affirmative, vous devez accorder à ce compte des autorisations de lecture sur les sources de données auxquelles il accède pendant l'actualisation des données. En effet, dans un classeur qui utilise les options d'authentification par défaut, le compte sans assistance est l'« utilisateur actuel » pendant l'actualisation des données. À moins que le propriétaire de planification remplace les informations d'identification dans la chaîne de connexion, ce compte aura besoin d'autorisations de lecture sur un nombre illimité de sources de données utilisées activement dans votre organisation.  
  
 **Vous êtes à l’aide des informations d’identification, option 2 : autoriser le propriétaire de la planification d’entrer un nom d’utilisateur Windows et un mot de passe ?**  
  
 En général, les utilisateurs qui créent des classeurs PowerPivot disposent déjà des autorisations suffisantes, car ils ont déjà importé les données en premier lieu. Si ces utilisateurs configurent par la suite l'actualisation des données de façon à ce qu'elle s'exécute sous leur propre identité d'utilisateur Windows, leur compte d'utilisateur Windows, qui a déjà des droits sur la base de données, sera utilisé pour extraire les données pendant l'actualisation des données. Les autorisations existantes doivent être suffisantes.  
  
 **Vous êtes à l’aide de l’option informations d’identification 3 : à l’aide d’une application de cible Service Banque d’informations sécurisé pour fournir une identité d’utilisateur pour l’exécution de travaux d’actualisation des données ?**  
  
 Tout compte utilisé pour exécuter un travail d'actualisation des données a besoin d'autorisations d'accès en lecture, pour les mêmes raisons que celles décrites pour le compte d'actualisation des données PowerPivot sans assistance.  
  
 **Comment vérifier les chaînes de connexion pour déterminer si vous pouvez remplacer les informations d’identification utilisées pendant l’actualisation des données**  
  
 Comme indiqué précédemment, vous pouvez remplacer un nom d'utilisateur et mot de passe au niveau du travail d'actualisation des données si la connexion utilise une authentification autre que l'authentification Windows (par exemple, l'authentification SQL Server). Les informations d'identification non-Windows sont passées à la chaîne de connexion à l'aide des paramètres ID d'utilisateur et Mot de passe. Si votre classeur contient une chaîne de connexion avec ces paramètres, vous pouvez spécifier éventuellement un autre nom d'utilisateur et un mot de passe pour l'actualisation des données de cette source de données.  
  
 Les étapes suivantes expliquent comment déterminer si vous avez une chaîne de connexion qui accepte les substitutions de nom d'utilisateur et de mot de passe.  
  
1.  Ouvrez le classeur dans Excel.  
  
2.  Ouvrez fenêtre PowerPivot (dans Excel, sur le ruban PowerPivot, cliquez sur Fenêtre PowerPivot).  
  
3.  Cliquez sur **conception**.  
  
4.  Cliquez sur **connexions existantes**.  
  
     Toutes les connexions utilisées dans le classeur sont répertoriés sous **des connexions de données PowerPivot**.  
  
5.  Sélectionnez la connexion et cliquez sur **modifier**, puis cliquez sur **avancé**. La chaîne de connexion est en bas de la page.  
  
 Si vous voyez **Integrated Security = SSPI** dans la chaîne de connexion, vous ne pouvez pas remplacer les informations d’identification dans la chaîne de connexion. La connexion utilisera toujours l'utilisateur actuel. Toutes les informations d'identification que vous spécifiées sont ignorées.  
  
 Si vous voyez **Persist Security Info = False, Password =\* \* \* \* \* \* \* \* \* \* \*, UserID =\<userlogin >**, puis vous avez une chaîne de connexion qui accepte les substitutions d’informations d’identification. Les informations d'identification qui s'affichent dans une chaîne de connexion (comme UserID et Password) ne sont pas des informations d'identification Windows, mais plutôt des connexions à une base de données ou d'autres comptes d'ouverture de session qui sont valides pour la source de données cible.  
  
 **Procédure de remplacement des informations d’identification dans la chaîne de connexion**  
  
 Le remplacement des informations d'identification s'effectue en spécifiant les informations d'identification de la source de données dans la planification d'actualisation des données. En tant qu'administrateur, vous pouvez spécifier une application cible dans le Service Banque d'informations sécurisé qui mappe les informations d'identification utilisées pour accéder aux données externes. Le propriétaire de la planification peut ensuite entrer l'ID de l'application cible dans la planification d'actualisation des données qu'il définit. Pour plus d’informations sur la création de cette application cible, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
 Le propriétaire de la planification peut également taper l'ensemble des informations d'identification utilisées pour se connecter aux sources de données pendant l'actualisation des données. L'illustration ci-dessous montre cette option de source de données dans la page de définition de la planification.  
  
 ![SSAS_PowerPivotKJ_DataRefreshDSOptions](media/ssas-powerpivotkj-datarefreshdsoptions.gif "SSAS_PowerPivotKJ_DataRefreshDSOptions")  
  
 **Accès aux données identification**  
  
 Comme mentionné dans les sections précédentes, le compte utilisé pour exécuter l'actualisation des données et se connecte aux sources de données externes est souvent le même. De ce fait, le compte utilisé pour accéder aux sources de données externes est déterminé par les options définies dans cette partie de la page de planification de l'actualisation des données. Ce peut être le compte d'actualisation des données PowerPivot sans assistance, le compte Windows d'un utilisateur individuel, ou le compte stocké dans une application cible prédéfinie.  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 Dans les cas où le compte utilisé pour exécuter l'actualisation des données est différent du compte utilisé pour importer les données (par exemple, le compte d'actualisation des données PowerPivot sans assistance via l'option d'informations d'identification 1, ou un autre ensemble d'informations d'identification stockées via l'option 3), vous devrez créer une connexion à une base de données pour ce compte et lui accorder des autorisations de lecture sur les sources de données externes.  
  
 Après avoir compris quels comptes requièrent l'accès aux données, vous pouvez commencer à vérifier les autorisations sur les sources de données utilisées le plus souvent dans les classeurs PowerPivot. Démarrez avec des entrepôts de données ou des bases de données de création de rapports utilisés activement, mais sollicitez également l'entrée de vos utilisateurs PowerPivot les plus actifs pour déterminer quelles sources de données ils utilisent. Une fois que vous avez une liste de sources de données, vous pouvez commencer à vérifier chacune d'entre elles de façon à vous assurer que les autorisations sont définies correctement.  
  
##  <a name="bkmk_upgradewrkbk"></a> Étape 7 : Activer la mise à niveau du classeur pour l’actualisation des données  
 Par défaut, les classeurs créés à l'aide de la version [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] de PowerPivot pour Excel ne peuvent pas être configurés pour l'actualisation des données planifiée sur une version [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] de PowerPivot pour SharePoint. Si vous hébergez des versions anciennes et récentes des classeurs PowerPivot dans votre environnement SharePoint, vous devez d'abord mettre à niveau tous les classeurs [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] avant qu'ils ne puissent être planifiés pour une actualisation automatique des données sur le serveur.  
  
##  <a name="bkmk_verify"></a> Étape 8 : Vérifier la configuration de l’actualisation de données  
 Pour vérifier l'actualisation des données, vous devez avoir un classeur PowerPivot publié sur un site SharePoint. Vous devez avoir des autorisations Collaboration sur le classeur et des autorisations d'accès à toutes les sources de données incluses dans la planification de l'actualisation des données.  
  
 Lorsque vous créez la planification, sélectionnez le **aussi actualiser dès que possible** case à cocher pour exécuter l’actualisation des données immédiatement. Vous pouvez ensuite examiner la page d'historique d'actualisation des données de ce classeur pour vérifier qu'elle s'est exécutée avec succès. N'oubliez pas que le travail du minuteur d'actualisation des données PowerPivot s'exécute toutes les minutes. Il faut autant de temps pour d'obtenir la confirmation de réussite de l'actualisation des données.  
  
 Veillez à essayer toutes les options d'informations d'identification que vous projetez de prendre en charge. Par exemple, si vous avez configuré le compte d'actualisation des données PowerPivot sans assistance, vérifiez que l'actualisation des données réussit à l'aide de cette option. Pour plus d’informations sur la planification et l’affichage des informations d’état, consultez [planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41; ](schedule-a-data-refresh-powerpivot-for-sharepoint.md) et [l’historique d’actualisation des données d’affichage &#40;PowerPivot pour SharePoint &#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).  
  
 Si l’actualisation des données échoue, reportez-vous à la [résolution des problèmes d’actualisation des données PowerPivot](http://go.microsoft.com/fwlink/?LinkID=223279) page sur le wiki TechNet pour les solutions possibles.  
  
##  <a name="bkmk_config"></a> Modifier les paramètres de Configuration pour l’actualisation des données  
 Chaque application de service PowerPivot possède des paramètres de configuration qui affectent les opérations d'actualisation des données. Cette section explique comment modifier ces paramètres.  
  
###  <a name="procIntervals"></a> Définissez « heures d’ouverture » pour déterminer les heures creuses du traitement  
 Les utilisateurs SharePoint qui planifient des opérations d'actualisation des données peuvent spécifier une heure de début au plus tôt « Après les heures d'ouverture ». Ils ont ainsi la possibilité de récupérer les données de transaction qui se sont accumulées pendant la journée de travail. En tant qu'administrateur de batterie de serveurs, vous pouvez spécifier la plage horaire qui définit au mieux la journée de travail dans votre organisation. Si vous définissez cette journée de sorte qu'elle s'étende de 04:00 à 20:00, le traitement de l'actualisation des données basé sur l'heure de début « Après les heures d'ouverture » commence à 20:01.  
  
 Les requêtes d'actualisation des données qui s'exécutent en dehors des heures d'ouverture sont ajoutées à la file d'attente dans leur ordre de réception. Les requêtes individuelles sont traitées à mesure que des ressources du serveur se libèrent.  
  
1.  Dans Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de l'application de service PowerPivot. Le Tableau de bord de gestion PowerPivot apparaît.  
  
3.  Dans Actions, cliquez sur **configurer les paramètres d’application de service** pour ouvrir la page Paramètres d’Application de Service de PowerPivot  
  
4.  Dans la section Actualisation des données, dans Heures d'ouverture, entrez une heure de début et une heure de fin indiquant la période de traitement après les heures d'ouverture.  
  
     Si vous ne souhaitez pas définir de période de traitement en dehors des heures d'ouverture, vous pouvez entrer la même valeur à la fois pour Heure de début et pour Heure de fin (par exemple, 12:00 pour les deux). Sachez toutefois que les pages de définition de la planification sur les sites SharePoint proposeront tout de même une option « Après les heures d'ouverture ». Des utilisateurs qui sélectionnent cette option sur une batterie de serveurs pour laquelle aucune plage de traitement en dehors des heures d'ouverture n'est définie peuvent alors recevoir des erreurs d'actualisation des données en rapport avec l'échec du démarrage de tel ou tel travail de traitement.  
  
5.  Cliquez sur **OK**.  
  
###  <a name="usagehist"></a> Limiter la durée de conservation de l’historique d’actualisation des données  
 L'historique d'actualisation des données est un enregistrement détaillé des messages d'échec et de réussite générés au fil du temps pour les opérations d'actualisation des données. Les informations d'historique sont collectées et gérées via le système de collecte des données d'utilisation de la batterie de serveurs. En tant que telles, les limites que vous définissez pour l'historique des données d'utilisation s'appliquent également à l'historique d'actualisation des données. Dans la mesure où les rapports sur l'utilisation rassemblent des données provenant de l'ensemble du système PowerPivot, un même paramètre d'historique permet de contrôler la rétention des données aussi bien pour l'historique d'actualisation des données que pour toutes les autres données d'utilisation collectées et stockées.  
  
1.  Dans Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de l'application de service PowerPivot. Le Tableau de bord de gestion PowerPivot apparaît.  
  
3.  Dans Actions, cliquez sur **configurer les paramètres d’application de service** pour ouvrir la page Paramètres d’Application de Service de PowerPivot  
  
4.  Dans la section Collection des données d'utilisation, dans Historique des données d'utilisation, tapez le nombre de jours pendant lequel vous souhaitez conserver un enregistrement de l'activité d'actualisation des données pour chaque classeur.  
  
     La valeur par défaut est 365 jours. La valeur minimale est 1 jour ; la valeur maximale 5 000 jours. La valeur 0 spécifie une période de rétention illimitée ; les données ne sont jamais supprimées. Notez qu'il n'y a aucun paramètre pour désactiver l'historique.  
  
5.  Cliquez sur **OK**.  
  
 Les utilisateurs SharePoint peuvent accéder aux informations d'historique en choisissant l'option Gérer l'actualisation des données d'un classeur assorti d'un historique d'actualisation des données. Ces informations sont également présentées dans le Tableau de bord de gestion PowerPivot utilisé par les administrateurs de batterie de serveurs pour gérer le fonctionnement des services PowerPivot. Pour plus d’informations, consultez [l’historique d’actualisation des données d’affichage &#40;PowerPivot pour SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).  
  
 Pour l'application de service PowerPivot, le stockage physique à long terme des données d'historique s'effectue dans la base de données de l'application de service PowerPivot. Pour plus d’informations sur la façon dont les données d’utilisation collectées et stockées, consultez [collecte des données d’utilisation PowerPivot](power-pivot-sharepoint/power-pivot-usage-data-collection.md).  
  
##  <a name="configTimerJob"></a> Replanifier le travail du minuteur d’actualisation des données PowerPivot  
 L'actualisation des données planifiée est déclenchée par un travail du minuteur d'actualisation des données PowerPivot qui analyse les informations de planification figurant dans la base de données de l'application de service PowerPivot à intervalles d'une minute. Lorsque l'actualisation des données est sur le point de commencer, le travail du minuteur ajoute la requête à une file d'attente de traitement d'un serveur PowerPivot disponible.  
  
 Vous pouvez augmenter l'intervalle entre deux analyses à des fins d'optimisation des performances. Vous pouvez également désactiver le travail du minuteur pour arrêter temporairement les opérations d'actualisation de données lorsque vous devez résoudre des problèmes.  
  
 Le paramétrage par défaut est d'une minute, soit la valeur minimale pouvant être spécifiée. Cette valeur est recommandée, car elle fournit le résultat le plus prédictible pour les planifications qui s'exécutent à des horaires arbitraires au cours de la journée. Par exemple, si un utilisateur planifie l'actualisation des données pour 16:15 et que le travail du minuteur recherche les planifications toutes les minutes, la requête d'actualisation des données planifiée est détectée à 16:15 et le traitement intervient quelques minutes après 16:15.  
  
 Si vous augmentez l'intervalle d'analyse de sorte que celle-ci n'intervienne que très rarement (par exemple, une fois par jour à minuit), toutes les opérations d'actualisation des données planifiées au cours de cet intervalle sont ajoutées à la fois à la file d'attente de traitement, ce qui peut surcharger le serveur et priver de ressources système d'autres applications. En fonction du nombre d'actualisations planifiées, la file d'attente de traitement peut prendre des proportions telles que tous les travaux ne pourront pas être effectués. Les requêtes d'actualisation des données figurant en fin de file d'attente peuvent alors être supprimées si elles coïncident avec le début de l'intervalle de traitement suivant.  
  
 Si votre configuration matérielle le permet, vous pouvez mitiger ce problème en spécifiant des processeurs supplémentaires afin d'exécuter davantage de travaux d'actualisation de données simultanés. Pour plus d’informations, consultez [configurer l’actualisation des données dédié ou du traitement de Query-Only &#40;PowerPivot pour SharePoint&#41;](configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md). Pour plus d’informations sur comment les requêtes d’actualisation des données sont découverts, ajoutés à une file d’attente et traitées, consultez [d’actualisation des données PowerPivot](power-pivot-sharepoint/power-pivot-data-refresh.md).  
  
1.  Dans l'Administration centrale, cliquez sur **Analyse**.  
  
2.  Cliquez sur **Examiner les définitions de travail**.  
  
3.  Sélectionnez le **travail du minuteur d’actualisation des données PowerPivot**.  
  
4.  Modifiez la fréquence de la planification pour modifier la fréquence à laquelle le travail du minuteur doit rechercher les informations de planification de l'actualisation des données.  
  
##  <a name="bkmk_disableDR"></a> Désactiver le travail du minuteur d’actualisation des données  
 Le travail du minuteur d'actualisation des données PowerPivot est un travail de niveau batterie de serveurs qui est soit activé, soit désactivé pour toutes les instances du serveur PowerPivot de la batterie de serveurs. Il n'est pas attaché à une application Web ou de service PowerPivot spécifique. Vous ne pouvez pas le désactiver sur certains serveurs pour forcer le traitement de l'actualisation des données sur d'autres serveurs de la batterie de serveurs.  
  
 Si vous désactivez le travail du minuteur d'actualisation des données PowerPivot, les requêtes déjà présentes dans la file d'attente seront traitées, mais aucune nouvelle requête ne sera ajoutée tant que vous ne l'aurez pas réactivé. Les requêtes qui ont été planifiées pour intervenir dans le passé ne sont pas traitées.  
  
 La désactivation du travail du minuteur n'a pas d'incidence sur la disponibilité de la fonctionnalité dans les pages d'application. Il n'existe aucun moyen de supprimer ou masquer la fonctionnalité d'actualisation des données dans les applications Web. Les utilisateurs qui disposent d'autorisations Collaboration ou supérieures restent en mesure de créer des planifications pour les opérations d'actualisation des données même si le travail du minuteur est définitivement désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [Configurer l’actualisation des données uniquement ou le traitement des requêtes uniquement &#40;PowerPivot pour SharePoint&#41;](configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md)   
 [Configurer PowerPivot compte d’actualisation des données sans assistance &#40;PowerPivot pour SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md)   
 [Configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
  