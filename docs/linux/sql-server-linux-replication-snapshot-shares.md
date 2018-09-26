---
title: Configurer les partages de dossier d’instantanés réplication SQL Server sur Linux | Microsoft Docs
description: Cet article décrit comment configurer la réplication d’instantané dossier partages SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 9/24/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e8da23d77719fd15b12c9f305491827c4a92954b
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46714950"
---
# <a name="configure-replication-snapshot-folder-with-shares"></a>Configurer le dossier de capture instantanée de réplication avec des partages

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Le dossier d’instantanés est un répertoire que vous avez désigné en tant que partage ; les agents qui lisent et écrivent dans ce dossier doivent disposer des autorisations suffisantes pour y accéder.

![diagramme de la réplication][1]

### <a name="replication-snapshot-folder-share-explained"></a>Partage de dossier de capture instantanée de réplication expliqué

Avant des exemples, nous allons étudier comment SQL Server utilise les partages samba dans la réplication. Voici un exemple de base de comment cela fonctionne.

1. Partages Samba sont définis pour les fichiers écrits dans `/local/path1` par la réplication des agents sur le serveur de publication peuvent être vus par l’abonné
2. SQL Server est configuré pour utiliser des chemins d’accès de partage lorsque vous configurez le serveur de publication sur le serveur de distribution, telles que toutes les instances examineriez la `//share/path`
3. SQL Server détecte que le chemin d’accès local à partir de la `//share/path` de savoir où rechercher les fichiers
4. SQL Server lit/écrit dans les chemins d’accès locaux soutenu par un partage samba


## <a name="configure-a-samba-share-for-the-snapshot-folder"></a>Configurer un partage samba pour le dossier d’instantanés 

Les agents de réplication doivent un répertoire partagé entre les hôtes de réplication pour accéder aux dossiers de capture instantanée sur d’autres ordinateurs. Par exemple, dans la réplication transactionnelle par extraction, l’agent de distribution se trouve sur l’abonné, ce qui nécessite l’accès au serveur de distribution pour obtenir des articles. Dans cette section, nous allons passer en revue un exemple montrant comment configurer un partage samba sur deux hôtes de réplication.


## <a name="steps"></a>Étapes

Par exemple, nous allons configurer un dossier d’instantanés sur l’hôte 1 (le serveur de distribution) à partager avec l’hôte 2 (l’abonné) à l’aide de Samba. 

### <a name="install-and-start-samba-on-both-machines"></a>Installez et démarrez Samba sur les deux ordinateurs 

Sur Ubuntu :

```bash
sudo apt-get -y install samba
sudo service smbd restart
```

Sur RHEL :

```bash
sudo yum install samba
sudo service smb start
sudo service smb status
```

### <a name="on-host-1-distributor-set-up-the-samba-share"></a>Sur la configuration de l’hôte 1 (serveur de distribution) le partage Samba 

1. Configuration utilisateur et un mot de passe pour samba :

  ```bash
  sudo smbpasswd -a mssql 
  ```

1. Modifier le `/etc/samba/smb.conf` pour inclure l’entrée suivante, renseignez le *nom_partage* et *chemin d’accès* champs
 ```bash
  <[share_name]>
  path = </local/path/on/host/1>
  writable = yes
  create mask = 770
  directory mask 
  valid users = mssql 
  ```

  **Exemple**

  ```bash
  [mssql_data]    <- Name of the shared directory
  path = /var/opt/mssql/repldata <- location of directory we wish to share
  writable = yes  <- determines if the share is writable from other hosts
  create mask = 770  <- Linux permissions for files created 
  directory mask = 770 <- Linux permissions for directories created
  valid users = mssql   <- list of users who can login to this share
  ```

### <a name="on-host-2-subscriber--mount-the-samba-share"></a>Sur l’hôte 2 (abonné) monter le partage Samba

Modifiez la commande avec les chemins d’accès corrects et exécutez la commande suivante sur machine2 :

  ```bash
  sudo mount //<name_of_host_1>/<share_name> </local/path/on/host/2> -o user=mssql,uid=mssql,gid=mssql
  ```

  **Exemple**

  ```bash
  mount //host1/mssql_data /var/opt/mssql/repldata_shared -o user=mssql,uid=mssql,gid=mssql

  user=mssql <- sets the login name for samba
  uid=mssql   <- makes the mssql user as the owner of the mounted directory
  gid=mssql   <- sets the mssql group as the owner of the mounted directory
  ```

### <a name="on-both-hosts--configure-sql-server-on-linux-instances-to-use-snapshot-share"></a>Sur les deux hôtes configurer SQL Server sur des Instances de Linux pour utiliser le partage d’instantané

Ajoutez la section suivante pour `mssql.conf` sur les deux ordinateurs. Utiliser partout où le partage samba pour le / / / chemin de partage. Dans cet exemple, il serait `//host1/mssql_data`

  ```bash
  [uncmapping]
  //share/path = /local/path/on/hosts/
  ```

  **Exemple**

  Sur host1 :

  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/1
  ```

  Sur host2 :
  
  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/2
  ```

### <a name="configuring-publisher-with-shared-paths"></a>Configuration du serveur de publication avec des chemins d’accès partagé

* Lorsque vous configurez la réplication, utilisez le chemin d’accès de partages (par exemple `//host1/mssql_data`
* Carte `//host1/mssql_data` à un répertoire local et le mappage ajouté à `mssql.conf`.

## <a name="next-steps"></a>Étapes suivantes

[Concepts : Réplication de SQL Server sur Linux](sql-server-linux-replication.md)

[Procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

[1]: ./media/sql-server-linux-replication-snapshot-shares/image1.png
