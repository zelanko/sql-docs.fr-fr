---
title: Installer SQL Server Reporting Services | Documents Microsoft
ms.date: 10/10/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 52c2f8fae79884b025e067b7d628cd3154ba93f4
ms.openlocfilehash: 5ce83ff18d6908441a3eaaf05599068ec5876308
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="install-sql-server-reporting-services"></a>Installation de SQL Server Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

Installation de SQL Server Reporting Services implique des composants de serveur pour le stockage des éléments de rapport, de rendu de rapports et de traitement d’abonnement et d’autres services de rapport.  Découvrez comment installer le serveur de rapports Power BI.

Pour télécharger SQL Server 2017 Reporting Services, accédez à la [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=55252).

> [!NOTE]
> Recherchez Power BI serveur de rapports ? Consultez [installer Power BI Report Server](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/).

## <a name="before-you-begin"></a>Avant de commencer

Avant d’installer Reporting Services, passez en revue les [les exigences matérielles et logicielles pour l’installation de SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).

## <a name="install-your-report-server"></a>Installer votre serveur de rapports

L’installation d’un serveur de rapports est simple. Il existe quelques étapes pour installer les fichiers.

> [!NOTE]
> Vous n’avez pas besoin d’un serveur du moteur de base de données SQL Server disponible au moment de l’installation. Vous avez besoin d’un configuration de Reporting Services après l’installation.

1. Rechercher l’emplacement de SQLServerReportingServices.exe et lancez le programme d’installation.

2. Sélectionnez **installer Reporting Services**.

    ![Installer Reporting Services](media/install-reporting-services/report-server-install.png)

3. Choisissez une édition à installer, puis sélectionnez **suivant**.

    ![Choisir l’édition](media/install-reporting-services/report-server-install-edition.png)

    Vous pouvez choisir l’édition d’évaluation ou de développeur dans la liste déroulante vers le bas.

    ![Éditions d’évaluation ou le développeur](media/install-reporting-services/report-server-install-edition-select.png)

    Sinon, vous pouvez entrer une clé de produit.

4. Lisez et acceptez les termes du contrat de licence, puis sélectionnez **suivant**.

5. Vous devez disposer d’un moteur de base de données pour stocker la base de données du serveur de rapports. Sélectionnez **suivant** pour installer uniquement le serveur de rapports.

    ![Non requis pour l’installation de base de données](media/install-reporting-services/report-server-install-db-engine.png)

6. Spécifiez l’emplacement d’installation du serveur de rapports. Sélectionnez **installer** pour continuer.

    ![Spécifiez le chemin d’installation](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > Le chemin d’accès par défaut est C:\Program Files\Microsoft SQL Server Reporting Services.

7. Après la réussite de l’installation, sélectionnez **configurer Report Server** pour lancer le Gestionnaire de Configuration de Reporting Services.

    ![Configurer le serveur de rapports](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>Configuration de votre serveur de rapports

Après avoir sélectionné **configurer Report Server** dans le programme d’installation, vous n’aurez **Gestionnaire de Configuration de serveur de rapports**. Pour plus d’informations, consultez [Gestionnaire de Configuration de serveur de rapports](reporting-services-configuration-manager-native-mode.md).

Vous devez [créer une base de données du serveur de rapports](ssrs-report-server-create-a-report-server-database.md) pour terminer la configuration initiale de Reporting Services. Un serveur de base de données SQL Server est requis pour effectuer cette étape.

### <a name="creating-a-database-on-a-different-server"></a>Création d’une base de données sur un autre serveur

Si vous créez la base de données du serveur de rapports sur un serveur de base de données sur un autre ordinateur, vous devrez modifier le compte de service pour le serveur de rapports à une information d’identification n’est reconnue sur le serveur de base de données.

Par défaut, le serveur de rapports utilise le compte de service virtuel. Si vous essayez de créer une base de données sur un autre serveur, vous pouvez recevoir l’erreur suivante lors de l’étape de droits de connexion application.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Pour contourner cette erreur, vous pouvez modifier le compte de service au Service réseau ou un compte de domaine. La modification du compte de service au Service réseau s’applique des droits dans le contexte du compte d’ordinateur pour le serveur de rapports.

Pour plus d’informations, consultez [configurer le compte de service report server](configure-the-report-server-service-account-ssrs-configuration-manager.md).

## <a name="windows-service"></a>Service Windows

Un service windows est créé dans le cadre de l’installation. Il est affiché en tant que **SQL Server Reporting Services**. Le nom du service est **SQLServerReportingServices**.

## <a name="default-url-reservations"></a>Réservations d’URL par défaut

Les réservations d'URL se composent d'un préfixe, d'un nom d'hôte, d'un port et d'un répertoire virtuel :

|Élément|Description|
|----------|-----------------|
|Préfixe|Le préfixe par défaut est HTTP. Si vous avez installé précédemment un certificat Secure Sockets Layer (SSL), le programme d’installation tente de créer des réservations d’URL qui utilisent le préfixe HTTPS.|
|Nom d'hôte|Le nom d'hôte par défaut est un caractère générique fort (+). Il indique que le serveur de rapports accepte toute requête HTTP sur le port désigné pour tout nom d’hôte qui correspond à l’ordinateur, y compris `http://<computername>/reportserver`, `http://localhost/reportserver`, ou`http://<IPAddress>/reportserver.`|
|Port|Le port par défaut est 80. Si vous utilisez un port autre que le port 80, vous devez ajouter explicitement à l’URL lorsque vous ouvrez le portail web dans une fenêtre de navigateur.|
|Répertoire virtuel|Par défaut, les répertoires virtuels sont créés dans le format de ReportServer pour le service Web Report Server et les rapports pour le portail web. Pour le service Web Report Server, le répertoire virtuel par défaut est **reportserver**. Pour le portail web, le répertoire virtuel par défaut est **rapports**.|

Voici un exemple de chaîne URL complète :

- `http://+:80/reportserver`, permet d’accéder au serveur de rapports.

- `http://+:80/reports`, permet d’accéder au portail web.

## <a name="firewall"></a>Pare-feu

Si vous accédez au serveur de rapports à partir d’un ordinateur distant, vous souhaitez vous assurer que vous avez configuré les règles de pare-feu si un pare-feu est présent.

Vous devez ouvrir le port TCP que vous avez configurée pour votre URL du Service Web et l’URL du portail Web. Par défaut, ceux-ci sont configurés sur le port TCP 80.

## <a name="additional-configuration"></a>Configuration supplémentaire

- Pour configurer l’intégration avec le service Power BI et pouvoir épingler des éléments de rapport à un tableau de bord Power BI, consultez [intégrer avec le service Power BI](power-bi-report-server-integration-configuration-manager.md).

- Pour configurer la messagerie pour traiter les abonnements, consultez [paramètres de courrier électronique](e-mail-settings-reporting-services-native-mode-configuration-manager.md) et [la remise dans un serveur de rapports par messagerie](../subscriptions/e-mail-delivery-in-reporting-services.md).

- Pour configurer le portail web et le rendre accessible sur un ordinateur distant pour afficher et gérer des rapports, consultez [configurer un pare-feu pour accéder au serveur de rapports](../report-server/configure-a-firewall-for-report-server-access.md) et [configurer un serveur de rapports pour l’administration à distance](../report-server/configure-a-report-server-for-remote-administration.md) .

## <a name="related-information"></a>Informations connexes

Pour plus d’informations sur la façon d’installer le mode natif de SQL Server 2016 Reporting Services, consultez [serveur de rapports en mode natif installer Reporting Services](install-reporting-services-native-mode-report-server.md). Pour plus d’informations sur l’installation de SQL Server 2016 Reporting Services en mode intégré SharePoint, consultez [installer le premier serveur de rapports en mode SharePoint](install-the-first-report-server-in-sharepoint-mode.md).

## <a name="next-steps"></a>Étapes suivantes

Votre serveur de rapports installé, commencer à créer des rapports et déployez-les sur votre serveur de rapports. Pour plus d’informations sur la façon de démarrer le Générateur de rapports, consultez [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md).

Pour créer des rapports à l’aide de SQL Server Data Tools, [télécharger SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714).

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
