---
title: Configurer un groupe de disponibilité et une instance de cluster de basculement avec plusieurs sous-réseaux (Linux)
description: Apprenez à configurer des groupes de disponibilité Always On et des instances de cluster de basculement avec plusieurs sous-réseaux pour SQL Server sur Linux.
ms.custom: seo-lt-2019
author: liweiSecurity
ms.author: liweiyin
ms.reviewer: VanMSFT
ms.date: 07/28/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 5abe1d99f753e0f41ca74a0864079293800dc1df
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362968"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Configurer Pacemaker pour les groupes de disponibilité Always On et les instances de cluster de basculement

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Quand un groupe de disponibilité Always On ou une instance de cluster de basculement (FCI) s’étend sur plusieurs sites, chaque site dispose généralement de son propre réseau. Cela signifie souvent que chaque site a sa propre adresse IP. Par exemple, les adresses du site A commencent par 192.168.1.*x* et les adresses du site B par 192.168.2.*x*, où *x* est la partie de l’adresse IP qui est unique sur le serveur. Sans une sorte de routage mis en place au niveau de la couche de mise en réseau, ces serveurs ne pourront pas communiquer entre eux. Il existe deux façons de gérer ce scénario : configurer un réseau qui sert de pont entre les deux sous-réseaux, connu sous le nom de réseau local virtuel, ou configurer le routage entre les sous-réseaux.

## <a name="vlan-based-solution"></a>Solution basée sur un réseau local virtuel
 
**Condition préalable** : Dans le cas d’une solution basée sur un réseau local virtuel, chaque serveur participant à un groupe de disponibilité ou à une instance de cluster de basculement (FCI) a besoin de deux cartes réseau (NIC) pour une disponibilité appropriée (une carte réseau à deux ports est un point de défaillance unique sur un serveur physique), afin qu’il soit possible d’attribuer des adresses IP sur son sous-réseau natif ainsi que d’une sur le réseau local virtuel. Cela s’ajoute à tout autre réseau nécessaire tel qu’iSCSI, qui a également besoin de son propre réseau.

La création d’adresses IP pour le groupe de disponibilité ou l’instance de cluster de basculement (FCI) est effectuée sur le réseau local virtuel. Dans l’exemple suivant, le réseau local virtuel a un sous-réseau 192.168.3.*x*, si bien que l’adresse IP créée pour le groupe de disponibilité ou pour l’instance de cluster de basculement (FCI) est 192.168.3.104. Il n’y a rien de plus à configurer, car une seule adresse IP est attribuée au groupe de disponibilité ou à l’instance de cluster de basculement (FCI).

![Configurer plusieurs sous-réseaux 01](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Configuration avec Pacemaker

Dans le monde de Windows, un cluster de basculement Windows Server (WSFC) prend en charge en mode natif plusieurs sous-réseaux et gère plusieurs adresses IP via une dépendance OU sur l’adresse IP. Sur Linux, il n’y a pas de dépendance OU, mais il existe un moyen d’obtenir un sous-réseau multiple approprié de manière native avec Pacemaker, comme indiqué dans ce qui suit. Pour ce faire, il ne suffit pas d’utiliser la ligne de commande Pacemaker normale pour modifier une ressource. Vous devez modifier la base d’informations de cluster (CIB). La base d’informations de cluster est un fichier XML avec la configuration Pacemaker.

![Configurer plusieurs sous-réseaux 02](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Mettez à jour la base d’informations de cluster

1. Exportez la base d’informations de cluster.

    **Red Hat Enterprise Linux (RHEL) et Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Où *filename* est le nom que vous souhaitez donner à la base d’informations de cluster.

2. Modifiez le fichier qui a été créé. Recherchez la section `<resources>`. Vous voyez les différentes ressources qui ont été créées pour le groupe de disponibilité ou pour l’instance de cluster de basculement (FCI). Trouvez celle associée à l'adresse IP. Ajoutez une section `<instance attributes>` avec les informations relatives à la deuxième adresse IP, soit au-dessus, soit en dessous de l’adresse existante, mais avant `<operations>`. Cela ressemble à la syntaxe suivante :

    ```xml
    <instance attributes id="<NameForAttribute>">
        <nvpair id="<NameForIP>" name="ip" value="<IPAddress>"/>
    </instance attributes>
    ```
    
    où *NameForAttribute* est le nom unique de cet attribut, *NameForIP* est le nom associé à l’adresse IP, et *IPAddress* est l’adresse IP du deuxième sous-réseau.
    
    Consultez l’exemple ci-dessous.
    
    ```xml
    <instance attributes id="virtualip-instance_attributes">
        <nvpair id="virtualip-instance_attributes-ip" name="ip" value="192.168.1.102"/>
    </instance attributes>
    ```
    
    Par défaut, il n’y a qu’une seule <instance/> dans le fichier XML CIB exporté. Si vous avez deux sous-réseaux, vous devez avoir deux entrées <instance/>.
    Voici un exemple avec des entrées pour deux sous-réseaux.
    
    ```xml
    <instance attributes id="virtualip-instance_attributes1">
        <rule id="Subnet1-IP" score="INFINITY" boolean-op="or">
            <expression id="Subnet1-Node1" attribute="#uname" operation="eq" value="Node1" />
            <expression id="Subnet1-Node2" attribute="#uname" operation="eq" value="Node2" />
        </rule>
        <nvpair id="IP-In-Subnet1" name="ip" value="192.168.1.102"/>
    </instance attributes>
    <instance attributes id="virtualip-instance_attributes2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node1" attribute="#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet2" name="ip" value="192.168.2.102"/>
    </instance attributes>
    ```
   
   « boolean-op= » ou «» est utilisé lorsque le sous-réseau comprend plusieurs serveurs.


3. Importez le CIB modifié et reconfigurez Pacemaker.

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    où *filename* est le nom du fichier CIB avec les informations d’adresse IP modifiées.

### <a name="check-and-verify-failover"></a>Vérifier le basculement

1. Une fois que le CIB est appliqué avec la configuration mise à jour, effectuez un test Ping du nom DNS associé à la ressource d’adresse IP dans Pacemaker. Il doit refléter l’adresse IP associée au sous-réseau qui héberge actuellement le groupe de disponibilité ou l’instance de cluster de basculement (FCI).

2. Faites basculer le groupe de disponibilité ou l’instance de cluster de basculement (FCI) sur l’autre sous-réseau.

3. Une fois que le groupe de disponibilité ou l’instance de cluster de basculement (FCI) est entièrement en ligne, effectuez un test Ping du nom DNS associé à l’adresse IP. Il doit refléter l’adresse IP dans le deuxième sous-réseau.

4. Si vous le souhaitez, vous pouvez faire basculer à nouveau le groupe de disponibilité ou l’instance de cluster de basculement (FCI) vers le sous-réseau d’origine.

Voici un post CSS qui montre comment configurer le CIB pour trois sous-réseaux : [Configure multiple-subnet AlwaysOn Availability Group by modifying CIB](https://techcommunity.microsoft.com/t5/sql-server-support/configure-multiple-subnet-alwayson-availability-groups-by/ba-p/1544838).
