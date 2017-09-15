---
title: "Mise à jour - SQL Server sur Linux docs | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour Microsoft SQL Server sur Linux."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 9e6b139e45ccb5184255eabedfb0f809ff64fd2b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nouveau et récemment mis à jour : SQL Server sur Linux docs



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates de mises à jour :* &nbsp; **2017-07-18** &nbsp; - à - &nbsp; **2017-09-11.**
- *Zone de sujet :* &nbsp; **Microsoft SQL Server sur Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants atteindre de nouveaux articles qui ont été ajoutées récemment.


1. [Messagerie de base de données et les alertes par courrier électronique avec l’Agent SQL sur Linux](sql-server-linux-db-mail-sql-agent.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriées dans la section extraits.

1. [Utiliser le groupe de disponibilité haute disponibilité pour SQL Server sur Linux](#TitleNum_1)
2. [Configurer SQL Server 2017 les images de conteneur sur Docker](#TitleNum_2)
3. [Configurer SQL Server sur Linux avec l’outil mssql-conf](#TitleNum_3)
4. [Commentaires client pour SQL Server sur Linux](#TitleNum_4)
5. [Migrer une base de données SQL Server à partir de Windows et Linux à l’aide de la sauvegarde et restauration](#TitleNum_5)
6. [Notes de publication pour 2017 du serveur SQL sur Linux](#TitleNum_6)
7. [Aide à l’installation de SQL Server sur Linux](#TitleNum_7)
8. [Installer SQL Server Integration Services (SSIS) sur Linux](#TitleNum_8)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-operate-ha-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-failover-hamd"></a>1. &nbsp;[Fonctionner à haute disponibilité groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-failover-ha.md)

*Mise à jour : 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 167.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1bef3ece125721b041aa2b9d836329736377df8d 669d2b9a614d680b98280d5b522ba82cf466536c  (PR=2948  ,  Filename=sql-server-linux-availability-group-failover-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



**Mettre à niveau le groupe de disponibilité**


Mettre à niveau un groupe de disponibilité, passez en revue les meilleures pratiques à [mise à niveau disponibilité groupe réplica instances--... / database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Les sections suivantes expliquent comment effectuer une mise à niveau propagée avec des instances de SQL Server sur Linux avec des groupes de disponibilité.

**Étapes de mise à niveau sur Linux**


Lorsque les réplicas du groupe de disponibilité sont sur des instances de SQL Server sous Linux, le type de cluster du groupe de disponibilité est `EXTERNAL` ou `NONE`. Un groupe de disponibilité qui est géré par un gestionnaire de cluster en plus de Cluster de basculement Windows Server (WSFC) est `EXTERNAL`. STIMULATEUR avec Corosync est un exemple d’un gestionnaire de cluster externe. Un groupe de disponibilité avec aucun gestionnaire de cluster a le type de cluster `NONE` les étapes de mise à niveau décrites ici sont spécifiques de groupes de disponibilité de type cluster `EXTERNAL` ou `NONE`.

1. Avant de commencer, sauvegardez chaque base de données.
2. Mettre à niveau des instances de SQL Server qui hébergent les réplicas secondaires.

    a. Mettre à niveau tout d’abord des réplicas secondaires asynchrones.

    b. Mettre à niveau les réplicas secondaires synchrones.

   >[!NOTE]
   >Si un groupe de disponibilité possède uniquement asynchrone réplicas - pour éviter toute perte de données modifiez un réplica synchrone et attendez qu’il est synchronisé. Puis, mettez à niveau de ce réplica.

   b.1. Arrêter la ressource sur le nœud qui héberge le réplica secondaire ciblé pour la mise à niveau

   Avant d’exécuter la commande de mise à niveau, arrêtez la ressource afin que le cluster ne sera pas surveiller et inutilement d’échouer. L’exemple suivant ajoute une contrainte d’emplacement sur le nœud entraîne sur la ressource doit être arrêtée. Mise à jour `ag_cluster-master` avec le nom de ressource et `nodeName1` avec le nœud qui héberge le réplica ciblé pour la mise à niveau.

```
   pcs constraint location ag_cluster-master avoids nodeName1
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>2. &nbsp;[Images de conteneur de configuration de SQL Server 2017 sur Docker](sql-server-linux-configure-docker.md)

*Mise à jour : 2017-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 257.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0239ed55a23721eedcc0407a0886d08da47c975b 108fe230151cff7dc91fcdc22218f232394746ec  (PR=3050  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=60272ce672c0a32738b0084ea86f8907ec7fc0a5) -->



1. Identifier le Docker **balise** pour la version que vous souhaitez utiliser. Pour afficher les légendes disponibles, consultez [la page du hub Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Extraire l’image de conteneur de SQL Server avec la balise. Par exemple, pour extraire l’image RC1, remplacez `<image_tag>` dans la commande suivante avec `rc1`.

```
   docker pull microsoft/mssql-server-linux:<image_tag>
```

1. Pour exécuter un nouveau conteneur avec cette image, spécifiez le nom de balise dans le `docker run` commande. Dans la commande suivante, remplacez `<image_tag>` avec la version que vous souhaitez exécuter.

```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

Ces étapes peuvent également servir à passer un conteneur existant. Par exemple, vous pourrez à restaurer ou de la rétrogradation d’un conteneur en cours d’exécution pour le dépannage ou de test. Pour passer un conteneur en cours d’exécution, vous devez utiliser une technique de persistance pour le dossier de données. Suivez la procédure décrite dans la [mise à niveau section--#upgrade), mais spécifie le nom de balise de l’ancienne version lorsque vous exécutez le nouveau conteneur.

> [!IMPORTANT]



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>3. &nbsp;[Configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md)

*Mise à jour : 2017-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= lbosq.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6117f03e9617b70077488d86f94b32537c4cb9e8 4247a749c056037dd71a27121525be04be6a4f21  (PR=3042  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=46b16dcf147dbd863eec0330e87511b4ced6c4ce) -->



**<a id="localaudit"></a>Définir un répertoire local d’audit**


Le **telemetry.userrequestedlocalauditdirectory** paramètre active d’Audit Local et vous permet de définir le répertoire où les Local journaux d’Audit est créés.

1. Créez un répertoire cible pour les nouveaux journaux d’Audit Local. L’exemple suivant crée un nouveau **/tmp/audit** active :

```
   sudo mkdir /tmp/audit
```

1. Modifier le propriétaire et le groupe du répertoire à la **mssql** utilisateur :

```
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
```

1. Exécutez le script mssql-conf en tant que racine avec le **définir** commande **telemetry.userrequestedlocalauditdirectory**:

```
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
```

1. Redémarrez le service SQL Server :

```
   sudo systemctl restart mssql-server
```

Pour plus d’informations, consultez [commentaires client pour SQL Server sur Linux--sql-server-linux-customer-feedback.md).

**<a id="lcid"></a>Modifier les paramètres régionaux de SQL Server**


Le **language.lcid** définition modifie les paramètres régionaux de SQL Server à un identificateur de langue prise en charge (LCID).

1. L’exemple suivant modifie les paramètres régionaux à Français (1036) :

```
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
```

1. Redémarrez le service SQL Server pour appliquer les modifications :

```
   sudo systemctl restart mssql-server
```

**<a id="memorylimit"></a>Définir la limite de mémoire**


Le **memory.memorylimitmb** définition des contrôles la quantité mémoire physique (en Mo) disponible pour SQL Server. La valeur par défaut est 80 % de la mémoire physique.

1. Exécutez le script mssql-conf en tant que racine avec le **définir** commande **memory.memorylimitmb**. L’exemple suivant modifie la mémoire disponible pour SQL Server à 3,25 Go (3328 Mo).

```
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
```

1. Redémarrez le service SQL Server pour appliquer les modifications :



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-customer-feedback-for-sql-server-on-linuxsql-server-linux-customer-feedbackmd"></a>4. &nbsp;[Feedback client pour SQL Server sur Linux](sql-server-linux-customer-feedback.md)

*Mise à jour : 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3) | [suivant](#TitleNum_5))

<!-- Source markdown line 104.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9d8122e864804004d91f6b7c5c3d24c4a4114d34 7316ef831c390a854c324f23a02c3fb6005e2fea  (PR=2948  ,  Filename=sql-server-linux-customer-feedback.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->




**Sur Docker**

Pour activer l’Audit Local sur docker, vous devez disposer Docker [conserver votre data--sql-server-linux-configure-docker.md).

1. Le répertoire cible pour les nouveaux journaux d’Audit Local se trouve dans le conteneur. Créer un répertoire cible pour les nouveaux journaux d’Audit Local dans le répertoire de l’hôte sur votre ordinateur. L’exemple suivant crée un nouveau **/audit** active :

```
   sudo mkdir <host directory>/audit
```


1. Ajouter un `mssql.conf` fichier avec les lignes `[telemetry]` et `userrequestedlocalauditdirectory = <host directory>/audit` dans le répertoire de l’hôte :

```
   echo '[telemetry]' >> <host directory>/mssql.conf
```

```
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
```
2. Exécuter l’image de conteneur
```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

**Étapes suivantes**





&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restoresql-server-linux-migrate-restore-databasemd"></a>5. &nbsp;[Migrer une base de données SQL Server à partir de Windows et Linux à l’aide de la sauvegarde et restauration](sql-server-linux-migrate-restore-database.md)

*Mise à jour : 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_4) | [suivant](#TitleNum_6))

<!-- Source markdown line 30.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e78f5516a46eab834f644979d3e1c0ca415fabcd 6b03a01385078290b9f451ac013b628f53e0e8b4  (PR=2948  ,  Filename=sql-server-linux-migrate-restore-database.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



* Ordinateur Windows avec les éléments suivants :
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) installé.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) installé.
  * Base de données cible à migrer.

* Ordinateur Linux avec les éléments suivants :
  * SQL Server 2017 RC2. Consultez les Démarrages rapides d’installation pour [RHEL--quickstart-install-connect-red-hat.md), [SLES : démarrage rapide-install-se connecter-suse.md) ou [Ubuntu : démarrage rapide-install-se connecter-ubuntu.md).
  * SQL Server 2017 RC2 [tools--sql-server-linux-setup-tools.md de ligne de commande).

**Créer une sauvegarde sur Windows**


Il existe plusieurs façons de créer un fichier de sauvegarde de base de données sur Windows. Les étapes suivantes utilisent SQL Server Management Studio (SSMS).

1. Démarrer **SQL Server Management Studio** sur votre ordinateur Windows.

1. Dans la boîte de dialogue de connexion, entrez **localhost**.

1. Dans l’Explorateur d’objets, développez **bases de données**.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>6. &nbsp;[Notes de publication pour 2017 du serveur SQL sur Linux](sql-server-linux-release-notes.md)

*Mise à jour : 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_5) | [suivant](#TitleNum_7))

<!-- Source markdown line 31.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4c8b9876f4792782314ba2f9b246405fb8036f84 acb97cf0a2e0bdd039575eaab9c41003316cbb02  (PR=2939  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



**<a id="RC2"></a>RC2 (2017 août)**


La version du moteur SQL Server pour cette version est 14.0.900.75.

**Plateformes prises en charge**


| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Bureau, serveur et station de travail Red Hat Enterprise Linux 7.3 | XFS ou EXT4 | [Guide--quickstart-install-connect-red-hat.md d’installation) |
| Serveur Linux SUSE Enterprise SP2 v12 | EXT4 | [Guide d’installation : démarrage rapide-install-se connecter-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guide d’installation : démarrage rapide-install-se connecter-ubuntu.md) |
| Moteur docker 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation : démarrage rapide-install-se connecter-docker.md) |

> [!NOTE]
> Vous devez au moins 3,25 Go de mémoire pour exécuter SQL Server sur Linux.
> Moteur SQL Server a été testé jusqu'à 1,5 To de mémoire pour l’instant.

**Détails du package**


Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes dans les guides d’installation suivantes :

- [Installer SQL Server--sql-server-linux-setup.md)
- [Install package--sql-server-linux-setup-full-text-search.md de recherche en texte intégral)
- [Installer l’Agent SQL Server package--sql-server-linux-setup-sql-agent.md)

| Package | version du package | Téléchargements |
|-----|-----|-----|
| Rpm de Red Hat | 14.0.900.75-1 | [Moteur le package RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Rpm de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Rpm de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Package de SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) |



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7. &nbsp;[Aide à l’installation de SQL Server sur Linux](sql-server-linux-setup.md)

*Mise à jour : 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_6) | [suivant](#TitleNum_8))

<!-- Source markdown line 70.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00394e1733568a55243788d828968ff9b58a3c99 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880  (PR=2971  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=303d3b74da3fe370d19b7602c0e11e67b63191e7) -->



**<a id="rollback"></a>Restauration SQL Server**


Pour restaurer ou rétrograder SQL Server vers une version précédente, procédez comme suit :

1. Identifiez le numéro de version pour le package de SQL Server que vous souhaitez rétrograder. Pour obtenir la liste de nombres de package, consultez [notes--sql-server-linux-release-notes.md de mise en production).

1. Passer à une version antérieure de SQL Server. Dans les commandes suivantes, remplacez `<version_number>` avec le numéro de version SQL Server que vous avez identifié à l’étape 1.

   | Plateforme | Commandes de mise à jour de package |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Il est uniquement pris en charge pour mettre à niveau vers une version au sein de la même version principale, telles que SQL Server 2017.

> [!IMPORTANT]
> Vers une version antérieure est uniquement prise en charge entre RC2 et RC1 pour l’instant.




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-install-sql-server-integration-services-ssis-on-linuxsql-server-linux-setup-ssismd"></a>8. &nbsp;[Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)

*Mise à jour : 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_7))

<!-- Source markdown line 66.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a3fecd2553d1b25406445b8a26b22c9015dd98fe f836d560513fef1217e7dbce0ab85f78eec6f937  (PR=2948  ,  Filename=sql-server-linux-setup-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



Si vous avez déjà `mssql-server-is` installé, vous pouvez mettre à jour vers la dernière version avec la commande suivante :

```
sudo apt-get install mssql-server-is
```


Pour supprimer `mssql-server-is`, vous pouvez exécuter de commande suivante :
```
sudo apt-get remove msssql-server-is
```



**<a name="RHEL"></a>Installer SSIS sur RHEL**

Pour installer le `mssql-server-is` le package sur RHEL, procédez comme suit :


1.  Activer le mode de super utilisateur.

```
    sudo su
```


2.  Téléchargez le fichier de configuration de Microsoft SQL Server Red Hat référentiel.

```
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
```


3.  Quitter le mode Super utilisateur.

```
    exit
```


4.  Exécutez les commandes suivantes pour installer SQL Server Integration Services.

```
    sudo yum install -y mssql-server-is
```


5.  Après l’installation, exécutez `ssis-conf`.







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section répertorie les articles très similaires pour les articles récemment mis à jour dans les autres domaines au sein de notre référentiel GitHub.com public : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (3 + 12) : **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (5 + 0) : **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (5 + 1) : **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (19 + 82) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (1 + 8) : **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (12 + 1) : **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (0 + 1) : **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (7 + 1) : **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (1 + 1) : **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (0 + 2) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveau + mis à jour (1 + 4) : **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (4 + 1) : **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)
- [Nouveau + mis à jour (0 + 1) : **Tools pour SQL** documents](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveau + mis à jour (0 0 +) : **Analysis Services pour SQL** documents](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveau + mis à jour (0 0 +) : **Master Data Services (MDS) pour SQL** documents](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



