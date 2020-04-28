---
title: Configuration du réseau de l’appliance
description: L’appliance Analytics Platform System (APS) est créée et configurée avec un ensemble de correctifs d’adresses IP sur tous les serveurs et les appareils applicables à partir de l’usine du IHV. Lors de la remise de l’appareil, l’adresse IP externe (Ethernet) adressée doit être reconfigurée pour correspondre aux besoins spécifiques du centre de données du client.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: af892cbb43b42953732bda59d371e3e22855413b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401410"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Configuration du réseau d’appliances pour Analytics Platform System
L’appliance Analytics Platform System (APS) est créée et configurée avec un ensemble de correctifs d’adresses IP sur tous les serveurs et les appareils applicables à partir de l’usine du IHV. Lors de la remise de l’appareil, l’adresse IP externe (Ethernet) adressée doit être reconfigurée pour correspondre aux besoins spécifiques du centre de données du client.  
  
> [!NOTE]  
> PDW V1 nécessitait 8 adresses IP externes (*côté client*) pour fournir une connectivité externe à chacun des nœuds du rack de contrôle. PDW 2012 (v2) a amélioré les communications réseau en exposant chaque composant de l’appliance en externe via des adresses IP. Cette approche offre une conception plus robuste qui réduit les coûts et améliore la flexibilité, et améliore le déplacement des données, le chargement des données et l’intégration de Hadoop. Le nombre d’adresses IP requises dépend du nombre de nœuds dans l’appliance. Pour prendre en charge ce plus grand bloc d’adresses IP, le client doit configurer un sous-réseau distinct pour PDW. Au sein de ce sous-réseau, il y aura suffisamment d’espace d’adressage IP (jusqu’à 250 adresses) pour prendre en charge les composants d’un maximum de 5 racks PDW.  
  
La page **configuration du réseau** vous permet d’afficher les paramètres réseau en externe pour les nœuds de votre appliance système Analytics Platform. Cette page est en lecture seule.  
  
![Réseau des appliances DWConfig](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Pour mettre à jour la configuration réseau sur votre appliance  
Modifiez les adresses IP du domaine de la structure et du domaine de la charge de travail en modifiant le fichier **AplianceInfo. xml** , puis en exécutant le programme d’installation. Cette opération se fait hors connexion. Les régions PDW seront automatiquement arrêtées lors du changement d’adresse IP.  
  
> [!NOTE]  
> Les noms de domaine sont fournis au cours de l’installation et sont spécifiés sous la forme de 6 caractères alphanumériques au maximum, en commençant par une lettre. Un système de nommage fréquent crée un domaine d’infrastructure à partir de F, un domaine de charge de travail PDW commençant par P. Ce format est supposé dans les rubriques du fichier d’aide, mais n’est pas obligatoire. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Pour modifier les adresses IP du système de plateforme d’analyse  
  
1.  À l’aide de l’application **Bureau à distance** , connectez-vous à **HST01** à l’aide du compte d’administrateur de domaine de charge de travail.  
  
2.  Sur le nœud HST01, ouvrez le fichier d’informations de l’appliance sur **c:\pdwinst\media\AplianceInfo.xml**.  
  
    > [!NOTE]  
    > Si le fichier n’est pas présent, vous devrez peut-être créer un nouveau fichier.  
  
3.  Mettez à jour les valeurs IP Ethernet en fonction des besoins, puis enregistrez le fichier.  
  
4.  Dans une fenêtre d’invite de commandes, exécutez la commande d’installation suivante pour mettre à jour les adresses IP pour la région PDW, à l’aide des noms de domaine P/F/H et des mots de passe d’administrateur.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Références du fabricant  
Pour plus d’informations sur les appliances Dell, consultez :  
  
-   Instructions du commutateur PowerConnect Guide de référence de l’interface de commande du système de la [série Dell PowerConnect 6200](https://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   [Guide de l’utilisateur iDRAC/BMC Integrated Dell Remote Access Controller 7 (iDRAC7) version 1.30.30](https://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   **PDU rack Dell à racks**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le système de plateforme Configuration Manager &#40;Analytics&#41;](launch-the-configuration-manager.md)  
  
