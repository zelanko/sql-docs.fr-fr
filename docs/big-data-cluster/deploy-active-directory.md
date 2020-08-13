---
title: Déployer en mode Active Directory
titleSuffix: SQL Server Big Data Cluster
description: Apprenez à mettre à niveau des clusters Big Data SQL Server dans un domaine Active Directory.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 037c8bd26249ab3dc2cb3d0d8f4adf718f56000e
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243070"
---
# <a name="deploy-big-data-clusters-2019-in-active-directory-mode"></a>Déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] en mode Active Directory

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Ce document explique comment déployer un cluster Big Data SQL Server dans le mode d’authentification Active Directory. Le cluster utilise un domaine AD existant pour l’authentification.

>[!Note]
>Avant la version SQL Server 2019 CU5, il existait dans Clusters Big Data une restriction selon laquelle il n’était possible de déployer qu’un seul cluster sur un domaine Active Directory. Elle a été supprimée avec la version CU5. Pour plus d’informations sur les nouvelles fonctionnalités, consultez [Concept : Déploiement de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] en mode Active Directory](active-directory-deployment-background.md). Les exemples de cet article sont ajustés pour prendre en charge les deux cas d’utilisation de déploiement.

## <a name="background"></a>Arrière-plan

Pour activer l’authentification Active Directory (AD), le cluster BDC crée automatiquement les utilisateurs, les groupes, les comptes d’ordinateur et les noms de principaux de service (SPN) dont les différents services du cluster ont besoin. Pour fournir une relation d’imbrication à ces comptes et permettre de définir la portée des autorisations, choisissez au cours du déploiement une unité d’organisation (UO) dans laquelle seront créés tous les objets AD associés au cluster Big Data. Créez cette UO avant le déploiement du cluster.

Pour créer automatiquement tous les objets requis dans Active Directory, le cluster BDC a besoin d’un compte AD pendant le déploiement. Ce compte doit disposer d’autorisations pour créer des utilisateurs, des groupes et des comptes d’ordinateur au sein de l’unité d’organisation fournie.

Les étapes ci-dessous supposent que vous disposez déjà d’un contrôleur de domaine Active Directory. Si vous n’avez pas de contrôleur de domaine, le [guide](https://social.technet.microsoft.com/wiki/contents/articles/37528.create-and-configure-active-directory-domain-controller-in-azure-windows-server.aspx) suivant comprend les étapes qui peuvent être utiles.

Pour obtenir la liste des comptes et des groupes AD, consultez [Objets Active Directory générés automatiquement](active-directory-objects.md).

## <a name="create-ad-objects"></a>Créer des objets AD

Avant de déployer un cluster BDC avec l’intégration AD, procédez comme suit :

1. Créez une unité d’organisation (UO) dans laquelle tous les objets AD du cluster BDC seront stockés. Vous pouvez également choisir de désigner une UO existante lors du déploiement.
1. Créez un compte AD pour le cluster BDC ou utilisez un compte existant et fournissez les autorisations appropriées à ce compte AD du cluster BDC.

### <a name="create-a-user-in-ad-for-bdc-domain-service-account"></a>Créer un utilisateur dans Active Directory pour le compte de service de domaine du cluster BDC

Le cluster Big Data requiert un compte avec des autorisations spécifiques. Avant de continuer, assurez-vous de disposer d’un compte AD existant ou de créer un nouveau compte, que le cluster Big Data pourra utiliser pour configurer les objets nécessaires.

Pour créer un utilisateur dans Active Directory, vous pouvez cliquer avec le bouton droit sur le domaine ou l’unité d’organisation et sélectionner **Nouveau** > **Utilisateur** :

![image12](./media/deploy-active-directory/image12.png)

Cet utilisateur est désigné sous le terme de *compte de service de domaine du cluster BDC* dans cet article.

### <a name="create-an-ou"></a>Création d’une unité d’organisation

Sur le contrôleur de domaine, ouvrez **Utilisateurs et ordinateurs Active Directory**. Dans le panneau de gauche, cliquez avec le bouton droit sur le répertoire dans lequel vous souhaitez créer votre UO, sélectionnez **Créer** \> **Unité d’organisation**, puis suivez les invites de l’Assistant pour créer l’UO. Vous pouvez également créer une unité d’organisation avec PowerShell :

```powershell
New-ADOrganizationalUnit -Name "<name>" -Path "<Distinguished name of the directory you wish to create the OU in>"
```

Les exemples de cet article utilisent `bdc` comme nom de l’UO.

![image13](./media/deploy-active-directory/image13.png)

![image14](./media/deploy-active-directory/image14.png)

### <a name="set-permissions-for-an-ad-account"></a>Définition d’autorisations pour un compte AD 

Que vous ayez créé un nouvel utilisateur AD ou que vous utilisiez un utilisateur Active Directory existant, l’utilisateur doit disposer de certaines autorisations. Ce compte est le compte d’utilisateur que le contrôleur du cluster BDC utilisera lorsqu’il joindra le cluster à Active Directory.

Le compte de service de domaine (DSA) du cluster BDC doit être en mesure de créer des utilisateurs, des groupes et des comptes d’ordinateur dans l’unité d’organisation. Dans les étapes suivantes, nous avons nommé le compte de service de domaine du cluster BDC `bdcDSA`. Vous pouvez choisir n’importe quel nom pour ce compte.

1. Sur le contrôleur de domaine, ouvrez **Utilisateurs et ordinateurs Active Directory**

1. Dans le volet de gauche, accédez à votre domaine, puis à l’unité d’organisation que `bdc` utilisera

1. Cliquez avec le bouton droit sur l’UO, puis sélectionnez **Propriétés**.

1. Accédez à l’onglet Sécurité (assurez-vous que vous avez sélectionné **Fonctionnalités avancées** en cliquant avec le bouton droit sur l’unité d’organisation et en sélectionnant **Afficher**)

    ![image15](./media/deploy-active-directory/image15.png)

1. Cliquez sur **Ajouter...** et ajoutez l’utilisateur **bdcDSA**.

    ![image16](./media/deploy-active-directory/image16.png)

    ![image17](./media/deploy-active-directory/image17.png)

1. Sélectionnez l’utilisateur **bdcDSA**, puis désactivez toutes les autorisations et cliquez sur **Avancé**.

1. Cliquez sur **Ajouter**

    ![image18](./media/deploy-active-directory/image18.png)

    - Cliquez sur **Sélectionner un principal**, insérez **bdcDSA**, puis cliquez sur OK.

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

    - Cliquez sur **Sélectionner un principal**, insérez **bdcDSA**, puis cliquez sur OK.

    - Définissez **Type** sur **Autoriser**

    - Définissez **S’applique à** sur **Objets ordinateur descendants**

    - Faites défiler l’affichage vers le bas et cliquez sur **Effacer tout**

    - Refaites défiler l’affichage vers le haut et sélectionnez **Réinitialiser le mot de passe**

    - Cliquez sur **OK**

- Cliquez sur **Ajouter**

    - Cliquez sur **Sélectionner un principal**, insérez **bdcDSA**, puis cliquez sur OK.

    - Définissez **Type** sur **Autoriser**

    - Définissez **S’applique à** sur **Objets utilisateur descendants**

    - Faites défiler l’affichage vers le bas et cliquez sur **Effacer tout**

    - Refaites défiler l’affichage vers le haut et sélectionnez **Réinitialiser le mot de passe**

    - Cliquez sur **OK**

- Cliquez sur **OK** encore à deux reprises pour fermer les boîtes de dialogue ouvertes

## <a name="prepare-deployment"></a>Préparer le déploiement

Pour le déploiement du cluster BDC avec l’intégration Active Directory, des informations supplémentaires doivent être fournies pour la création des objets liés au cluster BDC dans Active Directory.

En utilisant le profil `kubeadm-prod` (ou `openshift-prod` à partir de la version CU5), vous disposez automatiquement des espaces réservés aux informations relatives à la sécurité et aux points de terminaison requises pour l’intégration AD.

De plus, vous devez fournir des informations d’identification que les [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] utiliseront pour créer les objets nécessaires dans Active Directory. Ces informations d’identification sont fournies en tant que variables d’environnement.

## <a name="set-security-environment-variables"></a>Définir des variables d’environnement de sécurité

Les variables d’environnement suivantes fournissent les informations d’identification pour le compte de service de domaine du cluster BDC, qui seront utilisées pour configurer l’intégration Active Directory. Ce compte est également utilisé par le cluster BDC pour gérer désormais les objets AD associés au cluster BDC.

```bash
export DOMAIN_SERVICE_ACCOUNT_USERNAME=<AD principal account name>
export DOMAIN_SERVICE_ACCOUNT_PASSWORD=<AD principal password>
```

## <a name="provide-security-and-endpoint-parameters"></a>Fournir des paramètres de sécurité et de point de terminaison

Outre les variables d’environnement pour les informations d’identification, vous devez fournir des informations de sécurité et de point de terminaison pour que l’intégration Active Directory fonctionne. Les paramètres obligatoires font automatiquement partie du [profil de déploiement](deployment-guidance.md#configfile) `kubeadm-prod`/`openshift-prod`.

L’intégration AD nécessite les paramètres suivants. Ajoutez ces paramètres aux fichiers `control.json` et `bdc.json` à l’aide des commandes `config replace` présentées plus loin dans cet article. Tous les exemples ci-dessous utilisent l’exemple de domaine `contoso.local`.

- `security.activeDirectory.ouDistinguishedName` : nom unique d’une unité d’organisation (UO) dans laquelle tous les comptes Active Directory créés par le déploiement du cluster seront ajoutés. Si le domaine est appelé `contoso.local`, le nom unique de l’unité d’organisation est : `OU=BDC,DC=contoso,DC=local`.

- `security.activeDirectory.dnsIpAddresses` : contient la liste des adresses IP des serveurs DNS du domaine. 

- `security.activeDirectory.domainControllerFullyQualifiedDns`: Liste des noms de domaine complets de contrôleur de domaine. Le nom de domaine complet contient le nom de l’ordinateur/hôte du contrôleur de domaine. Si vous avez plusieurs contrôleurs de domaine, vous pouvez fournir une liste ici. Exemple : `HOSTNAME.CONTOSO.LOCAL`.

  > [!IMPORTANT]
  > Lorsque plusieurs contrôleurs de domaine servent un domaine, utilisez le contrôleur de domaine principal comme première entrée de la liste `domainControllerFullyQualifiedDns` dans la configuration de la sécurité. Pour récupérer le nom du contrôleur de domaine principal, tapez `netdom query fsmo` dans l’invite de commandes, puis appuyez sur **ENTRÉE**.

- `security.activeDirectory.realm` **Paramètre facultatif** : Dans la majorité des cas, le domaine est égal au nom de domaine. Pour les cas où ils ne sont pas les mêmes, utilisez ce paramètre pour définir le nom du domaine (par exemple, `CONTOSO.LOCAL`). La valeur fournie pour ce paramètre doit être complète.

- `security.activeDirectory.domainDnsName`: Nom du domaine DNS qui sera utilisé pour le cluster (par exemple, `contoso.local`).

- `security.activeDirectory.clusterAdmins`: Ce paramètre prend un groupe AD. L’étendue du groupe AD doit être universelle ou globale. Les membres de ce groupe possèdent le rôle de cluster *bdcAdmin*, ce qui leur donne des autorisations d’administrateur dans le cluster. Ils disposent donc des [autorisations `sysadmin` dans SQL Server](../relational-databases/security/authentication-access/server-level-roles.md#fixed-server-level-roles), des [autorisations `superuser` dans HDFS](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsPermissionsGuide.html#The_Super-User) et des autorisations d’administrateurs lorsqu’ils sont connectés au point de terminaison du contrôleur.

  >[!IMPORTANT]
  >Créez ce groupe dans AD avant le début du déploiement. Si l’étendue de ce groupe AD est locale au niveau du domaine, le déploiement échoue.

- `security.activeDirectory.clusterUsers`: Liste des groupes Active Directory qui sont des utilisateurs standard (aucune autorisation d’administrateur) dans le cluster Big Data. La liste peut inclure des groupes AD dont l’étendue est universelle ou globale. Il ne peut pas s’agir de groupes locaux au niveau du domaine.

Les groupes AD de cette liste sont associés au rôle de cluster Big Data *bdcUser* et doivent être autorisés à accéder à SQL Server (cf. [Autorisations SQL Server](../relational-databases/security/permissions-hierarchy-database-engine.md)) ou à HDFS (consultez [Guide des autorisations HDFS](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsPermissionsGuide.html#:~:text=Permission%20Checks%20%20%20%20Operation%20%20,%20%20N%2FA%20%2029%20more%20rows%20)). Lorsqu’ils sont connectés au point de terminaison du contrôleur, ces utilisateurs peuvent seulement lister les points de terminaison disponibles dans le cluster à l’aide de la commande *azdata bdc endpoint list*.

Pour savoir comment mettre à jour les groupes AD en ce qui concerne ces paramètres, consultez [Gestion de l’accès au cluster Big Data en mode Active Directory](manage-user-access.md).

  >[!IMPORTANT]
  >Créez ces groupes dans AD avant le début du déploiement. Si l’étendue de l’un de ces groupes AD est locale au niveau du domaine, le déploiement échoue.

  >[!IMPORTANT]
  >Si vos utilisateurs de domaine présentent de nombreuses appartenances à des groupes, ajustez les valeurs du paramètre de passerelle *httpserver.requestHeaderBuffer* (valeur par défaut : *8192*) et du paramètre HDFS *hadoop.security.group.mapping.ldap.search.group.hierarchy.levels* (valeur par défaut : *10*), à l’aide du fichier de configuration de déploiement *bdc.json* personnalisé. Cette meilleure pratique vise à éviter les délais de connexion à la passerelle et les réponses HTTP comportant le code d’état 431 (*Champs d’en-tête de demande trop volumineux*). Voici une section du fichier de configuration montrant comment définir les valeurs de ces paramètres et indiquant les valeurs recommandées pour un nombre élevé d’appartenance à des groupes : 

```json
{
    ...
    "spec": {
        "resources": {
            ...
            "gateway": {
                "spec": {
                    "replicas": 1,
                    "endpoints": [{...}],
                    "settings": {
                        "gateway-site.gateway.httpserver.requestHeaderBuffer": "65536"
                    }
                }
            },
            ...
        },
        "services": {
            ...
            "hdfs": {
                "resources": [...],
                "settings": {
                  "core-site.hadoop.security.group.mapping.ldap.search.group.hierarchy.levels": "4"
                }
            },
            ...
        }
    }
}
```

  >[!IMPORTANT]
  >Créez les groupes fournis pour les paramètres ci-dessous dans AD avant le début du déploiement. Si l’étendue de l’un de ces groupes AD est locale au niveau du domaine, le déploiement échoue.

- `security.activeDirectory.appOwners` **Paramètre facultatif** : Liste des groupes Active Directory qui sont autorisés à créer, supprimer et exécuter n’importe quelle application. La liste peut inclure des groupes AD dont l’étendue est universelle ou globale. Il ne peut pas s’agir de groupes locaux au niveau du domaine.

- `security.activeDirectory.appReaders` **Paramètre facultatif** : liste des groupes AD qui sont autorisés à exécuter n’importe quelle application. La liste peut inclure des groupes AD dont l’étendue est universelle ou globale. Il ne peut pas s’agir de groupes locaux au niveau du domaine.

Le tableau ci-dessous montre le modèle d’autorisation pour la gestion des applications :

|   Rôles autorisés   |   Commande azdata   |
|----------------------|--------------------|
|   appOwner           | azdata app create  |
|   appOwner           | azdata app update  |
|   appOwner, appReader| azdata app list    |
|   appOwner, appReader| azdata app describe|
|   appOwner           | azdata app delete  |
|   appOwner, appReader| azdata app run     |

- `security.activeDirectory.subdomain`: **(Paramètre facultatif)** Ce paramètre, introduit dans la version SQL Server 2019 CU5, permet de prendre en charge le déploiement de plusieurs clusters Big Data sur le même domaine. À l’aide de ce paramètre, vous pouvez spécifier des noms DNS différents pour tous les clusters Big Data déployés. Si la valeur de ce paramètre n’est pas spécifiée dans la section Active Directory du fichier `control.json`, c’est par défaut le nom du cluster Big Data (identique au nom de l’espace de noms Kubernetes) qui sera utilisé pour calculer la valeur du paramètre subdomain. 

  >[!NOTE]
  >La valeur transmise par le biais du paramètre subdomain ne constitue pas un nouveau domaine AD, mais seulement un domaine DNS utilisé en interne par le cluster Big Data.

  >[!IMPORTANT]
  >À partir de la version of SQL Server 2019 CU5, vous devez mettre à niveau **l’interface CLI azdata** ou en installer la dernière version pour tirer parti de ces nouvelles fonctionnalités et déployer plusieurs clusters Big Data dans le même domaine.

  Pour plus d’informations sur le déploiement de plusieurs clusters Big Data dans le même domaine Active Directory, consultez [Concept : Déploiement de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] en mode Active Directory](active-directory-deployment-background.md).

- `security.activeDirectory.accountPrefix`: **(Paramètre facultatif)** Ce paramètre, introduit dans la version SQL Server 2019 CU5, permet de prendre en charge le déploiement de plusieurs clusters Big Data sur le même domaine. Ce paramètre garantit, pour différents services Clusters Big Data, l’unicité des noms de compte, qui doivent varier d’un cluster à l’autre. La personnalisation du nom de préfixe de compte est facultative. Par défaut, c’est le nom du sous-domaine qui est utilisé comme préfixe de compte. Si ce nom dépasse 12 caractères, le préfixe de compte est constitué des 12 premiers caractères.  

  >[!NOTE]
  >Active Directory impose que les noms de compte soient limités à 20 caractères. Le cluster Big Data doit en utiliser 8 pour distinguer les pods et les StatefulSet, ce qui laisse 12 caractères comme limite du préfixe de compte.

[Vérifiez l’étendue du groupe AD](https://docs.microsoft.com/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps) pour déterminer s’il s’agit d’un groupe local de domaine.

Si vous n’avez pas encore initialisé le fichier de configuration de déploiement, vous pouvez exécuter cette commande pour obtenir une copie de la configuration. Les exemples ci-dessous utilisent le profil `kubeadm-prod`. Le même principe s’applique à `openshift-prod`.

```bash
azdata bdc config init --source kubeadm-prod  --target custom-prod-kubeadm
```

Pour définir les paramètres ci-dessus dans le fichier `control.json`, utilisez les commandes `azdata` suivantes. Ces commandes remplacent la configuration et fournissent vos propres valeurs avant le déploiement.

> [!IMPORTANT]
> Dans la version SQL Server 2019 CU2, la section de la configuration de la sécurité dans le profil de déploiement a été restructurée : tous les paramètres Active Directory se trouvent maintenant dans le nouveau *activeDirectory* de l’arborescence JSON sous *security* dans le fichier *control.json*.

>[!NOTE]
> En plus de fournir des valeurs distinctes pour le sous-domaine, comme nous l’avons vu dans cette section, vous devez utiliser des numéros de port différents pour les points de terminaison Clusters Big Data en cas de déploiement de plusieurs clusters Big Data dans le même cluster Kubernetes. Ces numéros de port peuvent être configurés au moment du déploiement au moyen de profils de [configuration de déploiement](deployment-custom-configuration.md).

L’exemple ci-dessous s’applique à SQL Server 2019 CU2. Il montre comment remplacer les valeurs des paramètres Active Directory dans la configuration du déploiement. Les détails du domaine ci-dessous sont des exemples de valeurs.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

Si vous le souhaitez, à partir de la version SQL Server 2019 CU5 uniquement, vous pouvez remplacer la valeur par défaut des paramètres `subdomain` et `accountPrefix`.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.subdomain=[\"bdctest\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.accountPrefix=[\"bdctest\"]"
```

De la même façon, dans les versions antérieures à SQL Server 2019 CU2, vous pouvez exécuter :

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

Outre les informations ci-dessus, vous devez également fournir des noms DNS pour les différents points de terminaison de cluster. Les entrées DNS utilisant les noms DNS que vous avez fournis seront automatiquement créées sur votre serveur DNS lors du déploiement. Vous utiliserez ces noms lors de la connexion aux différents points de terminaison du cluster. Par exemple, si le nom DNS de l’instance maître SQL est `mastersql`, sachant que le sous-domaine utilise la valeur par défaut du nom de cluster dans *control.json*, vous utiliserez `mastersql.contoso.local,31433` ou `mastersql.mssql-cluster.contoso.local,31433` (en fonction des valeurs fournies dans les fichiers de configuration de déploiement pour le nom DNS des points de terminaison) pour vous connecter à l’instance maître à partir des outils. 

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[1].dnsName=<monitoring services DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=<SQL Master Primary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=<SQL Master Secondary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=<Gateway (Knox) DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=<app proxy DNS name>.<Domain name. e.g. contoso.local>"
```

> [!IMPORTANT]
> Vous pouvez utiliser les noms DNS de point de terminaison de votre choix, à condition qu’ils soient complets et n’entrent pas en conflit entre deux clusters Big Data déployés dans le même domaine. Il est possible d’opter pour la valeur du paramètre `subdomain` afin d’être sûr que les noms DNS soient différents entre les clusters. Par exemple :

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.<subdomain e.g. mssql-cluster>.contoso.local"
```

Vous trouverez un exemple de script ici pour [déployer un cluster Big Data SQL Server sur un cluster Kubernetes à nœud unique (kubeadm) avec l’intégration Active Directory](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm-ad).

> [!Note]
> Il peut exister des cas de figure dans lesquels la prise en compte du nouveau paramètre `subdomain` n’est pas possible, par exemple, si vous devez déployer une version antérieure à CU5 et que vous avez déjà mis à niveau **l’interface CLI azdata**. Même si cette situation est très improbable, vous pouvez définir le paramètre `useSubdomain` sur `false` dans la section Active Directory de `control.json` pour rétablir le comportement d’avant CU5.  Voici la commande à exécuter :

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.useSubdomain=false"
```

Vous devez maintenant avoir défini tous les paramètres requis pour un déploiement du cluster BDC avec l’intégration Active Directory.

Vous pouvez maintenant déployer le cluster BDC intégré à Active Directory à l’aide de la commande `azdata` et du profil de déploiement kubeadm-prod. Pour obtenir une documentation complète sur le déploiement des [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)], consultez [Comment déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md).

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

Il existe deux solutions pour se connecter au point de terminaison du contrôleur à l’aide de `azdata` et de l’authentification AD. Vous pouvez utiliser le paramètre *--endpoint/-e* :

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

Vous pouvez également vous connecter à l’aide du paramètre *--namespace/-n*, à savoir le nom du cluster Big Data :

```bash
kinit <username>@<domain name>
azdata login -n <clusterName> --auth ad
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

**Limitations à prendre en compte dans SQL Server 2019 CU5**

- Actuellement, les tableaux de bord Recherche dans les journaux et Métriques ne prennent pas en charge l’authentification Active Directory. Le nom d’utilisateur et le mot de passe de base définis lors du déploiement peuvent être utilisés pour l’authentification auprès de ces tableaux de bord. Tout autre point de terminaison de cluster prend en charge l’authentification AD.

- À l’heure actuelle, le mode AD sécurisé ne fonctionne que sur les environnements de déploiement `kubeadm` et `openshift`, et non sur AKS ni ARO. Les profils de déploiement `kubeadm-prod` et `openshift-prod` comprennent les sections de sécurité par défaut.

- Avant la version SQL Server 2019 CU5, seul un cluster Big Data par domaine (Active Directory) est autorisé. La présence de plusieurs clusters Big Data par domaine est disponible à partir de la version CU5.

- Aucun des groupes AD spécifiés dans les configurations de sécurité ne peut être d’une étendue DomainLocal. Vous pouvez vérifier l’étendue d’un groupe AD en suivant [ces instructions](https://docs.microsoft.com/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps).

- Le compte AD qui peut servir à se connecter à Clusters Big Data est autorisé à partir du domaine configuré pour Clusters Big Data. Les connexions à partir d’un autre domaine approuvé ne sont pas prises en charge.

## <a name="next-steps"></a>Étapes suivantes

[Résolution des problèmes d’intégration Active Directory Clusters Big Data SQL Server](troubleshoot-active-directory.md)

[Concept : Déploiement de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] en mode Active Directory](active-directory-deployment-background.md)
