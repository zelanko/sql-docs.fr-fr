---
title: Déployer un cluster Big Data SQL Server en mode Active Directory
titleSuffix: Deploy SQL Server Big Data Cluster in Active Directory mode
description: Apprenez à mettre à niveau des clusters Big Data SQL Server dans un domaine Active Directory.
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 11/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 40b1101d9ee6c57db865282d1556f96aa4311a1f
ms.sourcegitcommit: 02b7fa5fa5029068004c0f7cb1abe311855c2254
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74127443"
---
# <a name="deploy-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-in-active-directory-mode"></a>Déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] en mode Active Directory

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce document décrit le déploiement d’un cluster Big Data (cluster BDC) SQL Server 2019 en mode d’authentification Active Directory, qui utilisera un domaine Active Directory existant pour l’authentification.

## <a name="background"></a>Arrière-plan

Pour activer l’authentification Active Directory (AD), le cluster BDC crée automatiquement les utilisateurs, les groupes, les comptes d’ordinateur et les noms de principaux de service (SPN) dont les différents services du cluster ont besoin. Pour fournir une relation contenant-contenu à ces comptes et permettre de définir la portée des autorisations, nommez une unité d’organisation (UO) au cours du déploiement, où tous les objets AD associés au cluster BDC seront créés. Créez cette UO avant le déploiement du cluster.

Pour créer automatiquement tous les objets requis dans Active Directory, le cluster BDC a besoin d’un compte AD pendant le déploiement. Ce compte doit disposer d’autorisations pour créer des utilisateurs, des groupes et des comptes d’ordinateur au sein de l’unité d’organisation fournie.

Les étapes ci-dessous supposent que vous disposez déjà d’un contrôleur de domaine Active Directory. Si vous n’avez pas de contrôleur de domaine, le [guide](https://social.technet.microsoft.com/wiki/contents/articles/37528.create-and-configure-active-directory-domain-controller-in-azure-windows-server.aspx) suivant comprend les étapes qui peuvent être utiles.

## <a name="create-ad-objects"></a>Créer des objets AD

Avant de déployer un cluster BDC avec l’intégration AD, procédez comme suit :

1. Créez une unité d’organisation (UO) dans laquelle tous les objets AD du cluster BDC seront stockés. Vous pouvez également choisir de désigner une unité d’organisation existante lors du déploiement.
1. Créez un compte AD pour le cluster BDC ou utilisez un compte existant et fournissez les autorisations appropriées à ce compte AD du cluster BDC.

### <a name="create-a-user-in-ad-for-bdc-domain-service-account"></a>Créer un utilisateur dans Active Directory pour le compte de service de domaine du cluster BDC

Le cluster Big Data requiert un compte avec des autorisations spécifiques. Avant de continuer, assurez-vous de disposer d’un compte AD existant ou de créer un nouveau compte, que le cluster Big Data pourra utiliser pour configurer les objets nécessaires.

Pour créer un utilisateur dans Active Directory, vous pouvez cliquer avec le bouton droit sur le domaine ou l’unité d’organisation et sélectionner **Nouveau** > **Utilisateur** :

![image12](./media/deploy-active-directory/image12.png)

Cet utilisateur est désigné sous le terme de *compte de service de domaine du cluster BDC* dans cet article.

### <a name="creating-an-ou"></a>Création d’une unité d’organisation

Sur le contrôleur de domaine, ouvrez **Utilisateurs et ordinateurs Active Directory**. Dans le volet de gauche, cliquez avec le bouton droit sur le répertoire dans lequel vous souhaitez créer votre UO, sélectionnez Nouveau - \> **Unité d’organisation**, puis suivez les invites de l’Assistant pour créer l’unité d’organisation. Vous pouvez également créer une unité d’organisation avec PowerShell :

```powershell
New-ADOrganizationalUnit -Name "<name>" -Path "<Distinguished name of the directory you wish to create the OU in>"
```

Dans les exemples de cet article, nous nommerons l’unité d’organisation : `bdc`

![image13](./media/deploy-active-directory/image13.png)

![image14](./media/deploy-active-directory/image14.png)

### <a name="setting-permissions-the-bdc-ad-account"></a>Définition des autorisations du compte AD du cluster BDC

Que vous ayez créé un nouvel utilisateur AD ou que vous utilisiez un utilisateur Active Directory existant, l’utilisateur doit disposer de certaines autorisations. Ce compte est le compte d’utilisateur que le contrôleur du cluster BDC utilisera lorsqu’il joindra le cluster à Active Directory.

Le compte de service de domaine (DSA) du cluster BDC doit être en mesure de créer des utilisateurs, des groupes et des comptes d’ordinateur dans l’unité d’organisation. Dans les étapes suivantes, nous avons nommé le compte de service de domaine du cluster BDC `bdcDSA`. Vous pouvez choisir n’importe quel nom pour ce compte.

1. Sur le contrôleur de domaine, ouvrez **Utilisateurs et ordinateurs Active Directory**

1. Dans le volet de gauche, accédez à votre domaine, puis à l’unité d’organisation que `bdc` utilisera

1. Cliquez avec le bouton droit sur l’unité d’organisation et sélectionnez **Propriétés**

1. Accédez à l’onglet Sécurité (assurez-vous que vous avez sélectionné **Fonctionnalités avancées** en cliquant avec le bouton droit sur l’unité d’organisation et en sélectionnant **Afficher**)

    ![image15](./media/deploy-active-directory/image15.png)

1. Cliquez sur **Ajouter...** et ajoutez l’utilisateur **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA**

    ![image16](./media/deploy-active-directory/image16.png)

    ![image17](./media/deploy-active-directory/image17.png)

1. Sélectionnez l’utilisateur **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA** et désactivez toutes les autorisations, puis cliquez sur **Avancé**

1. Cliquez sur **Ajouter**

    ![image18](./media/deploy-active-directory/image18.png)

    - Cliquez sur **Sélectionner un principal**, insérez **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA**, puis cliquez sur OK

    - Définissez **Type** sur **Autoriser**

    - Définissez **S’applique à** sur **Cet objet et tous ceux descendants**

        ![image19](./media/deploy-active-directory/image19.png)

    - Faites défiler l’affichage vers le bas et cliquez sur **Effacer tout**

    - Refaites défiler l’affichage vers le haut, puis sélectionnez :
       - **Lire toutes les propriétés**
       - **Écrire toutes les propriétés**
       - **Créer des objets ordinateur**
       - **Supprimer des objets ordinateur**
       - **Créer des objets groupe**
       - **Supprimer des objets groupe**
       - **Créer des objets utilisateur**
       - **Supprimer des objets utilisateur**

    - Cliquez sur **OK**

- Cliquez sur **Ajouter**

    - Cliquez sur **Sélectionner un principal**, insérez **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA**, puis cliquez sur OK

    - Définissez **Type** sur **Autoriser**

    - Définissez **S’applique à** sur **Objets ordinateur descendants**

    - Faites défiler l’affichage vers le bas et cliquez sur **Effacer tout**

    - Refaites défiler l’affichage vers le haut et sélectionnez **Réinitialiser le mot de passe**

    - Cliquez sur **OK**

- Cliquez sur **Ajouter**

    - Cliquez sur **Sélectionner un principal**, insérez **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]DSA**, puis cliquez sur OK

    - Définissez **Type** sur **Autoriser**

    - Définissez **S’applique à** sur **Objets utilisateur descendants**

    - Faites défiler l’affichage vers le bas et cliquez sur **Effacer tout**

    - Refaites défiler l’affichage vers le haut et sélectionnez **Réinitialiser le mot de passe**

    - Cliquez sur **OK**

- Cliquez sur **OK** encore à deux reprises pour fermer les boîtes de dialogue ouvertes

## <a name="prepare-deployment"></a>Préparer le déploiement

Pour le déploiement du cluster BDC avec l’intégration Active Directory, des informations supplémentaires doivent être fournies pour la création des objets liés au cluster BDC dans Active Directory.

En utilisant le profil `kubeadm-prod`, vous disposez automatiquement des espaces réservés pour les informations relatives à la sécurité et les informations relatives aux points de terminaison qui sont requises pour l’intégration Active Directory.

De plus, vous devez fournir des informations d’identification que les [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] utiliseront pour créer les objets nécessaires dans Active Directory. Ces informations d’identification sont fournies en tant que variables d’environnement.

## <a name="set-security-environment-variables"></a>Définir des variables d’environnement de sécurité

Les variables d’environnement suivantes fournissent les informations d’identification pour le compte de service de domaine du cluster BDC, qui seront utilisées pour configurer l’intégration Active Directory. Ce compte est également utilisé par le cluster BDC pour gérer désormais les objets AD associés au cluster BDC.

```bash
export DOMAIN_SERVICE_ACCOUNT_USERNAME=<AD principal account name>
export DOMAIN_SERVICE_ACCOUNT_PASSWORD=<AD principal password>
```

## <a name="provide-security-and-endpoint-parameters"></a>Fournir des paramètres de sécurité et de point de terminaison

Outre les variables d’environnement pour les informations d’identification, vous devez fournir des informations de sécurité et de point de terminaison pour que l’intégration Active Directory fonctionne. Les paramètres obligatoires font automatiquement partie du [profil de déploiement](deployment-guidance.md#configfile) `kubeadm-prod`.

L’intégration AD nécessite les paramètres suivants. Ajoutez ces paramètres aux fichiers `control.json` et `bdc.json` à l’aide des commandes `config replace` présentées plus loin dans cet article. Tous les exemples ci-dessous utilisent l’exemple de domaine `contoso.local`.

- `security.ouDistinguishedName` : nom unique d’une unité d’organisation (UO) dans laquelle tous les comptes Active Directory créés par le déploiement du cluster seront ajoutés. Si le domaine est appelé `contoso.local`, le nom unique de l’unité d’organisation est : `OU=BDC,DC=contoso,DC=local`.

- `security.dnsIpAddresses` : liste des adresses IP des contrôleurs de domaine

- `security.domainControllerFullyQualifiedDns`: Liste des noms de domaine complets de contrôleur de domaine. Le nom de domaine complet contient le nom de l’ordinateur/hôte du contrôleur de domaine. Si vous avez plusieurs contrôleurs de domaine, vous pouvez fournir une liste ici. Exemple : `HOSTNAME.CONTOSO.LOCAL`

- `security.realm` **Paramètre facultatif** : Dans la majorité des cas, le domaine est égal au nom de domaine. Pour les cas où ils ne sont pas les mêmes, utilisez ce paramètre pour définir le nom du domaine (par exemple, `CONTOSO.LOCAL`).

- `security.domainDnsName`: Nom de votre domaine (par exemple, `contoso.local`).

- `security.clusterAdmins`: Ce paramètre accepte le groupe AD *one-. Les membres de ce groupe obtiennent des autorisations d’administrateur dans le cluster. Cela signifie qu’ils auront des autorisations sysadmin dans SQL Server, des autorisations de superutilisateur dans HDFS et des administrateurs dans le contrôleur.

- `security.clusterUsers`: Liste des groupes Active Directory qui sont des utilisateurs standard (aucune autorisation d’administrateur) dans le cluster Big Data.

- `security.appOwners` **Paramètre facultatif** : Liste des groupes Active Directory qui sont autorisés à créer, supprimer et exécuter une application quelconque.

- `security.appReaders` **Paramètre facultatif** : liste des utilisateurs ou groupes Active Directory qui sont autorisés à exécuter une application quelconque. 

Si vous n’avez pas encore initialisé le fichier de configuration de déploiement, vous pouvez exécuter cette commande pour obtenir une copie de la configuration.

```bash
azdata bdc config init --source kubeadm-prod  --target custom-prod-kubeadm
```

Pour définir les paramètres ci-dessus dans le fichier `control.json`, utilisez les commandes `azdata` suivantes. Ces commandes remplacent la configuration et fournissent vos propres valeurs avant le déploiement.

L’exemple ci-dessous remplace les valeurs des paramètres associés à Active Directory dans la configuration du déploiement. Les détails du domaine ci-dessous sont des exemples de valeurs.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterUsers=[\"bdcusersgroup\"]"
```

Outre les informations ci-dessus, vous devez également fournir des noms DNS pour les différents points de terminaison de cluster. Les entrées DNS utilisant les noms DNS que vous avez fournis seront automatiquement créées sur votre serveur DNS lors du déploiement. Vous utiliserez ces noms lors de la connexion aux différents points de terminaison du cluster. Par exemple, si le nom DNS de l’instance principale SQL est `mastersql`, vous utiliserez `mastersql.contoso.local,31433` pour vous connecter à l’instance principale à partir des outils.

> [!NOTE]
> Veillez à créer des entrées DNS sur le serveur DNS pour les noms que vous définissez ci-dessous. Pour les déploiements `kubeadm`, vous pouvez, par exemple, utiliser l’adresse IP du nœud principal Kubernetes lors de la création des entrées DNS.

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[1].dnsName=<monitoring services DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=<SQL Master Primary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=<SQL Master Secondary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=<Gateway (Knox) DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=<app proxy DNS name>.<Domain name. e.g. contoso.local>"
```

Vous trouverez un exemple de script ici pour [déployer un cluster Big Data SQL Server sur un cluster Kubernetes à nœud unique (kubeadm) avec l’intégration Active Directory](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm-ad).

Vous devez maintenant avoir défini tous les paramètres requis pour un déploiement du cluster BDC avec l’intégration Active Directory.

Pour obtenir une documentation complète sur le déploiement de [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)], consultez la [documentation officielle](deployment-guidance.md).

## <a name="verify-reverse-dns-entry-for-domain-controller"></a>Vérifier l’entrée DNS inversée pour le contrôleur de domaine

Assurez-vous qu’il existe une entrée DNS inversée (enregistrement PTR) pour le contrôleur de domaine lui-même, inscrite sur le serveur DNS. Vous pouvez vérifier cela en exécutant un `nslookup` du nom de domaine sur le contrôleur de domaine, pour voir qu’il peut être résolu avec l’adresse IP du contrôleur de domaine.

## <a name="connect-to-cluster-endpoints-in-ad-mode"></a>Se connecter aux points de terminaison de cluster en mode AD

Connectez-vous à l’instance principale SQL Server avec l’authentification AD.

Pour vérifier les connexions AD à l’instance SQL Server, connectez-vous à l’instance principale SQL avec `sqlcmd`. Les connexions sont automatiquement créées pour les groupes fournis lors du déploiement (`clusterUsers` et `clusterAdmins`).

Si vous utilisez Linux, commencez par exécuter `kinit` en tant qu’utilisateur Active Directory, puis exécutez `sqlcmd`. Si vous utilisez Windows, connectez-vous simplement en tant qu’utilisateur souhaité à partir d’un **ordinateur client joint au domaine**.

### <a name="connect-to-master-instance-from-linuxmac"></a>Se connecter à l’instance principale à partir de Linux/Mac

```bash
kinit <username>@<domain name>
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="connect-to-master-instance-from-windows"></a>Se connecter à l’instance principale à partir de Windows

```cmd
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="log-in-to-sql-server-master-instance-using-azure-data-studio-or-ssms"></a>Se connecter à l’instance principale SQL Server à l’aide d’Azure Data Studio ou SSMS

À partir d’un client joint au domaine, vous pouvez ouvrir SSMS ou Azure Data Studio et vous connecter à l’instance principale. Il s’agit de la même expérience que la connexion à n’importe quelle instance SQL Server à l’aide de l’authentification Active Directory.

À partir de SSMS :

![image23](./media/deploy-active-directory/image23.png)

À partir d’Azure Data Studio :

![image24](./media/deploy-active-directory/image24.png)}

### <a name="log-in-to-controller-with-ad-authentication"></a>Se connecter au contrôleur avec l’authentification Active Directory

#### <a name="connect-to-controller-with-ad-authentication-from-linuxmac"></a>Se connecter au contrôleur avec l’authentification Active Directory à partir de Linux/Mac

Vous pouvez vous connecter au point de terminaison du contrôleur à l’aide de `azdata` et de l’authentification Active Directory.

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

#### <a name="connect-to-controller-with-ad-authentication-from-windows"></a>Se connecter au contrôleur avec l’authentification Active Directory à partir de Windows

```cmd
azdata login -e https://<controller DNS name>:30080 --auth ad
```

### <a name="use-ad-authentication-to-knox-gateway-webhdfs"></a>Utiliser l’authentification AD pour la passerelle Knox (webHDFS)

Vous pouvez également émettre des commandes HDFS à l’aide de curl via le point de terminaison de la passerelle Knox. Cela nécessite l’authentification Active Directory pour Knox. La commande curl ci-dessous émet un appel REST webHDFS via la passerelle Knox pour créer un répertoire appelé `products`

```bash
curl -k -v --negotiate -u : https://<Gateway DNS name>:30443/gateway/default/webhdfs/v1/products?op=MKDIRS -X PUT
```

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

**Limitations à prendre en compte dans cette version :**

- Actuellement, les tableaux de bord Recherche dans les journaux et Métriques ne prennent pas en charge l’authentification Active Directory. La prise en charge d’Active Directory pour ce point de terminaison est planifiée pour une version ultérieure. Le nom d’utilisateur et le mot de passe de base définis lors du déploiement peuvent être utilisés pour l’authentification auprès de ces tableaux de bord. Tout autre point de terminaison de cluster prend en charge l’authentification AD.

- Le mode Active Directory sécurisé fonctionnera uniquement sur les environnements de déploiement `kubeadm` et non pas sur AKS pour le moment. Le profil de déploiement `kubeadm-prod` comprend les sections de sécurité par défaut.

- Un seul cluster BDC par domaine est autorisé pour l’instant. L’activation de plusieurs clusters BDC par domaine est planifiée pour une version ultérieure.
