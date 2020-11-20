---
title: Configurer WSUS
description: Ces instructions vous guident tout au long des étapes d’utilisation de l’Assistant Configuration de Windows Server Update Services (WSUS) pour configurer WSUS pour Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 06ac0126bb12668654c04e6a82b20ca551dd925e
ms.sourcegitcommit: a49a66dbda0cb16049e092b49c8318ac3865af3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94983056"
---
# <a name="configure-windows-server-update-services-wsus-in-analytics-platform-system"></a>Configurer Windows Server Update Services (WSUS) dans Analytics Platform System
Ces instructions vous guident tout au long des étapes d’utilisation de l’Assistant Configuration de Windows Server Update Services (WSUS) pour configurer WSUS pour Analytics Platform System. Vous devez configurer WSUS avant de pouvoir appliquer des mises à jour logicielles à l’appliance. WSUS est déjà installé sur la machine virtuelle VMM de l’appliance.  
  
Pour plus d’informations sur la configuration de WSUS, consultez le [Guide d’installation pas à pas de WSUS](/windows/deployment/deploy-whats-new) sur le site Web WSUS. Après la configuration de WSUS, consultez [Télécharger et appliquer des mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) pour lancer une mise à jour.  
  
> [!WARNING]  
> Si vous rencontrez des erreurs pendant ce processus de configuration, arrêtez et contactez le support technique pour obtenir de l’aide. N’ignorez pas les erreurs ou continuez dans le processus après la réception des erreurs.  
  
## <a name="before-you-begin"></a>Avant de commencer  
Pour configurer WSUS, vous devez :  
  
-   Utilisez les informations de connexion du compte d’administrateur de domaine de l’appliance Analytics Platform System.  
  
-   Disposer d’une connexion Analytics Platform System disposant des autorisations pour accéder à la **console d’administration** et afficher les informations d’état de l’appliance.  
  
-   Vous devez connaître l’adresse IP du serveur WSUS en amont si vous envisagez de synchroniser les mises à jour à partir d’un serveur WSUS en amont au lieu de synchroniser les mises à jour directement à partir de Microsoft Update. Assurez-vous que votre serveur WSUS en amont est configuré pour autoriser les connexions anonymes et prend en charge SSL.  
  
-   Vous devez connaître l’adresse IP du serveur proxy si votre appliance doit utiliser un serveur proxy pour accéder au serveur en amont ou à Microsoft Update.  
  
-   Dans la plupart des cas, WSUS doit accéder aux serveurs en dehors de l’appliance. Pour prendre en charge ce scénario d’utilisation, le système DNS de la plateforme d’analyse peut être configuré pour prendre en charge un redirecteur de nom externe qui permettra aux ordinateurs hôtes du système de plateforme d’analyse et aux machines virtuelles d’utiliser des serveurs DNS externes pour résoudre les noms en dehors de l’appliance. Pour plus d’informations, consultez [utiliser un redirecteur DNS pour résoudre les noms DNS non-Appliance &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>Pour configurer Windows Server Update Services (WSUS)  
  
1.  Connectez-vous à la **console d’administration**. Dans l' **onglet État** de l’appliance, vérifiez que les colonnes **cluster** et **réseau** affichent le vert (ou **na**) pour tous les nœuds. Vérifiez les indicateurs d’état de tous les nœuds de l’état de l' **Appliance**.  
  
    -   Il est possible de continuer en toute sécurité avec des indicateurs en vert ou en NA.  
  
    -   Évaluer les erreurs d’avertissement non critiques (jaunes). Dans certains cas, les messages d’avertissement ne bloquent pas les mises à jour. S’il y a une erreur de volume de disque non critique qui ne se trouve pas sur C:\ , vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
    -   La plupart des indicateurs rouges doivent être résolus avant de continuer. En cas de défaillances de disque, utilisez la page alertes de la **console d’administration** pour vérifier qu’il n’y a pas plus d’une défaillance de disque au sein de chaque serveur ou groupe San. S’il n’y a pas plus d’une défaillance de disque au sein de chaque serveur ou groupe SAN, vous pouvez passer à l’étape suivante avant de résoudre les défaillances de disque. Veillez à contacter le support Microsoft pour résoudre les défaillances de disque dès que possible.  
  
2.  Connectez-vous à la machine virtuelle VMM en tant qu’administrateur de domaine de l’appliance.  
  
3.  Lancez l’Assistant Configuration de.  
  
    #### <a name="to-launch-the-configuration-wizard"></a>Pour lancer l’Assistant Configuration  
  
    1.  Dans le **tableau de bord gestionnaire de serveur**, dans le menu **Outils** , cliquez sur **Windows Server Update Services**.  
  
    2.  Dans le volet gauche de la fenêtre **Update Services** , développez le serveur du nœud de gestion des machines virtuelles (**_appliance_domain_-VMM**), puis cliquez sur **options**.  
  
    3.  Dans le volet **options** , cliquez sur **Assistant Configuration du serveur WSUS** pour lancer l’Assistant Configuration.  
  
        ![Menu du tableau de bord du gestionnaire de serveur](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  Si c’est la première fois que vous exécutez l’Assistant WSUS, vous pouvez être invité à configurer un répertoire pour le stockage des mises à jour. `C:\wsus` est un emplacement approprié ; Toutefois, vous pouvez fournir un chemin d’accès différent.  
  
        ![Chemin d'accès WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  Passez en revue la liste **avant de commencer** la liste des éléments à terminer avant de terminer l’Assistant.  
  
        ![WSUS - Avant de commencer](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  Dans la page **rejoindre le programme d’amélioration du Microsoft Update** , sélectionnez **Oui, je souhaite participer au programme d’amélioration de l’Microsoft Update**, puis cliquez sur **suivant**.  
  
        ![WSUS - Programme d'amélioration](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    Vous devez maintenant voir la page **choisir un serveur en amont** . La capture d’écran suivante est le point de départ de l’Assistant Configuration de.  
  
    ![WSUS - Synchronisation du serveur en amont](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  Choisissez le serveur en amont.  
  
    Dans la page **choisir un serveur en amont** de l’Assistant Configuration de WSUS, vous devez sélectionner la façon dont WSUS sur le nœud de gestion d’ordinateur virtuel se connecte à un serveur en amont pour obtenir les mises à jour logicielles. Vous avez deux possibilités pour synchroniser le serveur en amont avec [Microsoft Update](https://go.microsoft.com/fwlink/?LinkId=133349) ou pour synchroniser les mises à jour avec un autre serveur de Windows Server Update Services.  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Pour effectuer une mise à jour à l’aide de Microsoft Update  
  
    1.  Si vous choisissez de synchroniser avec Microsoft Update, vous n’avez pas besoin d’apporter des modifications à la page **choisir un serveur en amont** . Cliquez sur **Suivant**.  
  
        ![WSUS - Synchronisation du serveur en amont](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>Pour effectuer une mise à jour à partir d’un autre serveur WSUS  
  
    1.  Si vous choisissez de synchroniser avec une source autre que Microsoft Update (un serveur en amont), spécifiez le serveur (entrez l’adresse IP) et le port sur lequel ce serveur communiquera avec le serveur en amont.  
  
        ![WSUS - Synchronisation du serveur en amont à partir de WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Pour utiliser protocole SSL (SSL), activez la case à cocher **utiliser SSL lors de la synchronisation des informations de mise à jour** . Dans ce cas, les serveurs utilisent le port 443 pour la synchronisation.  
  
        ![WSUS - Synchronisation du serveur en amont à partir de WSUS SSL](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  Dans le cas d’un serveur réplica, activez la case à cocher **Il s’agit d’un réplica du serveur en amont**. Il est possible de sélectionner les deux **utiliser SSL lors de la synchronisation des informations de mise à jour** et **il s’agit d’un réplica du serveur en amont**.  
  
        ![WSUS - Réplica du serveur en amont](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  À ce stade, vous avez terminé la configuration du serveur en amont. Cliquez sur **suivant**, ou sélectionnez **spécifier un serveur proxy** dans le volet de navigation gauche.  
  
5.  Spécifiez le serveur proxy.  
  
    Si ce serveur nécessite un serveur proxy pour accéder à Microsoft Update ou à un autre serveur en amont, vous pouvez configurer les paramètres du serveur proxy ici. Sinon, cliquez sur **suivant**.  
  
    ![Proxy WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>Pour configurer les paramètres de serveur proxy  
  
    1.  Dans la page **spécifier le serveur proxy** de l’Assistant Configuration, activez la case à cocher **utiliser un serveur proxy lors** de la synchronisation, puis tapez l’adresse IP du serveur proxy (et non le nom) et le numéro de port (port 80 par défaut) dans les zones correspondantes.  
  
    2.  Pour vous connecter au serveur proxy à l’aide d’informations d’identification de l’utilisateur spécifiques, activez la case à cocher **Utiliser les informations d’identification de l’utilisateur pour se connecter au serveur proxy**, puis saisissez le nom d’utilisateur, le domaine et le mot de passe de l’utilisateur dans les zones correspondantes. Si vous souhaitez activer l’authentification de base pour l’utilisateur qui se connecte au serveur proxy, activez la case à cocher **autoriser l’authentification de base (le mot de passe est envoyé en texte clair)** .  
  
        ![WSUS - Informations d'identification proxy](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  À ce stade, vous avez terminé la configuration du serveur proxy. Cliquez sur **Suivant** pour afficher la page suivante, dans laquelle vous pouvez commencer à configurer le processus de synchronisation.  
  
6.  Démarrez la connexion.  
  
    ![WSUS - Connexion proxy initiale en cours](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    Cliquez sur **Démarrer la connexion**.  
  
    Une fois la connexion établie, cliquez sur **suivant** pour passer à la page suivante, dans laquelle vous pouvez choisir langues.  
  
7.  Choisissez langues.  
  
    Sélectionnez **Télécharger les mises à jour uniquement dans ces langues**.  
  
    Sélectionnez **anglais**, puis cliquez sur **suivant**.  
  
    ![Choisir langues](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  Choisissez produits.  
  
    > [!NOTE]  
    > Si vous utilisez un serveur en amont, vous ne pourrez peut-être pas choisir produits. Si cette option n’est pas disponible, ignorez cette étape.

    > [!WARNING]  
    > Excluez les mises à jour SQL Server 2016.
  
    Désélectionnez toutes les mises à jour sélectionnées.  
  
    Sélectionnez **SQL Server 2012**, **SQL Server 2014**, **Windows Server 2012 R2**, **System Center 2012 R2-Virtual Machine Manager**, **Windows Server 2016** et **System Center 2016-Virtual Machine Manager** , puis cliquez sur **suivant**.  
  
9. Choisissez classifications.  
  
    > [!NOTE]  
    > Si vous utilisez un serveur en amont, vous ne pourrez peut-être pas choisir de classifications.  Si cette option n’est pas disponible, ignorez cette étape.  
  
    Désélectionnez toutes les mises à jour précédemment sélectionnées.  
  
    Sélectionnez les mises à jour **critiques**, les mises à jour de **sécurité** et les **correctifs cumulatifs** pour les mises à jour qui seront synchronisées pour l’appliance Analytics Platform System, puis cliquez sur **suivant**.  
  
    ![Choisir classifications](./media/configure-windows-server-update-services-wsus/sql-server-pdw-wsus-choose-classifications.png "SQL-Server-PDW-WSUS-Choose-classifications")  
  
10. Configurez le calendrier de synchronisation.  
  
    Sélectionnez **synchroniser manuellement**, puis cliquez sur **suivant**.  
  
    ![Définir la planification de synchronisation](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. Commencer la synchronisation initiale.  
  
    Sélectionnez **commencer la synchronisation initiale**, puis cliquez sur **suivant**.  
  
12. Terminer.  
  
    Cliquez sur **Terminer**.  
  
## <a name="group-the-appliance-servers-in-wsus"></a><a name="bkmk_WSUSGroup"></a>Regrouper les serveurs d’appliance dans WSUS  
Après la configuration de WSUS pour Analytics Platform System, l’étape suivante consiste à regrouper les serveurs de l’appliance. En ajoutant tous les serveurs d’appliances à un groupe, WSUS peut appliquer les mises à jour logicielles à tous les serveurs de l’appliance.  
  
> [!NOTE]  
> Le système WSUS est conçu pour s’exécuter de façon asynchrone. Le lancement de l’activité n’entraîne pas toujours une mise à jour immédiate. Par conséquent, vous devrez peut-être attendre un certain temps jusqu’à ce que les ordinateurs soient visibles dans les boîtes de dialogue WSUS. L’exécution `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` de la commande décrite à la fin de la rubrique [Télécharger et appliquer les mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) peut aider à actualiser les boîtes de dialogue.  
  
#### <a name="to-group-the-appliance-servers"></a>Pour regrouper les serveurs d’appliance  
  
1.  Ouvrez la console WSUS, cliquez avec le bouton droit sur **tous les ordinateurs** , puis cliquez sur **Ajouter un groupe d’ordinateurs**.  
  
    ![Ajouter un groupe d'ordinateurs.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  Entrez le nom « APS » pour le groupe d’ordinateurs, puis cliquez sur **Ajouter**.  
  
    ![Entrer un nom pour le nouveau groupe d'ordinateurs.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  Cliquez à nouveau sur **tous les ordinateurs** , modifiez l’État dans le menu déroulant **État** en **n’importe quel**, puis cliquez sur **Actualiser**. Pour afficher le nouveau groupe que vous venez d’ajouter, vous devrez peut-être développer **tous les ordinateurs** en cliquant dessus dans le contrôle d’arborescence à gauche.  
  
    ![Modifier l'état en N'importe lequel et cliquer sur Actualiser](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  Sélectionnez tous les ordinateurs qui font partie de l’appliance, cliquez avec le bouton droit, puis cliquez sur **modifier l’appartenance**.  
  
    ![Modifier l'appartenance de tous les ordinateurs PDW.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  Sélectionnez le nouveau groupe d’ordinateurs que vous avez créé en cliquant sur la case à cocher, puis sur **OK**.  
  
    ![Définissez l'appartenance au groupe d'ordinateurs](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  Sélectionnez le nouveau groupe d’ordinateurs, changez son **État** en **n’importe lequel**, puis cliquez sur **Actualiser**. Tous les ordinateurs doivent maintenant être attribués à ce groupe et sont listés dans le volet droit. Il est généralement possible de continuer quand les nœuds affichent des avertissements, tels que **ce nœud n’a pas encore signalé d’État**.  
  
    ![Changez l’État en n’importe lequel, puis cliquez sur Actualiser.](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
