---
title: Configurer un groupe de disponibilité et une instance de cluster de basculement avec plusieurs sous-réseaux (Linux)
description: Apprenez à configurer des groupes de disponibilité Always On et des instances de cluster de basculement avec plusieurs sous-réseaux pour SQL Server sur Linux.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/01/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: d6cd6b4cdd25c6da0a7d034e2f980ad583a6561b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901551"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Configurer Pacemaker pour les groupes de disponibilité Always On et les instances de cluster de basculement

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Quand un groupe de disponibilité Always On ou une instance de cluster de basculement (FCI) s’étend sur plusieurs sites, chaque site dispose généralement de son propre réseau. Cela signifie souvent que chaque site a sa propre adresse IP. Par exemple, les adresses du site A commencent par 192.168.1.*x* et les adresses du site B par 192.168.2.*x*, où *x* est la partie de l’adresse IP qui est unique sur le serveur. Sans une sorte de routage mis en place au niveau de la couche de mise en réseau, ces serveurs ne pourront pas communiquer entre eux. Il existe deux façons de gérer ce scénario : configurer un réseau qui sert de pont entre les deux sous-réseaux, connu sous le nom de réseau local virtuel, ou configurer le routage entre les sous-réseaux.

## <a name="vlan-based-solution"></a>Solution basée sur un réseau local virtuel
 
**Condition préalable** : Dans le cas d’une solution basée sur un réseau local virtuel, chaque serveur participant à un groupe de disponibilité ou à une instance de cluster de basculement (FCI) a besoin de deux cartes réseau (NIC) pour une disponibilité appropriée (une carte réseau à deux ports est un point de défaillance unique sur un serveur physique), afin qu’il soit possible d’attribuer des adresses IP sur son sous-réseau natif ainsi que d’une sur le réseau local virtuel. Cela s’ajoute à tout autre réseau nécessaire tel qu’iSCSI, qui a également besoin de son propre réseau.

La création d’adresses IP pour le groupe de disponibilité ou l’instance de cluster de basculement (FCI) est effectuée sur le réseau local virtuel. Dans l’exemple suivant, le réseau local virtuel a un sous-réseau 192.168.3.*x*, si bien que l’adresse IP créée pour le groupe de disponibilité ou pour l’instance de cluster de basculement (FCI) est 192.168.3.104. Il n’y a rien de plus à configurer, car une seule adresse IP est attribuée au groupe de disponibilité ou à l’instance de cluster de basculement (FCI).

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Configuration avec Pacemaker

Dans le monde de Windows, un cluster de basculement Windows Server (WSFC) prend en charge en mode natif plusieurs sous-réseaux et gère plusieurs adresses IP via une dépendance OU sur l’adresse IP. Sur Linux, il n’y a pas de dépendance OU, mais il existe un moyen d’obtenir un sous-réseau multiple approprié de manière native avec Pacemaker, comme indiqué dans ce qui suit. Pour ce faire, il ne suffit pas d’utiliser la ligne de commande Pacemaker normale pour modifier une ressource. Vous devez modifier la base d’informations de cluster (CIB). La base d’informations de cluster est un fichier XML avec la configuration Pacemaker.

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Mettez à jour la base d’informations de cluster

1.  Exportez la base d’informations de cluster.

    **Red Hat Enterprise Linux (RHEL) et Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Où *filename* est le nom que vous souhaitez donner à la base d’informations de cluster.

2.  Modifiez le fichier qui a été créé. Recherchez la section `<resources>`. Vous voyez les différentes ressources qui ont été créées pour le groupe de disponibilité ou pour l’instance de cluster de basculement (FCI). Trouvez celle associée à l'adresse IP. Ajoutez une section `<instance attributes>` avec les informations relatives à la deuxième adresse IP, soit au-dessus, soit en dessous de l’adresse existante, mais avant `<operations>`. Cela ressemble à la syntaxe suivante :

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    où *NameForAttribute* est le nom unique de cet attribut, *Score* est le numéro affecté à l’attribut, qui doit être supérieur au sous-réseau principal, *RuleName*est le nom de la règle, *ExpressionName* est le nom de l’expression, *NodeNameInSubnet2* est le nom du nœud dans l’autre sous-réseau, *NameForSecondIP* est le nom associé à la deuxième adresse IP, *IPAddress* est l’adresse IP du deuxième sous-réseau, *NameForSecondIPNetmask* est le nom associé au masque réseau et *Netmask* est le masque réseau pour le deuxième sous-réseau.
    
    Consultez l’exemple ci-dessous.
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  Importez le CIB modifié et reconfigurez Pacemaker.

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

1.  Une fois que le CIB est appliqué avec la configuration mise à jour, effectuez un test Ping du nom DNS associé à la ressource d’adresse IP dans Pacemaker. Il doit refléter l’adresse IP associée au sous-réseau qui héberge actuellement le groupe de disponibilité ou l’instance de cluster de basculement (FCI).
2.  Faites basculer le groupe de disponibilité ou l’instance de cluster de basculement (FCI) sur l’autre sous-réseau.
3.  Une fois que le groupe de disponibilité ou l’instance de cluster de basculement (FCI) est entièrement en ligne, effectuez un test Ping du nom DNS associé à l’adresse IP. Il doit refléter l’adresse IP dans le deuxième sous-réseau.
4.  Si vous le souhaitez, vous pouvez faire basculer à nouveau le groupe de disponibilité ou l’instance de cluster de basculement (FCI) vers le sous-réseau d’origine.
