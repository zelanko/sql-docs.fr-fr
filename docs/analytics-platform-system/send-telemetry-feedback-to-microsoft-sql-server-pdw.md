---
title: Commentaires de télémétrie - Analytique Platform System | Microsoft Docs
description: Envoyer des commentaires de télémétrie à Microsoft pour système de plateforme d’Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 442505d470d1c7b7a82a02610d650d9f0b8c8d07
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678378"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Envoyer des commentaires de télémétrie à Microsoft pour système de plateforme d’Analytique
Analytique Platform System possède une fonctionnalité de télémétrie facultatif qui envoie des données de la Console d’administration à Microsoft. 
  
> [!NOTE]  
> Dans cette version, Microsoft ne surveille pas activement les données de télémétrie. Les données sont collectées uniquement à des fins d’analyse.  
  
## <a name="privacy"></a>Confidentialité  
Pour fournir la protection des données personnelles maximale, points d’accès est fourni sans activation de la télémétrie. Avant d’activer cette fonctionnalité, tout d’abord examiner la [déclaration de confidentialité de Microsoft Analytique Platform System](https://go.microsoft.com/fwlink/?LinkId=400902). Pour vous abonner, exécutez le script PowerShell décrit ci-dessous.  
  
## <a name="enable"></a>Activer la télémétrie  
**Transfert DNS :** Envoi de données de télémétrie à Microsoft requiert Analytique Platform System pour se connecter à internet via un redirecteur DNS. Pour activer cette fonctionnalité, vous devez activer la redirection DNS sur tous les hôtes et les charges de travail des machines virtuelles. Appeler le `Enable-RemoteMonitoring` avec la `SetupDnsForwarder` option pour configurer la redirection DNS et activer la télémétrie correctement. Appeler le `Enable-RemoteMonitoring` commande sans le `SetupDnsForwarder` option lors de la redirection DNS est déjà configurée et vous souhaitez uniquement activer l’analyse de pulsation.  
  
> [!IMPORTANT]  
> Activation du transfert de DNS, la connexion internet pour tous les hôtes et les charges de travail des machines virtuelles s’ouvre.  
  
#### <a name="to-enable-feedback"></a>Pour activer les commentaires  
  
1.  À l’aide d’un compte administrateur de domaine appliance, connectez-vous au nœud de contrôle (<strong>*appliance_domain*-CTL01</strong>) et ouvrez une invite de commandes à l’aide de vos informations d’identification administrateur de Windows.  
  
2.  Accédez au répertoire suivant : `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importez le module `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Pour importer vous devez utiliser les deux points dans la commande.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Appeler le `Enable-RemoteMonitoring` commande.  
  
    > [!NOTE]  
    > Le script suppose que la connexion internet fonctionne correctement et ne valide pas la connexion internet.  
  
    1.  La première fois que vous activez la télémétrie, utilisez la commande suivante pour vous assurer de tous les redirecteurs DNS sont correctement configurés. Dans cet exemple, remplacez l’adresse IP de DNS transférés `xx.xx.xx.xx` avec l’adresse IP du redirecteur DNS dans votre environnement.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Lorsque des redirecteurs DNS sont déjà configurés, telles que la réactivation précédemment désactivé la télémétrie, utilisez la commande suivante pour activer la télémétrie sans configurer le transfert de DNS.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Vous devrez lire et accepter que APS recueillera des informations sur l’appliance. Il y aura un lien vers la déclaration de confidentialité de points d’accès que vous pouvez copier et coller dans n’importe quel navigateur internet pour révision.  
  
6.  Entrez **Y** pour accepter et s’abonner à des commentaires ou entrez **N** n’accepte ne pas.  
  
7.  Si vous avez entré **Y** il y aura une série de commandes qui seront exécutées, et ce qui permettra la télémétrie (et éventuellement le redirecteur DNS) fonctionnalité sur votre appliance. Si vous voyez des erreurs ou des informations qui vous amène à penser que la commande n’a pas réussie contactez CSS.  
  
Si vous avez entré **N**, aucune commande n’est exécutée et la fonctionnalité ne sera pas activée et il n’est rien d’autre à faire.  
  
Il n’existe aucun risque à en cours d’exécution le `Enable-RemoteMonitoring` commande plusieurs fois. Si le redirecteur DNS est déjà défini, vous obtiendrez un message d’avertissement qui indique qui est le cas.  
  
## <a name="disable"></a>Désactiver la télémétrie  
Désactivation de la télémétrie s’arrête toutes les opérations qui communiquent des informations sur l’état du matériel et les points d’accès de surveillance de service dans le cloud.  
  
> [!IMPORTANT]  
> Cette opération désactivera pas votre redirecteur DNS ou une connexion internet qui peut être en cours d’utilisation par d’autres fonctionnalités dans l’appliance.  
  
#### <a name="to-disable-telemetry"></a>Pour désactiver la télémétrie  
  
1.  À l’aide d’un compte administrateur de domaine appliance, connectez-vous au nœud de contrôle (<strong>*appliance_domain*-CTL01</strong>) et ouvrez une fenêtre PowerShell avec des privilèges d’administrateur.  
  
2.  Accédez au répertoire suivant : `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importez le module `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Pour importer vous devez utiliser les deux points dans la commande.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Appeler le `Disable-RemoteMonitoring` commande sans paramètres. Cette commande arrête l’envoi des commentaires. (Cela n’affecte pas monitoring local.) Toutefois, la commande ne sera pas désactiver le redirecteur DNS et/ou de désactiver la connexion internet. Cela doit être effectuée manuellement après avoir désactivé avec succès des commentaires.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Si vous voyez des erreurs ou des informations qui vous amène à penser que la commande n’a pas réussie contactez CSS.  
  
Il n’existe aucun risque à en cours d’exécution le `Disable-RemoteMonitoring` commande plusieurs fois.  
  
## <a name="next-steps"></a>Étapes suivantes
Pour plus d'informations, consultez :
- [Surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [Surveiller l’Appliance à l’aide de vues système &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
- [Surveiller l’Appliance à l’aide de System Center Operations Manager &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [Utiliser un redirecteur DNS pour résoudre les noms DNS de Non-Appliance &#40;Analytique Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
