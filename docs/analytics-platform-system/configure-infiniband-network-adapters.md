---
title: Configurer InfiniBand
description: Décrit comment configurer les cartes réseau InfiniBand sur un serveur client non-appareil pour se connecter au nœud de contrôle sur des Data Warehouse parallèles (PDW). Utilisez ces instructions pour la connectivité de base et pour la haute disponibilité, afin que le chargement, la sauvegarde et d’autres processus se connectent automatiquement au réseau InfiniBand actif.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 583d7617c0620d5d1ec24d60fbf10435a547616d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401291"
---
# <a name="configure-infiniband-network-adapters-for-analytics-platform-system"></a>Configurer des cartes réseau InfiniBand pour Analytics Platform System
Décrit comment configurer les cartes réseau InfiniBand sur un serveur client non-appareil pour se connecter au nœud de contrôle sur des Data Warehouse parallèles (PDW). Utilisez ces instructions pour la connectivité de base et pour la haute disponibilité, afin que le chargement, la sauvegarde et d’autres processus se connectent automatiquement au réseau InfiniBand actif.  
  
## <a name="Basics"></a>Description  
Ces instructions vous indiquent comment rechercher et définir les adresses IP InfiniBand et les masques de sous-réseau appropriés sur votre serveur connecté par InfiniBand. Elles expliquent également comment configurer votre serveur pour utiliser le DNS de l’appliance APS afin que votre connexion soit résolue en réseau InfiniBand actif.  
  
Pour la haute disponibilité, les APS possèdent deux réseaux InfiniBand, un actif et un passif. Chaque réseau InfiniBand possède une adresse IP différente pour le nœud de contrôle. Si le réseau InfiniBand actif tombe en panne, le réseau de l’InfiniBand passif devient le réseau actif. Dans ce cas, un script ou un processus se connecte automatiquement au réseau InfiniBand actif sans modifier les paramètres du script.  
  
Plus précisément, dans cet article, vous allez :  
  
1.  Recherchez les adresses IP InfiniBand des serveurs DNS APS (appliance_domain-AD01 et appliance_domain *-AD02). Pour ce faire, vous devez vous connecter aux serveurs AD01 et AD02 et obtenir les adresses IP pour chaque réseau InfiniBand. Les adresses IP InfiniBand sur le nœud AD sont les adresses IP DNS.  
  
2.  Configurez chaque carte réseau pour utiliser une adresse IP disponible sur les réseaux APS InfiniBand.  
  
    1.  Si vous avez deux cartes réseau InfiniBand, vous configurez une carte avec une adresse IP disponible dans le premier réseau InfiniBand, appelé TeamIB1, et l’autre adaptateur avec une adresse IP disponible dans le second réseau InfiniBand, appelé TeamIB2. Utilisez l’adresse IP appliance_domain-AD01 TeamIB1 comme serveur DNS préféré et l’adresse IP appliance_domain-AD02 TeamIB1 en tant que serveur DNS auxiliaire pour la carte réseau TeamIB1. Utilisez l’adresse IP appliance_domain-AD01 TeamIB2 comme serveur DNS préféré et l’adresse IP appliance_domain-AD02 TeamIB2 en tant que serveur DNS auxiliaire pour la carte réseau TeamIB2.  
  
    2.  Si vous n’avez qu’une seule carte réseau InfiniBand, vous configurez la carte avec une adresse IP disponible à partir de l’un des réseaux InfiniBand. Ensuite, vous configurez les serveurs DNS préférés et secondaires sur cet adaptateur à l’aide de appliance_domain-AD01 TeamIB1 et appliance_domain-AD02 TeamIB1, ou à l’aide de appliance_domain-AD01 TeamIB2 et appliance_domain-AD02 TeamIB2 selon le même réseau en tant qu’adaptateur configuré en tant que serveur préféré et les serveurs DNS secondaires, respectivement.  
  
3.  Configurez votre carte réseau InfiniBand pour utiliser les serveurs DNS APS pour résoudre votre connexion au réseau InfiniBand actif.  
  
    1.  Pour configurer cela, utilisez les paramètres TCP/IP avancés pour ajouter le suffixe DNS du domaine de l’appliance au début de la liste des suffixes DNS sur votre serveur client. Cela ne doit être configuré que sur l’une des cartes réseau. le paramètre s’applique aux deux adaptateurs.  
  
Après la configuration de vos cartes réseau InfiniBand, les processus clients peuvent se connecter au nœud de contrôle sur le réseau InfiniBand `PDW_region-SQLCTL01` en utilisant pour l’adresse du serveur. Votre serveur ajoute le suffixe DNS du système Analytics Platform, ou vous pouvez entrer l’adresse complète qui `PDW_region-SQLCTL01.appliance_domain.pdw.local`correspond à.  
  
Par exemple, si le nom de votre région PDW est MyPDW et que le nom de l’appliance est MyAPS, la spécification du serveur dwloader pour le chargement des données est l’une des suivantes :  
  
-   `dwloader -S MYPDW-SQLCTL01.MyAPS.pdw.local`  
  
-   `dwloader -S MYPDW-SQLCTL01`  
  
## <a name="BeforeBegin"></a>Avant de commencer  
  
### <a name="requirements"></a>Spécifications  
Vous avez besoin d’un compte de domaine d’appliance APS pour vous connecter au nœud AD01. Par exemple, F12345 * \administrator.  
  
Vous avez besoin d’un compte Windows sur le serveur client qui a l’autorisation de configurer les cartes réseau.  
  
### <a name="prerequisites"></a>Conditions préalables requises  
Ces instructions supposent que le serveur client est déjà monté en rack et branché au réseau de l’appliance InfiniBand. Pour obtenir des instructions sur la mise en rack et le câblage, consultez [acquérir et configurer un serveur de chargement](acquire-and-configure-loading-server.md).  
  
### <a name="general-remarks"></a>Remarques d'ordre général  
En utilisant SQLCTL01, le système de plateforme d’analyse DNS connecte votre serveur client au nœud de contrôle à l’aide du réseau InfiniBand actif. Cela s’applique uniquement à l’obtention de la connexion ; Si le réseau InfiniBand tombe en panne pendant une charge ou une sauvegarde, vous devez redémarrer le processus.  
  
Pour répondre aux besoins de votre entreprise, vous pouvez également joindre le serveur client à votre propre groupe de travail ou domaine Windows non-appliance.  
  
## <a name="Sec1"></a>Étape 1 : obtenir les paramètres réseau de l’appliance InfiniBand  
*Pour obtenir les paramètres réseau de l’appliance InfiniBand*  
  
1.  Connectez-vous au nœud AD01 de l’appliance à l’aide du compte appliance_domain \Administrateur.  
  
2.  Sur le nœud de l’appliance AD01, ouvrez le panneau de configuration, sélectionnez réseau et Internet, sélectionnez Centre réseau et partage *, puis sélectionnez Modifier les paramètres de la carte.  
  
3.  Dans la fenêtre Connexions réseau, cliquez avec le bouton droit sur Team IB1, puis sélectionnez Propriétés.  
  
    ![Connexions InfiniBand sur le nœud de gestion](media/network-teamib.png "Connexions InfiniBand sur le nœud de gestion")  
  
4.  À partir du Fenêtre Propriétés Protocole Internet version 4 (TCP/IPv4), notez les valeurs pour l' **adresse IP** et le **masque de sous-réseau**.  L’adresse IP du nœud ** _domaine\__ de l’appliance-ad01** est l’adresse IP du serveur DNS de la plateforme d’analyse.  
  
5.  Répétez les étapes 1-5 ci-dessus pour l’adaptateur TeamIB1 sur le serveur ** _\_Domain_-AD02** .  
  
    ![Propriétés du nœud de gestion PDW-InfiniBand 1](media/network-ip1-properties.png "Propriétés du nœud de gestion PDW-InfiniBand 1")  
  
6.  Cliquez sur Annuler pour fermer la fenêtre.  
  
7.  Recherchez une adresse IP inutilisée sur le réseau TeamIB1 et notez-la.  
  
    Pour rechercher une adresse IP inutilisée, ouvrez une fenêtre de commande et essayez d’envoyer une requête ping à des adresses IP au sein de la plage d’adresses de votre appliance. Dans cet exemple, l’adresse IP du réseau TeamIB1 est 172.16.14.30. Recherchez une adresse IP commençant par 172.16.14 qui n’est pas utilisée. Par exemple, à partir de la ligne de commande, entrez « ping 172.16.14.254 ». Si la demande Ping échoue, l’adresse IP est disponible.  
  
8.  Faites la même chose pour TeamIB2. Dans la fenêtre * Connexions réseau, cliquez avec le bouton droit sur Team IB2, puis sélectionnez Propriétés.  
  
9. À partir du Fenêtre Propriétés Protocole Internet version 4 (TCP/IPv4), notez les valeurs de l’adresse IP et du masque de sous-réseau pour TeamIB2.  
  
10. Répétez les étapes 8-9 ci-dessus pour l’adaptateur TeamIB2 sur le serveur appliance_domain-AD02.  
  
    ![Propriétés de TeamIB2](media/network-ip2-properties.png "Propriétés de TeamIB2")  
  
11. Recherchez une adresse IP inutilisée sur le réseau **TeamIB2** et notez-la.  
  
    Pour rechercher une adresse IP inutilisée, ouvrez une fenêtre de commande et essayez d’envoyer une requête ping à des adresses IP au sein de la plage d’adresses de votre appliance. Dans cet exemple, l’adresse IP du réseau TeamIB2 est 172.16.18.30. Recherchez une adresse IP commençant par 172.16.18 qui n’est pas utilisée. Par exemple, à partir de la ligne de commande, entrez « ping 172.16.18.254 ». Si la demande Ping échoue, l’adresse IP est disponible.  
  
## <a name="Sec2"></a>Étape 2 : configurer les paramètres de carte réseau InfiniBand sur votre serveur client  

### <a name="notes"></a>Notes  
  
-   Ces étapes vous montrent comment inscrire votre serveur auprès des serveurs DNS APS.  
  
-   Pour répondre à vos besoins en matière de réseau, vous pouvez également joindre le serveur client à votre propre groupe de travail ou domaine Windows non-appliance.  
  
-   Les instructions vous guident dans la configuration de deux cartes réseau sur chaque serveur.  Si vous n’avez qu’une seule carte réseau, choisissez l’un des réseaux à configurer sur la carte réseau, puis ajoutez la deuxième adresse IP DNS en tant que serveur DNS secondaire.  
  
### <a name="to-configure-the-infiniband-network-adapter-settings-on-your-client-server"></a>Pour configurer les paramètres de carte réseau InfiniBand sur votre serveur client  
  
1.  Connectez-vous en tant qu’administrateur Windows à votre serveur de chargement, de sauvegarde ou autre client sur le réseau de l’appliance InfiniBand.  
  
2.  Ouvrez le volet de contrôle *, sélectionnez Centre réseau et partage, puis sélectionnez Modifier les paramètres de la carte.  
  
### <a name="to-configure-the-first-network-adapter"></a>Pour configurer la première carte réseau  
  
1.  Dans la fenêtre Connexions réseau, cliquez avec le bouton droit sur l’un des emplacements réseau non identifiés pour la carte Mellanox, puis sélectionnez Propriétés.  
  
    ![Sélectionner les réseaux InfiniBand](media/network-connections.png "Sélectionner les réseaux InfiniBand")  
  
2.  Dans le Fenêtre Propriétés  
  
    1.  Sous l’onglet général, définissez l’adresse IP sur l’adresse IP que vous avez vérifiée comme étant libre dans le test ping pour TeamIB1. Pour les exemples de valeurs utilisés dans cet article, vous devez entrer 172.16.14.254.  
  
    2.  Définissez le masque de sous-réseau sur le masque de sous-réseau que vous avez écrit pour TeamIB1.  
  
    3.  Définissez le serveur DNS préféré sur l’adresse IP de TeamIB1 que vous avez notée précédemment à partir du nœud appliance_domain *-AD01.  
  
    4.  Définissez le serveur DNS de remplacement sur l’adresse IP de TeamIB1 que vous avez notée précédemment à partir du nœud appliance_domain *-AD02.  
  
        ![Propriétés de la carte réseau InfiniBand 1](media/network-ib1-properties.png "SQL_Server_PDW_Network_IB1_properties")  
  
    5.  Cliquez sur OK pour appliquer les modifications.  
  
### <a name="to-configure-the-second-network-adapter"></a>Pour configurer la deuxième carte réseau  
  
1.  Ignorez cette section si vous n’avez qu’une seule carte réseau.  
  
2.  Dans la fenêtre Connexions réseau, cliquez avec le bouton droit sur le deuxième emplacement réseau non identifié pour la carte Mellanox, puis sélectionnez Propriétés.  
  
    ![Sélectionner les réseaux InfiniBand](media/network-connections.png "Sélectionner les réseaux InfiniBand")  
  
3.  Dans le Fenêtre Propriétés  
  
    1.  Sous l’onglet général, définissez l’adresse IP sur l’adresse IP que vous avez vérifiée comme étant libre dans le test ping pour TeamIB2. Pour les exemples de valeurs utilisés dans cet article, vous devez entrer 172.16.18.254.  
  
    2.  Définissez le masque de sous-réseau sur le masque de sous-réseau que vous avez écrit pour TeamIB2.  
  
    3.  Définissez le serveur DNS préféré sur l’adresse IP de TeamIB2 que vous avez notée précédemment à partir du nœud appliance_domain *-AD01.  
  
    4.  Définissez le serveur DNS de remplacement sur l’adresse IP de TeamIB2 que vous avez notée précédemment à partir du nœud appliance_domain *-AD02.  
  
        > [!NOTE]  
        > Si vous n’avez qu’une seule carte réseau, configurez les serveurs DNS préférés et secondaires à l’aide de l’appliance AD01 TeamIB1 et de l’appliance AD02 TeamIB1 en tant que serveurs DNS préférés et secondaires, ou utilisez l’appliance AD01 TeamIB2 et l’appliance AD02 TeamIB2 en tant que serveurs DNS préférés et secondaires, selon que la machine virtuelle Active Directory a basculé.  
  
        ![Propriétés de la carte réseau InfiniBand 1](media/network-ib1-properties.png "Propriétés de la carte réseau InfiniBand 1")  
  
    5.  Cliquez sur OK pour appliquer les modifications.  
  
### <a name="to-configure-the-dns-suffix"></a>Pour configurer le suffixe DNS  
  
1.  Dans la fenêtre Connexions réseau, cliquez avec le bouton droit sur l’un des emplacements réseau de la carte Mellanox, puis sélectionnez Propriétés.  
  
2.  Cliquez sur Options avancées... bouton.  
  
3.  Dans la fenêtre paramètres TCP/IP avancés, si l’option Ajouter ces suffixes DNS (dans l’ordre) n’est pas grisée, cochez la case «ajouter ces suffixes DNS (dans l’ordre) :, sélectionnez le suffixe de domaine de l’appliance, puis cliquez sur Ajouter.... Le suffixe de domaine de l’appliance est`appliance_domain.local`  
  
4.  Si l’option Ajouter ces suffixes DNS (dans l’ordre) est grisée, vous pouvez ajouter le domaine APS à ce serveur en modifiant la clé de Registre HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\Windows NT\DNSClient.  
  
    ![Paramètres TCP/IP](media/network-tcpip.png "Paramètres TCP/IP")  
  
5.  Pour accélérer la résolution des adresses, nous vous recommandons de déplacer le suffixe de l’appliance vers le haut de la liste.  
  
6.  Cliquez sur OK.  
  
7.  Vous pouvez maintenant vous connecter au réseau de l’appliance InfiniBand à `PDW_region-SQLCTL01.appliance_domain.local`l’aide de `appliance_domain-SQLCTL01`, ou simplement. La connexion peut être établie plus rapidement si vous vous connectez avec le nom complet et le suffixe DNS.  
  
    Exemples pour une appliance nommée MyAPS avec une région MyPDW PDW :  
  
    -   MyPDW-SQLCTL01. MyAPS. local  
  
    -   MyPDW-SQLCTL01  
  
## <a name="see-also"></a>Voir aussi  
[Acquérir et configurer un serveur de chargement](acquire-and-configure-loading-server.md)  
  
