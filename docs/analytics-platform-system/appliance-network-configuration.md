---
title: "Configuration réseau (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e2b9abe-963d-479b-a4a7-1739fcb3e249
caps.latest.revision: "27"
ms.openlocfilehash: e24ed8e992591d08628ffeb14c30a47d7fa5b54a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="appliance-network-configuration"></a>Configuration réseau
L’application SQL Server PDW est conçue et configurée avec un ensemble de correction des adresses IP dans l’ensemble de tous les serveurs et appareils applicables à partir de l’usine du fabricant de matériel. Lors de la livraison de l’application, l’adresse IP externe (Ethernet) traité doit être reconfiguré pour répondre aux besoins de centre de données du client spécifique.  
  
> [!NOTE]  
> PDW V1 requis 8 IP externe (*face au client*) des adresses pour fournir une connectivité externe à chaque contrôle rack de nœuds. PDW 2012 (V2) améliorée des communications réseau en exposant chaque composant de l’application en externe via les adresses IP. Cette approche fournit une conception plus robuste, ce qui réduit les coûts et augmente la flexibilité et améliore le déplacement des données, le chargement de données et l’intégration de Hadoop. Le nombre d’adresses IP nécessaire varie selon le nombre de nœuds dans l’application et la présence de fonctionnalités, telles que HDInsight. Pour prendre en compte ce plus grand bloc d’adresses IP, le client doit configurer un sous-réseau distinct pour PDW. Dans ce sous-réseau, il y a un espace d’adressage IP (jusqu'à 250 adresses) pour prendre en charge les composants de jusqu'à 5 racks PDW.  
  
Le **Configuration réseau** page permet de vous permet d’afficher les paramètres de réseau externe pour les nœuds sur votre appliance Analytique plateforme système. Cette page est en lecture seule.  
  
![Réseau des appliances DWConfig](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Pour mettre à jour la configuration du réseau sur votre appliance  
Modifier les adresses IP de l’ensemble fibre optique domaine, domaine de la charge de travail et HDInsight domaines en modifiant le **AplianceInfo.xml** fichier, puis vous exécutez le programme d’installation. Il s’agit d’une opération hors connexion. HDInsight (le cas échéant) et PDW régions seront automatiquement arrêtées pendant la modification d’adresse IP.  
  
> [!NOTE]  
> Les noms de domaine sont fournis lors de l’installation et sont spécifiés comme jusqu'à 6 caractères alphanumériques, commençant par une lettre. Un système d’affectation de noms fréquent crée un domaine de l’ensemble fibre optique en commençant par F, un domaine de la charge de travail PDW commençant par P et un domaine HDInsight commençant par H. Ce format est présumé tout au long de l’aide du fichier, mais n’est pas obligatoire. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Pour modifier les adresses IP du système de plateforme Analytique  
  
1.  À l’aide de la **Bureau à distance** application, se connecter à **HST01** à l’aide du compte administrateur de domaine de la charge de travail.  
  
2.  Sur le nœud HST01, ouvrez le fichier info appliance **c:\pdwinst\media\AplianceInfo.xml**.  
  
    > [!NOTE]  
    > Si le fichier n’est pas présent, un nouveau fichier peut doivent être créés.  
  
3.  Mettre à jour les valeurs Ethernet IP en fonction des besoins et enregistrez le fichier.  
  
4.  Dans une fenêtre d’invite de commandes, exécutez la commande suivante pour mettre à jour les adresses IP de la région PDW, en utilisant les noms de domaine P/F/H et les mots de passe d’administrateur.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Références du fabricant  
Pour plus d’informations sur les équipements Dell, consultez :  
  
-   Instructions de commutateur PowerConnect [Guide de référence du système de la série Dell PowerConnect 6200 CLI](http://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC [Guide de l’utilisateur de la Version 1.30.30 intégré Dell distant accès contrôleur 7 (iDRAC7)](http://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU **Dell limitées Rack PDU**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41;](launch-the-configuration-manager.md)  
  
