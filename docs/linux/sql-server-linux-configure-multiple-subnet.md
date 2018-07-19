---
title: Configurer le sous-réseau de plusieurs groupes de disponibilité AlwaysOn et les instances de cluster de basculement sur Linux | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/1/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 612ac9c684fa8e0383981a32a94cf82d8ec68678
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001694"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Configurer plusieurs sous-réseaux groupes de disponibilité AlwaysOn et les instances de cluster de basculement

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Quand une instance de cluster toujours sur groupe de disponibilité (AG) ou le basculement (FCI) s’étend sur plusieurs sites, chaque site généralement a sa propre mise en réseau. Souvent, cela signifie que chaque site dispose de sa propre adresse IP. Par exemple, les adresses du Site A commencent par 192.168.1. *x* et les adresses du Site B commencent par 192.168.2. *x*, où *x* est la partie de l’adresse IP qui est unique sur le serveur. Sans une sorte de routage en place au niveau de la couche de mise en réseau, ces serveurs ne seront pas en mesure de communiquer entre eux. Il existe deux façons de gérer ce scénario : configurer un réseau qui établit un pont entre les deux sous-réseaux différents, appelés un réseau local virtuel, ou configurer le routage entre les sous-réseaux.

## <a name="vlan-based-solution"></a>Solution basée sur le réseau local virtuel
 
**Configuration requise**: solution pour un VLAN-based, chaque serveur impliqué dans un groupe de disponibilité ou une instance FCI a besoin de deux cartes réseau (NIC) pour une disponibilité (un double port de carte réseau serait un point unique de défaillance sur un serveur physique), afin qu’il puisse être attribué des adresses IP sur son sous-réseau natif ainsi que l’autre sur le réseau local virtuel. Il s’agit en plus de tout autre besoin de réseau, telle qu’iSCSI, qui doit également son propre réseau.

La création d’adresse IP pour le groupe de disponibilité ou une instance FCI est effectuée sur le réseau local virtuel. Dans l’exemple suivant, le réseau local virtuel possède un sous-réseau de 192.168.3. *x*, de sorte que l’adresse IP créée pour le groupe de disponibilité ou une instance FCI est 192.168.3.104. Aucune opération supplémentaire ne doit être configuré, dans la mesure où il existe une seule adresse IP affectée au groupe de disponibilité ou de l’ICF.

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Configuration de Pacemaker

Dans le monde de Windows, un Cluster de basculement de Windows Server (WSFC) en mode natif prend en charge de plusieurs sous-réseaux et gère plusieurs adresses IP via une dépendance OR sur l’adresse IP. Sur Linux, il n’existe aucune dépendance OR, mais il existe un moyen pour obtenir un sous-réseau multi approprié en mode natif avec Pacemaker, comme indiqué par ce qui suit. Pour ce faire, vous ne pouvez pas simplement à l’aide de la ligne de commande Pacemaker normale pour modifier une ressource. Vous devez modifier les informations du cluster base (CIM). Le CIM est un fichier XML avec la configuration de Pacemaker.

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Mettre à jour le CIM

1.  Exporter le CIM.

    **Red Hat Enterprise Linux (RHEL) et Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Où *filename* est le nom que vous souhaitez appeler le CIM.

2.  Modifiez le fichier qui a été généré. Recherchez le `<resources>` section. Vous verrez les différentes ressources qui ont été créés pour le groupe de disponibilité ou une instance FCI. Recherchez celui associé à l’adresse IP. Ajouter un `<instance attributes>` section avec les informations pour la deuxième adresse IP supérieure ou inférieure à celle existant, mais avant que `<operations>`. Il est similaire à la syntaxe suivante :

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    où *NameForAttribute* est le nom unique pour cet attribut, *Score* est le numéro attribué à l’attribut, qui doit être supérieure au sous-réseau principal, *RuleName*est le nom de la règle, *ExpressionName* est le nom de l’expression, *NodeNameInSubnet2* est le nom du nœud dans le second sous-réseau *NameForSecondIP* est le nom associé à la deuxième adresse IP, *IPAddress* est l’adresse IP pour le deuxième sous-réseau, *NameForSecondIPNetmask* est le nom associé avec le masque de réseau, et *Masque réseau* est le masque de réseau pour le deuxième sous-réseau.
    
    Voici un exemple.
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  Importer la CIB modifié et reconfigurer Pacemaker.

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    où *filename* est le nom du fichier CIB avec les informations d’adresse IP modifiées.

### <a name="check-and-verify-failover"></a>Vérifiez et vérifier le basculement

1.  Une fois le CIM est correctement appliqué avec la configuration mise à jour, ping sur le nom DNS associé à la ressource d’adresse IP dans Pacemaker. Il doit refléter l’adresse IP associé au sous-réseau qui héberge actuellement le groupe de disponibilité ou une instance FCI.
2.  Échec du groupe de disponibilité ou une instance FCI à l’autre sous-réseau.
3.  Une fois le groupe de disponibilité ou une instance FCI entièrement en ligne, exécutez ping sur le nom DNS associé à l’adresse IP. Il doit refléter l’adresse IP dans le deuxième sous-réseau.
4.  Si vous le souhaitez, restaurez le groupe de disponibilité ou une instance FCI le sous-réseau d’origine.
