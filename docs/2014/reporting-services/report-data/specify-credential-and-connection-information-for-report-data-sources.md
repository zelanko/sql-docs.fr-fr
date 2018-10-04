---
title: Spécifier des informations d’identification et de connexion pour les sources de données de rapport | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- no credentials option [Reporting Services]
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- Windows authentication [Reporting Services]
- data sources [Reporting Services], security
- connection strings [Reporting Services]
- unattended report processing [Reporting Services]
- reports [Reporting Services], security
- remote data sources [Reporting Services]
- credentials [Reporting Services]
- authentication [Reporting Services]
- external data sources [Reporting Services]
- prompted credentials [Reporting Services]
- multiple connections
- stored credentials [Reporting Services]
- security [Reporting Services], data sources
- Windows integrated security [Reporting Services]
ms.assetid: fee1a663-a313-424a-aed2-5082bfd114b3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ce1866d4ffde34052a05ec6fbcbcd2c0dacaea42
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082241"
---
# <a name="specify-credential-and-connection-information-for-report-data-sources"></a>Spécifier des informations d'identification et de connexion pour les sources de données de rapport
  Un serveur de rapports utilise des informations d'identification pour se connecter à des sources de données externes qui fournissent du contenu aux rapports ou des informations de destinataire aux abonnements pilotés par les données. Vous pouvez spécifier des informations d'identification qui utilisent l'authentification Windows, l'authentification de base de données, aucune authentification ou une authentification personnalisée. Lors de l'envoi d'une demande de connexion sur le réseau, le serveur de rapports emprunte l'identité d'un compte d'utilisateur ou du compte d'exécution sans assistance. Pour plus d’informations sur le contexte de sécurité sous lequel une demande de connexion est émise, consultez [Configuration d’une source de données et connexions réseau](#DataSourceConfigurationConnections) plus loin dans cette rubrique.  
  
> [!NOTE]  
>  Les informations d'identification permettent également d'authentifier les utilisateurs qui accèdent à un serveur de rapports. Des informations supplémentaires sur l'authentification des utilisateurs sur un serveur de rapports sont fournies dans une autre rubrique.  
  
 La connexion à une source de données externe est définie lorsque vous créez le rapport. Elle peut être gérée séparément une fois le rapport publié. Vous pouvez spécifier une expression ou une chaîne de connexion statique qui autorise les utilisateurs à sélectionner une source de données à partir d'une liste dynamique. Pour plus d’informations sur la façon de spécifier une chaîne de connexion et de type de source de données, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
## <a name="using-remote-data-sources"></a>Utilisation de sources de données distantes  
 Si le rapport récupère des données à partir d'un serveur de base de données distant, vérifiez les éléments suivants :  
  
-   Les informations d'identification fournies au serveur de base de données sont valides. Si vous utilisez des informations d'identification de l'utilisateur Windows, assurez-vous que l'utilisateur a l'autorisation d'accéder au serveur et à la base de données.  
  
-   Les ports utilisés par le serveur de base de données sont ouverts. Si vous accédez à des bases de données relationnelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur des ordinateurs externes, ou si la base de données du serveur de rapports se trouve sur une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] externe, vous devez ouvrir les ports 1433 et 1434 sur l'ordinateur externe. Veillez à redémarrer le serveur après avoir ouvert les ports. Pour plus d’informations, consultez [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).  
  
-   Les connexions distantes doivent être activées. Si vous accédez à des bases de données relationnelles SQL Server sur des ordinateurs externes, vous pouvez utiliser l'outil Gestionnaire de configuration SQL Server pour vous assurer que les connexions distantes via TCP sont activées.  
  
## <a name="ways-to-specify-credentials-for-connecting-to-remote-data-sources"></a>Spécifications des informations d'identification pour la connexion à des sources de données distantes  
 Les sources de données qui fournissent du contenu aux rapports sont habituellement hébergées sur des serveurs distants. Pour extraire des données pour un rapport, un serveur de rapports doit se connecter au serveur en utilisant un jeu d'informations d'identification que vous fournissez d'avance ou qui est obtenu au moment de l'exécution. Lors de la configuration d'une source de données, vous pouvez spécifier des informations d'identification de la manière suivante :  
  
-   demander à l'utilisateur des informations d'identification ;  
  
-   stocker des informations d'identification ;  
  
-   utiliser la sécurité intégrée Windows ;  
  
-   aucune utilisation d'informations d'identification.  
  
 L'environnement réseau détermine les types de connexions que vous pouvez prendre en charge. Par exemple, si le protocole Kerberos version 5 est activé, vous pouvez utiliser les fonctionnalités de délégation et d'emprunt d'identité de l'authentification Windows pour prendre en charge les connexions entre serveurs. Si votre réseau ne prend pas en charge ces fonctionnalités de sécurité, vous devrez contourner les contraintes de connexion. Si la délégation et l'emprunt d'identité ne sont pas activés, les informations d'identification Windows peuvent être passées via une connexion d'ordinateur avant d'expirer. Une connexion utilisateur depuis un ordinateur client vers un ordinateur du serveur de rapports compte comme la première connexion. Si l'utilisateur ouvre un rapport qui récupère des données sur un serveur distant, cette connexion compte comme une deuxième connexion et échoue si vous avez spécifié que la connexion doit utiliser la sécurité intégrée lorsque la délégation n'est pas activée.  
  
 Si plusieurs connexions sont exigées pour exécuter un aller-retour réseau à partir de l'ordinateur client sur une source de données du rapport externe, choisissez une des stratégies suivantes pour y réussir.  
  
-   Activez les fonctionnalités d'emprunt d'identité et de délégation dans votre domaine afin que les informations d'identification puissent être déléguées sans limite à d'autres ordinateurs.  
  
-   Utilisez des informations d'identification stockées ou demandées par invite pour puiser dans des sources de données externes des données pour les rapports. Les informations d'identification peuvent être un compte de domaine Windows ou une connexion de base de données.  
  
### <a name="prompted-credentials"></a>Informations d'identification demandées par invite  
 Lorsque vous configurez une connexion de source de données de rapport afin qu'elle utilise des informations d'identification demandées par invite, chaque utilisateur qui accède au rapport doit entrer un nom d'utilisateur et un mot de passe pour récupérer les données. Cette approche est recommandée pour les rapports qui contiennent des données confidentielles. Les informations d'identification demandées par invite ne peuvent être utilisées que sur les rapports qui s'exécutent à la demande. Les informations d'identification demandées par invite peuvent être un compte de domaine Windows ou une connexion de base de données. Pour utiliser l’authentification Windows, vous devez sélectionner **Utiliser en tant qu’informations d’identification Windows lors de la connexion à la source de données**. Sinon, le serveur de rapports passe les informations d'identification au serveur de base de données pour l'authentification de l'utilisateur. Si le serveur de base de données ne parvient pas à authentifier les informations d’identification fournies, la connexion échoue.  
  
### <a name="windows-integrated-security"></a>Sécurité intégrée de Windows  
 Quand vous utilisez l’option **Sécurité intégrée de Windows** , le serveur de rapports transmet le jeton de sécurité de l’utilisateur qui accède au rapport au serveur qui héberge la source de données externe. Dans ce cas, l'utilisateur n'est pas invité à taper son nom d'utilisateur ou son mot de passe. Cette approche est recommandée si les fonctionnalités d'emprunt d'identité et de délégation sont activées. Si ces fonctionnalités ne sont pas activées, vous ne devez utiliser cette approche que si tous les serveurs auxquels vous voulez accéder résident sur le même ordinateur.  
  
### <a name="stored-credentials"></a>Informations d'identification stockées  
 Vous pouvez stocker les informations d'identification utilisées pour accéder à une source de données externe. Les informations d'identification sont stockées à l'aide d'un chiffrement réversible dans la base de données du serveur de rapports. Vous pouvez spécifier un ensemble d'informations d'identification pour chaque source de données utilisée dans un rapport. Les informations d'identification fournies récupèrent les mêmes données pour chaque utilisateur qui exécute le rapport.  
  
 Les informations d'identification stockées sont recommandées dans le cadre d'une stratégie d'accès aux serveurs de base de données distants. Le stockage d'informations d'identification est obligatoire pour prendre en charge les abonnements, planifier la génération d'historiques de rapports ou l'actualisation d'instantanés de rapports. Lorsqu'un rapport s'exécute en tant que processus d'arrière-plan, le serveur de rapports est l'agent qui exécute le rapport. En l'absence de contexte utilisateur en place, le serveur de rapports doit obtenir les informations d'identification de la base de données du serveur de rapports pour se connecter à une source de données.  
  
 Le nom d'utilisateur et le mot de passe que vous spécifiez peuvent être des informations d'identification de Windows ou une connexion de base de données. Si vous spécifiez des informations d'identification Windows, le serveur de rapports transmet les informations d'identification à Windows pour authentification ultérieure. Autrement, les informations d'identification sont transmises au serveur de base de données pour authentification.  
  
#### <a name="how-to-grant-allow-log-on-locally-permissions-to-domain-user-accounts"></a>Comment accorder des autorisations « Permettre l'ouverture d'une session locale » à des comptes d'utilisateurs de domaine  
 Si vous utilisez des informations d'identification stockées pour vous connecter à une source de données externe, le compte d'utilisateur de domaine Windows doit être autorisé à ouvrir une session localement. Cette autorisation permet au serveur de rapports d'emprunter l'identité de l'utilisateur sur le serveur de rapports et d'envoyer la requête à la source de données externe en utilisant l'identité de l'utilisateur.  
  
 Pour accorder cette autorisation, procédez comme suit :  
  
1.  Sur le serveur de rapports, dans **Outils d’administration**, ouvrez **Stratégie de sécurité locale**.  
  
2.  Sous **Paramètres de sécurité**, développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **Permettre l’ouverture d’une session locale** , puis cliquez avec le bouton droit sur **Propriétés**.  
  
4.  Cliquez sur **Ajouter un groupe ou un utilisateur**.  
  
5.  Cliquez sur **Emplacements**, spécifiez un domaine ou un autre emplacement à rechercher, puis cliquez sur **OK**.  
  
6.  Entrez le compte Windows pour lequel vous voulez autoriser une connexion interactive, puis cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue **Propriétés de Permettre l’ouverture d’une session locale** , cliquez sur **OK**.  
  
8.  Assurez-vous que le compte que vous avez sélectionné ne possède pas d'autorisations refusées :  
  
    1.  Cliquez avec le bouton droit sur **Interdire l’ouverture d’une session locale** , puis cliquez avec le bouton droit sur **Propriétés**.  
  
    2.  Si le compte figure dans la liste, sélectionnez-le et cliquez sur **Supprimer**.  
  
#### <a name="using-impersonation-with-stored-credentials"></a>Utilisation d'emprunt d'identité avec stockage des informations d'identification  
 Vous pouvez également utiliser des informations d'identification pour emprunter l'identité d'un autre utilisateur. Pour les bases de données SQL Server, à l’aide de l’emprunt d’identité options définit le [SETUSER](/sql/t-sql/statements/setuser-transact-sql) (fonction).  
  
> [!IMPORTANT]  
>  N'utilisez pas l'emprunt d'identité pour les rapports qui prennent en charge les abonnements ou qui utilisent des planifications pour générer des historiques de rapports ou actualiser un instantané d'exécution de rapport.  
  
### <a name="no-credentials"></a>Aucune information d'identification  
 Vous pouvez configurer une connexion de source de données de sorte qu'elle n'utilise aucune information d'identification. Étant donné que Microsoft recommande de toujours utiliser des informations d'identification pour accéder aux sources de données, le fait de choisir de ne pas en utiliser n'est pas conseillé. Toutefois, vous pouvez choisir d'exécuter un rapport sans information d'identification dans les cas suivants :  
  
-   La source de données distante ne nécessite pas d'informations d'identification.  
  
-   Les informations d'identification figurent dans la chaîne de connexion (recommandé uniquement pour les connexions sécurisées).  
  
-   Le rapport est un sous-rapport qui utilise les informations d'identification du rapport parent.  
  
 Dans ces conditions, le serveur de rapports se connecte à une source de données distante à l'aide du compte d'exécution sans assistance qui doit être défini à l'avance. Étant donné que le serveur de rapports ne se connecte pas à un serveur distant en utilisant ses informations d'identification de service, vous devez spécifier un compte que le serveur de rapports peut utiliser pour établir la connexion. Pour plus d’informations sur la création de ce compte, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
##  <a name="DataSourceConfigurationConnections"></a> Configuration d’une source de données et connexions réseau  
 Le tableau suivant montre comment les connexions sont établies pour des combinaisons spécifiques de types d'informations d'identification et d'extensions de traitement de données. Si vous utilisez une extension de traitement de données personnalisée, consultez [Spécifier des connexions pour des extensions de traitement de données personnalisées](specify-connections-for-custom-data-processing-extensions.md).  
  
|**Type**|**Contexte de connexion réseau**|**Types de source de données**<br /><br /> **(SQL Server, Oracle, ODBC, OLE DB, Analysis Services, XML, SAP NetWeaver BI, Hyperion Essbase)**|  
|--------------|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|  
|Sécurité intégrée|Emprunter l'identité de l'utilisateur actuel.|Pour tous les types de sources de données, se connecter en utilisant le compte d'utilisateur actuel.|  
|Informations d'identification Windows|Emprunter l'identité de l'utilisateur spécifié.|Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, ODBC et OLE DB : connectez-vous à l'aide du compte d'utilisateur avec emprunt d'identité.|  
|Informations d'identification de la base de données|Emprunter l'identité du compte d'exécution sans assistance ou du compte de service.<br /><br /> (Reporting Services supprime les autorisations d'administrateur lors de l'envoi d'une demande de connexion utilisant l'identité du service).|Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, ODBC et OLE DB :<br /><br /> Ajouter le nom d'utilisateur et le mot de passe à la chaîne de connexion.<br /><br /> Pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:<br /><br /> La connexion aboutit si vous utilisez le protocole TCP/IP, sinon elle échoue.<br /><br /> Pour XML :<br /><br /> La connexion échoue sur le serveur de rapports si des informations d'identification de base de données sont utilisées.|  
|None|Emprunter l'identité du compte d'exécution sans assistance.|Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, ODBC et OLE DB :<br /><br /> Utiliser les informations d'identification définies dans la chaîne de connexion. La connexion échoue sur le serveur de rapports si le compte d'exécution sans assistance n'est pas défini.<br /><br /> Pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:<br /><br /> La connexion échoue toujours si aucune information d'identification n'est spécifiée, même si le compte d'exécution sans assistance est défini.<br /><br /> Pour XML :<br /><br /> Se connecter comme utilisateur anonyme si le compte d'exécution sans assistance est défini ; sinon, la connexion échoue.|  
  
## <a name="setting-credentials-programmatically"></a>Définition des informations d'identification par programme  
 Vous pouvez définir des informations d'identification dans votre code pour contrôler l'accès aux rapports et au serveur de rapports. Pour plus d’informations, consultez [des Sources de données et les méthodes de connexion](../report-server-web-service/methods/data-sources-and-connection-methods.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Gérer les Sources de données de rapport](../../integration-services/connection-manager/data-sources.md)   
 [Le Gestionnaire de rapports &#40;SSRS en Mode natif&#41;](../report-manager-ssrs-native-mode.md)   
 [Créer, supprimer ou modifier une Source de données partagée &#40;le Gestionnaire de rapports&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Configurer les propriétés de Source de données pour un rapport &#40;le Gestionnaire de rapports&#41;](configure-data-source-properties-for-a-report-report-manager.md)  
  
  
