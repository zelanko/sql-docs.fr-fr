---
title: Configurer un serveur Linux SQL machine virtuelle dans Azure | Documents Microsoft
description: "Ce didacticiel montre comment créer un ordinateur virtuel de Linux SQL Server 2017 dans Azure."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 222e23b2-51e7-429b-b8e5-61e0ebe7df9b
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 0470622b0fe5a8835213617a4fc2e8c74f674873
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-linux-sql-server-2017-virtual-machine-with-the-azure-portal"></a>Créer un ordinateur virtuel de Linux SQL Server 2017 avec le portail Azure

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Azure fournit des images de machine virtuelle Linux qui ont installé de SQL Server 2017 RC2. Cette rubrique fournit une brève présentation sur la façon d’utiliser le portail Azure pour créer une machine virtuelle Linux SQL Server. 

## <a name="create-a-linux-vm-with-sql-server-installed"></a>Créer une VM Linux avec SQL Server installé

Ouvrez le [portail Azure](https://portal.azure.com/).

1. Cliquez sur **nouveau** sur la gauche.

1. Dans le **nouveau** panneau, cliquez sur **de calcul**.

1. Cliquez sur **voir tous les** à côté du **les applications proposées** titre.

   ![Consultez toutes les images de machine virtuelle](./media/sql-server-linux-azure-virtual-machine/azure-compute-blade.png)

1. Dans la zone de recherche, tapez **SQL Server 2017**, puis appuyez sur **entrée** pour démarrer la recherche.

    ![Filtre de recherche pour les images de machine virtuelle 2017 de SQL Server](./media/sql-server-linux-azure-virtual-machine/searchfilter.png)

    > [!TIP]
    > Ce filtre montre les images de machine virtuelle Linux disponibles pour SQL Server 2017. Au fil du temps, les images de SQL Server 2017 pour les autres distributions Linux prises en charge sont répertoriés. Vous pouvez cliquer également sur cette [lien](https://ms.portal.azure.com/#blade/Microsoft_Azure_Marketplace/GalleryFeaturedMenuItemBlade/selectedMenuItemId/home/searchQuery/sql%20server%202017) pour accéder directement aux résultats de recherche pour SQL Server 2017. 

1. Sélectionnez une image de SQL Server 2017 dans les résultats de recherche.

1. Cliquez sur **Créer**.

1. Sur le **notions de base** panneau, renseignez les détails de votre VM Linux. 

    ![Panneau de principes de base](./media/sql-server-linux-azure-virtual-machine/basics.png)

    > [!Note]
    > Vous avez le choix de l’utilisation d’une clé publique SSH ou un mot de passe pour l’authentification. SSH est plus sûre. Pour obtenir des instructions sur la façon de générer une clé SSH, consultez [créer SSH clés sur Mac et Linux pour les machines virtuelles dans Azure Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-mac-create-ssh-keys). 

1. Cliquez sur **OK**.

1. Sur le **taille** panneau, choisissez une taille de machine. Développement et test fonctionnel, nous vous recommandons une taille de machine virtuelle **DS2** ou une version ultérieure. Test des performances, utilisez **DS13** ou une version ultérieure.

    ![Choisissez une taille de machine virtuelle](./media/sql-server-linux-azure-virtual-machine/vmsizes.png)

    Pour voir les autres tailles, sélectionnez **afficher toutes les**. Pour plus d’informations sur les tailles de machine virtuelle, consultez [tailles de Linux VM](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-sizes).

1. Cliquez sur **Sélectionner**.

1. Sur le **paramètres** panneau, vous pouvez apporter des modifications aux paramètres ou conservez les paramètres par défaut.

1. Cliquez sur **OK**.

1. Sur le **Résumé** , cliquez sur **OK** pour créer la machine virtuelle.

> [!NOTE]
> La machine virtuelle Azure préconfigure le pare-feu pour ouvrir le port SQL Server 1433 pour les connexions distantes. Mais, pour se connecter à distance, vous devez également ajouter une règle de groupe de sécurité réseau comme décrit dans la section suivante.

## <a id="remote"></a>Configurer des connexions à distance

Pour être en mesure de se connecter à distance à SQL Server sur une machine virtuelle Azure, vous devez configurer une règle de trafic entrant sur le groupe de sécurité réseau. La règle autorise le trafic sur le port sur lequel SQL Server écoute (valeur par défaut 1433). Les étapes suivantes montrent comment utiliser le portail Azure pour cette étape. 

1. Dans le portail, sélectionnez **virtuels**, puis sélectionnez votre machine virtuelle SQL Server.

1. Dans la liste des propriétés, sélectionnez **interfaces réseau**.

1. Sélectionnez ensuite l’Interface réseau pour votre machine virtuelle.

    ![Interfaces réseau](./media/sql-server-linux-azure-virtual-machine/networkinterfaces.png)

1. Cliquez sur le lien de groupe de sécurité réseau.

    ![Groupe de sécurité réseau](./media/sql-server-linux-azure-virtual-machine/networksecuritygroup.png)

1. Dans les propriétés du groupe de sécurité réseau, sélectionnez **les règles de sécurité de trafic entrant**.

1. Cliquez sur le **+ ajouter** bouton.

1. Fournissez un nom de « SQLServerRemoteConnections ».

1. Dans le **Service** liste, sélectionnez **MS SQL**.

    ![Règle de groupe de sécurité de MS SQL](./media/sql-server-linux-azure-virtual-machine/sqlnsgrule.png)

1. Cliquez sur **OK** pour enregistrer la règle pour votre machine virtuelle.

## <a id="connect"></a>Se connecter à la machine virtuelle Linux

Si vous utilisez déjà un interpréteur de commandes BASH, se connecter à la machine virtuelle Azure à l’aide de la **ssh** commande. Dans la commande suivante, remplacez le nom d’utilisateur de machine virtuelle et l’adresse IP pour se connecter à votre VM Linux.

```bash
ssh -l AzureAdmin 100.55.555.555
```

Vous pouvez trouver l’adresse IP de votre machine virtuelle dans le portail Azure.

![Adresse IP dans le portail Azure](./media/sql-server-linux-azure-virtual-machine/vmproperties.png)

Si vous en cours d’exécution sur Windows et que vous ne disposez pas d’un interpréteur de commandes BASH, vous pouvez installer un client SSH, tel que PuTTY.

1. [Téléchargez et installez PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

1. Exécutez PuTTY.

1. Sur l’écran de configuration de PuTTY, entrez l’adresse IP de votre machine virtuelle.

1. Cliquez sur Ouvrir, puis entrez votre nom d’utilisateur et un mot de passe à la demande.

Pour plus d’informations sur la connexion aux machines virtuelles Linux, consultez [créer un VM Linux sur Azure à l’aide du portail](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-quick-create-portal#ssh-to-the-vm).

## <a name="configure-sql-server"></a>Configurer SQL Server

1. Une fois connecté à votre VM Linux, ouvrez une nouvelle commande Terminal Server.

1. Configurez SQL Server avec la commande suivante.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup 
   ```

   Acceptez la licence et entrer un mot de passe pour le compte d’administrateur système. Vous pouvez démarrer le serveur lorsque vous y êtes invité.

1. Si vous le souhaitez, [installer les outils SQL Server](sql-server-linux-setup-tools.md).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une machine virtuelle de SQL Server 2017 dans Azure, vous pouvez vous connecter localement avec **sqlcmd** pour exécuter des requêtes Transact-SQL.

Si vous avez configuré la machine virtuelle de Azure pour les connexions distantes de SQL Server, vous devez également être en mesure de se connecter à distance. Pour obtenir un exemple de la connexion à SQL Server sur Linux à partir d’un ordinateur Windows à distance, consultez [SSMS d’utilisation de Windows pour se connecter à SQL Server sur Linux](sql-server-linux-develop-use-ssms.md).

Pour plus d’informations sur les ordinateurs virtuels Linux dans Azure, consultez le [Documentation de Machine virtuelle Linux](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/).

