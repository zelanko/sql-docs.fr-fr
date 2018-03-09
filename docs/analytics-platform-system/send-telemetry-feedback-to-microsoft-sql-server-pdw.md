---
title: "Envoyer des commentaires de télémétrie à Microsoft (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40a994f0-7eff-4db9-9572-401d6e1187a0
caps.latest.revision: "18"
ms.openlocfilehash: f78a9e7c1e66085dd84ba71e8e7b5f517131e18a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="send-telemetry-feedback-to-microsoft"></a>Envoyer des commentaires de télémétrie à Microsoft
Système de plateforme Analytique possède une fonctionnalité de télémétrie facultatif qui envoie des données de la Console d’administration à Microsoft. Nous vous encourageons à activer cette option pour nous aider à améliorer le produit.  
  
> [!NOTE]  
> Dans cette version, Microsoft ne surveille pas activement les données de télémétrie. Les données collectées sont uniquement à des fins d’analyse.  
  
## <a name="privacy"></a>Confidentialité  
Pour fournir la protection de la confidentialité maximal, les points d’accès est fourni sans activer la télémétrie. Avant d’activer cette fonctionnalité, tout d’abord examiner les [déclaration de confidentialité de Microsoft Analytique plateforme System](http://go.microsoft.com/fwlink/?LinkId=400902). Ensuite, pour participer exécuter le script PowerShell décrit ci-dessous.  
  
## <a name="enable"></a>Activez la télémétrie  
**Transfert de DNS :** envoyer les données de télémétrie à Microsoft requiert le système de plateforme Analytique pour vous connecter à internet via un redirecteur DNS. Pour activer cette fonctionnalité, vous devez activer la redirection DNS sur tous les hôtes et les charges de travail ordinateurs virtuels. Appeler le `Enable-RemoteMonitoring` avec la `SetupDnsForwarder` option Configurer la redirection DNS et activez la télémétrie correctement. Appeler le `Enable-RemoteMonitoring` commande sans le `SetupDnsForwarder` option lors de la redirection DNS est déjà configurée et que vous souhaitez uniquement activer l’analyse de pulsation.  
  
> [!IMPORTANT]  
> Activation du transfert de DNS, la connexion internet pour tous les hôtes et les charges de travail ordinateurs virtuels s’ouvre.  
  
#### <a name="to-enable-feedback"></a>Pour activer les commentaires  
  
1.  À l’aide d’un compte administrateur de domaine appliance, connectez-vous au nœud de contrôle (***appliance_domain*-CTL01**) et ouvrez une invite de commandes à l’aide de vos informations d’identification d’administrateur de Windows.  
  
2.  Accédez au répertoire suivant : `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importez le module`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Pour importer vous devez utiliser les deux points dans la commande.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Appeler le `Enable-RemoteMonitoring` commande.  
  
    > [!NOTE]  
    > Le script suppose que la connexion internet fonctionne correctement et qu’il ne valide pas la connexion internet.  
  
    1.  La première fois que vous activez la télémétrie, utilisez la commande suivante pour vérifier que tous les redirecteurs DNS sont configurées correctement. Dans cet exemple, remplacez l’adresse IP du serveur DNS transféré `xx.xx.xx.xx` avec l’adresse IP du redirecteur DNS dans votre environnement.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Lorsque des redirecteurs DNS sont déjà configurés, telles que la réactivation précédemment désactivée télémétrie, utilisez la commande suivante pour activer la télémétrie sans configurer le DNS de transfert.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Vous devrez lire et accepter que APS collecte des informations sur l’appareil. Il y aura un lien vers la déclaration de confidentialité de points d’accès que vous pouvez copier et coller dans n’importe quel navigateur internet pour un examen.  
  
6.  Entrez **Y** pour accepter et s’abonner à des commentaires ou entrez **N** de ne pas accepter.  
  
7.  Si vous avez entré **Y** il y aura une série de commandes qui seront exécutées qui permettra la télémétrie (et éventuellement le redirecteur DNS) fonctionnalité sur votre appliance. Si vous voyez des erreurs ou des informations qui vous conduit à penser que la commande n’a pas réussie contactez Microsoft pour obtenir une assistance.  
  
Si vous avez entré **N**, aucune commande ne sera exécutée et la fonctionnalité ne sera pas activée, et rien de plus à faire.  
  
Il n’existe pas de risque à en cours d’exécution le `Enable-RemoteMonitoring` commande plusieurs fois. Si le redirecteur DNS est déjà défini, vous obtiendrez un message d’avertissement indiquant qu’est le cas.  
  
## <a name="disable"></a>Désactiver la télémétrie  
La désactivation de télémétrie s’arrête toutes les opérations qui communiquent des informations sur l’état du matériel et les points d’accès de contrôle de service dans le cloud.  
  
> [!IMPORTANT]  
> Cette opération désactivera pas votre redirecteur DNS ou une connexion internet qui peut être utilisé par d’autres fonctionnalités dans l’application.  
  
#### <a name="to-disable-telemetry"></a>Pour désactiver la télémétrie  
  
1.  À l’aide d’un compte administrateur de domaine appliance, connectez-vous au nœud de contrôle (***appliance_domain*-CTL01**) et ouvrez une fenêtre PowerShell avec des privilèges d’administrateur.  
  
2.  Accédez au répertoire suivant : `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importez le module`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Pour importer vous devez utiliser les deux points dans la commande.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Appeler le `Disable-RemoteMonitoring` commande sans paramètres. Cette commande arrête l’envoi de commentaires. (Cela affecteront pas l’analyse locale.) Toutefois, la commande ne sera pas désactiver le redirecteur DNS et/ou désactiver les connexions internet. Cela doit être manuellement après avoir désactivé avec succès les commentaires.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Si vous voyez des erreurs ou des informations qui vous conduit à penser que la commande n’a pas réussie contactez Microsoft pour obtenir une assistance.  
  
Il n’existe pas de risque à en cours d’exécution le `Disable-RemoteMonitoring` commande plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler le matériel à l’aide de la Console d’administration &#40; Système de plateforme Analytique &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
[Contrôler le matériel à l’aide de vues système &#40; Système de plateforme Analytique &#41;](monitor-the-appliance-by-using-system-views.md)  
[Contrôler le matériel à l’aide de System Center Operations Manager &#40; Système de plateforme Analytique &#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
[Utilisez un redirecteur DNS pour résoudre les noms DNS de l’Appliance Non &#40; Système de plateforme Analytique &#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
