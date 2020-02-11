---
title: Commentaires sur la télémétrie
description: Envoyer des commentaires de télémétrie à Microsoft pour Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 639eb4e9e5c531e154b9eb7f91165af365bc519f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400365"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Envoyer des commentaires de télémétrie à Microsoft pour Analytics Platform System
Analytics Platform System possède une fonctionnalité de télémétrie facultative qui envoie les données de la console d’administration à Microsoft. 
  
> [!NOTE]  
> Dans cette version, Microsoft n’analyse pas activement les données de télémétrie. Les données sont collectées à des fins d’analyse uniquement.  
  
## <a name="privacy"></a>Nominative  
Pour fournir la protection maximale de la confidentialité, APS est fourni sans activer la télémétrie. Avant d’activer cette fonctionnalité, consultez tout d’abord la [déclaration de confidentialité Microsoft Analytics Platform System](https://go.microsoft.com/fwlink/?LinkId=400902). Pour vous abonner, exécutez le script PowerShell décrit ci-dessous.  
  
## <a name="enable"></a>Activer la télémétrie  
**Transfert DNS :** L’envoi de données de télémétrie à Microsoft requiert Analytics Platform System pour se connecter à Internet via un redirecteur DNS. Pour activer cette fonctionnalité, vous devez activer le transfert DNS sur tous les ordinateurs hôtes et les machines virtuelles de charge de travail. Appelez la `Enable-RemoteMonitoring` commande avec l' `SetupDnsForwarder` option permettant de configurer correctement le transfert DNS et d’activer la télémétrie. Appelez la `Enable-RemoteMonitoring` commande sans l' `SetupDnsForwarder` option lorsque le transfert DNS est déjà configuré et que vous souhaitez uniquement activer la surveillance des pulsations.  
  
> [!IMPORTANT]  
> L’activation du transfert DNS ouvre la connexion Internet pour tous les ordinateurs hôtes et toutes les machines virtuelles de charge de travail.  
  
#### <a name="to-enable-feedback"></a>Pour activer les commentaires  
  
1.  À l’aide d’un compte d’administrateur de domaine d’appliance, connectez-vous au nœud de contrôle (<strong>*appliance_domain*-CTL01</strong>) et ouvrez une invite de commandes en utilisant vos informations d’identification d’administrateur Windows.  
  
2.  Accédez au répertoire suivant : `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importer le module`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Pour importer, vous devez utiliser deux points dans la commande.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Appelez la `Enable-RemoteMonitoring` commande.  
  
    > [!NOTE]  
    > Le script suppose que la connexion Internet fonctionne correctement et ne valide pas la connexion Internet.  
  
    1.  La première fois que vous activez la télémétrie, utilisez la commande suivante pour vous assurer que tous les redirecteurs DNS sont correctement configurés. Dans cet exemple, remplacez l’adresse `xx.xx.xx.xx` IP transférée DNS par l’adresse IP du redirecteur DNS dans votre environnement.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Lorsque les redirecteurs DNS sont déjà configurés, par exemple la réactivation de la télémétrie précédemment désactivée, utilisez la commande suivante pour activer la télémétrie sans configurer le transfert DNS.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Vous serez invité à lire et à confirmer que les APS recueilleront des informations sur l’appliance. Il y aura un lien vers la déclaration de confidentialité APS que vous pouvez copier et coller dans n’importe quel navigateur Internet pour révision.  
  
6.  Entrez **Y** pour accepter et accepter les commentaires ou entrez **N** pour ne pas accepter.  
  
7.  Si vous avez entré **y** , une série de commandes s’exécutera, ce qui activera la fonctionnalité de télémétrie (et éventuellement le redirecteur DNS) sur votre appliance. Si vous voyez des erreurs ou des informations qui vous conduisent à croire que la commande n’a pas réussi à contacter CSS pour obtenir de l’aide.  
  
Si vous avez entré **n**, aucune commande n’est exécutée et la fonctionnalité n’est pas activée et il n’y a rien d’autre à faire.  
  
Il n’y a aucun effet sur `Enable-RemoteMonitoring` l’exécution de la commande plusieurs fois. Si le redirecteur DNS est déjà défini, vous obtiendrez un message d’avertissement indiquant que c’est le cas.  
  
## <a name="disable"></a>Désactiver la télémétrie  
La désactivation de la télémétrie entraînera l’arrêt de toutes les opérations qui communiquent les informations relatives à l’état de l’appliance au service d’analyse APS dans le Cloud.  
  
> [!IMPORTANT]  
> Si vous effectuez cette opération, vous ne désactivez pas votre redirecteur DNS ou votre connexion Internet qui peut être utilisée par d’autres fonctionnalités de l’appliance.  
  
#### <a name="to-disable-telemetry"></a>Pour désactiver la télémétrie  
  
1.  À l’aide d’un compte d’administrateur de domaine d’appliance, connectez-vous au nœud de contrôle (<strong>*appliance_domain*-CTL01</strong>) et ouvrez une fenêtre PowerShell avec des privilèges d’administrateur.  
  
2.  Accédez au répertoire suivant : `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importer le module`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Pour importer, vous devez utiliser deux points dans la commande.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Appelle la `Disable-RemoteMonitoring` commande sans paramètres. Cette commande arrête d’envoyer des commentaires. (Cela n’affecte pas l’analyse locale.) Toutefois, la commande ne désactive pas le redirecteur DNS et/ou ne désactive aucune connectivité Internet. Cette opération doit être effectuée manuellement après la désactivation réussie des commentaires.  
  
    **Exemple :**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Si vous voyez des erreurs ou des informations qui vous conduisent à croire que la commande n’a pas réussi à contacter CSS pour obtenir de l’aide.  
  
Il n’y a aucun effet sur `Disable-RemoteMonitoring` l’exécution de la commande plusieurs fois.  
  
## <a name="next-steps"></a>Étapes suivantes
Pour plus d'informations, consultez les pages suivantes :
- [Surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [Surveiller l’appliance à l’aide des vues système &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
- [Surveiller l’appliance à l’aide de System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [Utiliser un redirecteur DNS pour résoudre les noms DNS non-Appliance &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
