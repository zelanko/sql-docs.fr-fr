---
title: Créer une base de données du serveur de rapports en mode natif (Gestionnaire de configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- databases [Reporting Services], creating
ms.assetid: 81b9f4ad-800b-4688-8b47-a5a83dc8ff10
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8ff6878b05138bb1ad4c23e57699dd896ab7b441
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198821"
---
# <a name="create-a-native-mode-report-server-database--ssrs-configuration-manager"></a>Créer une base de données du serveur de rapports en mode natif (Gestionnaire de configuration de SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif utilise une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le stockage interne. La base de données est un composant nécessaire et elle permet de stocker les rapports publiés, les modèles, les sources de données partagées, les données de session, les ressources et les métadonnées du serveur.  
  
 Pour créer une base de données du serveur de rapports ou modifier la chaîne de connexion ou les informations d'identification, utilisez les options de la page Base de données du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] En Mode natif|  
  
## <a name="when-to-create-or-configure-the-report-server-databases"></a>Quand créer ou configurer les bases de données de serveur de rapports  
 Vous devez créer et configurer la base de données du serveur de rapports si vous avez installé le serveur de rapports en mode fichiers uniquement.  
  
 Si vous avez installé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] soit la configuration par défaut pour le mode natif, la base de données de serveur de rapports a été créé et configuré automatiquement lorsque l’instance de serveur de rapports a été installée. Vous pouvez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour afficher ou modifier les paramètres que le programme d'installation a configurés automatiquement.  
  
##  <a name="rsdbrequirements"></a> Avant de commencer  
 La création ou la configuration d'une base de données de serveur de rapports est un processus comportant plusieurs étapes. Avant de créer la base de données du serveur de rapports, pensez à la façon dont vous souhaitez spécifier les éléments suivants :  
  
 Sélectionner un serveur de base de données  
 Consultez les versions prises en charge du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans [Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md).  
  
 Activer les connexions TCP/IP  
 Activez les connexions TCP/IP pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Certaines éditions du [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’activent pas TCP/IP par défaut. Les instructions sont fournies dans cette rubrique.  
  
 Ouvrir le port pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Pour un serveur distant, si vous utilisez le logiciel de pare-feu, vous devez ouvrir le port sur lequel le [!INCLUDE[ssDE](../../includes/ssde-md.md)] écoute.  
  
 Choisir les informations d'identification du serveur de rapports  
 Décidez comment le serveur de rapports se connectera aux bases de données de serveur de rapports. Les types d'informations d'identification incluent le compte d'utilisateur de domaine, le compte d'utilisateur de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le compte de service Report Server.  
  
 Ces informations d'identification sont chiffrées et stockées dans le fichier RSReportServer.config. Le serveur de rapports utilise ces informations d'identification pour les connexions continues à la base de données du serveur de rapports. Si vous souhaitez utiliser un compte d'utilisateur Windows ou un compte d'utilisateur de base de données, veillez bien à en spécifier un qui existe déjà. Bien que le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] crée une connexion et définisse les autorisations nécessaires, il ne crée pas de compte automatiquement. Pour plus d’informations, consultez [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 Choisir une langue du serveur de rapports  
 Choisissez une langue à spécifier pour le serveur de rapports. Les noms de rôle prédéfinis, les descriptions et les dossiers Mes rapports n'apparaissent pas en différentes langues lorsque les utilisateurs se connectent au serveur à l'aide de différentes versions linguistiques d'un navigateur.  
  
 Vérifier les informations d'identification pour créer et mettre en service la base de données  
 Vérifiez que les informations d’identification de votre compte ont l’autorisation de créer des bases de données sur l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Ces informations d’identification sont utilisées pour une connexion unique afin de créer la base de données du serveur de rapports et **RSExecRole**. Si une connexion n'existe pas déjà, une connexion d'utilisateur de la base de données est créée pour le compte utilisé par le serveur de rapports pour se connecter à la base de données. Vous pouvez vous connecter sous le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows avec lequel vous êtes connecté ou vous pouvez entrer une connexion de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-enable-access-to-a-remote-report-server-database"></a>Pour activer l'accès à une base de données distante du serveur de rapports  
  
1.  Si vous utilisez une instance distante du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , ouvrez une session sur le serveur de base de données pour vérifier ou activer les connexions TCP/IP.  
  
2.  Dans le menu **Démarrer**, pointez successivement sur **Tous les programmes**, **Microsoft SQL Server**et **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
3.  Ouvrez **Configuration du réseau SQL Server**.  
  
4.  Sélectionnez l'instance.  
  
5.  Avec le bouton droit **TCP/IP** et cliquez sur **activé**.  
  
6.  Redémarrage du service.  
  
7.  Ouvrez votre logiciel de pare-feu, ainsi que le port sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute. Pour l'instance par défaut, il s'agit généralement du port 1433 pour les connexions TCP/IP. Pour plus d’informations, consultez [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-create-a-local-report-server-database"></a>Pour créer une base de données locale du serveur de rapports  
  
1.  Démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous à l'instance du serveur de rapports pour laquelle vous créez la base de données. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  Dans la page Base de données, cliquez sur **Modifier la base de données**.  
  
3.  Cliquez sur **Créer une nouvelle base de données de serveur de rapports**, puis cliquez sur **Suivant**.  
  
4.  Connectez-vous à l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] que vous allez utiliser pour créer et héberger la base de données du serveur de rapports :  
  
    1.  Tapez l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] que vous souhaitez utiliser. L'Assistant affiche un [!INCLUDE[ssDE](../../includes/ssde-md.md)] local qui s'exécute comme instance par défaut en cas de disponibilité. Sinon, vous devez entrer le serveur et l'instance à utiliser. Les instances nommées sont spécifiées dans le format suivant : \<nom_ serveur>\\<nom_instance\>.  
  
    2.  Entrez les informations d’identification utilisées pour une connexion unique au [!INCLUDE[ssDE](../../includes/ssde-md.md)] en vue de créer les bases de données du serveur de rapports. Pour plus d'informations sur la façon dont ces informations d'identification sont utilisées, consultez [Avant de commencer](#rsdbrequirements) dans cette rubrique.  
  
    3.  Pour valider la connexion au serveur, cliquez sur **Tester la connexion** .  
  
    4.  Cliquez sur **Suivant**.  
  
5.  Spécifiez les propriétés utilisées pour créer la base de données. Pour plus d'informations sur la façon dont ces propriétés sont utilisées, consultez [Avant de commencer](#rsdbrequirements) dans cette rubrique :  
  
    1.  Tapez le nom de la base de données du serveur de rapports. Une base de données temporaire est créée parallèlement à la base de données primaire. Pensez à utiliser un nom descriptif qui vous aidera à vous rappeler comment la base de données est utilisée. Notez que le nom que vous spécifiez sera utilisé pendant toute la durée de vie de la base de données. Vous ne pouvez pas renommer une base de données du serveur de rapports après sa création.  
  
    2.  Sélectionnez la langue dans laquelle vous souhaitez que les définitions de rôle et Mes rapports apparaissent.  
  
    3.  Le mode du serveur de rapports est toujours défini à **Natif**.  
  
    4.  Cliquez sur **Suivant**.  
  
6.  Spécifiez les informations d'identification que le serveur de rapports doit utiliser pour se connecter à la base de données du serveur de rapports.  
  
    1.  Spécifiez le type d'authentification :  
  
         Sélectionnez **Informations d'identification de la base de données** pour vous connecter à l'aide d'une connexion de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déjà définie. L'utilisation d'informations d'identification de base de données est recommandée si le serveur de rapports se trouve sur un ordinateur qui est dans un domaine différent, un domaine non approuvé ou derrière un pare-feu.  
  
         Sélectionnez **Informations d’identification Windows** si vous avez un compte d’utilisateur de domaine avec les privilèges les plus faibles qui a l’autorisation de se connecter à l’ordinateur et au serveur de base de données.  
  
         Sélectionnez **Informations d'identification du service** si vous souhaitez que le serveur de rapports se connecte à l'aide de son compte de service. Avec cette option, le serveur se connecte en utilisant la sécurité intégrée ; les informations d'identification ne sont pas chiffrées ou stockées.  
  
    2.  Cliquez sur **Suivant**.  
  
7.  Examinez les informations sur la page Résumé pour vérifier que les paramètres sont corrects, puis cliquez sur **Suivant**.  
  
8.  Vérifiez la connexion en cliquant sur une URL de la page URL de Report Server ou de la page URL du Gestionnaire de rapports. Les URL doivent être définies dans l'ordre pour que ce test fonctionne. Si la connexion à la base de données du serveur de rapports est valide, vous pouvez voir l'arborescence des dossiers du serveur de rapports ou le Gestionnaire de rapports dans une fenêtre de navigateur. Pour plus d’informations, consultez [vérifier une Installation Reporting Services](verify-a-reporting-services-installation.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une connexion de base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Base de données &#40;SSRS en Mode natif&#41;](../../sql-server/install/database-ssrs-native-mode.md)   
 [Gérer un serveur de rapports Reporting Services en Mode natif](../report-server/manage-a-reporting-services-native-mode-report-server.md)   
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
