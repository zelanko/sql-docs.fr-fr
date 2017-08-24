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
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 13c237af359c543f6a99a0fce101af81b5eb2bcf
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nouveau et récemment mis à jour : SQL Server sur Linux docs

Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-05-23** &nbsp; - à - &nbsp; **2017-07-17**
- *Zone de sujet :* &nbsp; **Microsoft SQL Server sur Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux Articles vient d’être créés

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Exécuter l’image de SQL Server 2017 conteneur avec Docker](quickstart-install-connect-docker.md)
2. [Installer SQL Server et de créer une base de données sur Red Hat](quickstart-install-connect-red-hat.md)
3. [Installer SQL Server et de créer une base de données sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
4. [Installer SQL Server et de créer une base de données sur Ubuntu](quickstart-install-connect-ubuntu.md)
5. [Exemple : Script d’installation sans assistance de SQL Server pour Red Hat Enterprise Linux](sample-unattended-install-redhat.md)
6. [Exemple : Script d’installation sans assistance de SQL Server pour SUSE Linux Enterprise Server](sample-unattended-install-suse.md)
7. [Exemple : Script d’installation sans assistance de SQL Server pour Ubuntu](sample-unattended-install-ubuntu.md)
8. [Authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md)
9. [Haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md)
10. [Configurer SQL Server 2017 les images de conteneur sur Docker](sql-server-linux-configure-docker.md)
11. [Commentaires client pour SQL Server sur Linux](sql-server-linux-customer-feedback.md)
12. [Chiffrement des connexions à SQL Server sur Linux](sql-server-linux-encrypted-connections.md)
13. [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriées dans la section extraits.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-sles-cluster-for-sql-server-availability-groupsql-server-linux-availability-group-cluster-slesmd"></a>1. &nbsp;[Configurer SLES Cluster pour le groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-sles.md)

*Updated: 2017-06-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 189.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f8d28af253be1dc67615f1ea04135b2f6dff3b71 8be07deddcf0c348d75bf5b4f44615c2383e0722  (PR=2150  ,  Filename=sql-server-linux-availability-group-cluster-sles.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=6dccaff93a6c8b2374a1fad069b2f597898802fc) -->



**Définissez la propriété cluster start-échec-est-irrécupérable false**


`Start-failure-is-fatal`Indique si un échec pour démarrer une ressource sur un nœud empêche d’autres tentatives de démarrage sur ce nœud. Lorsque la valeur `false`, le cluster décide s’il faut essayer de démarrer sur le même nœud en fonction d’actuelle count et migration seuil d’échec la ressource. Par conséquent, une fois le basculement se produit, STIMULATEUR va tenter de démarrage de la ressource de groupe de disponibilité sur l’ancien principal une fois que l’instance SQL est disponible. STIMULATEUR s’occupe de rétrograder le réplica secondaire, et il rejoindra automatiquement le groupe de disponibilité. En outre, si `start-failure-is-fatal` a la valeur `false`, le cluster revient aux limites configurées failcount configurés avec le seuil de la migration, par conséquent, vous devez vous assurer par défaut pour le seuil de migration est mis à jour en conséquence.

Pour mettre à jour la valeur de propriété d’exécution false :
```
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
Si la propriété a la valeur par défaut `true`, si la première tentative de démarrage de la ressource échoue, l’intervention de l’utilisateur est requis après un basculement automatique pour nettoyer le nombre d’échecs de ressources et réinitialiser la configuration à l’aide de : `sudo crm resource cleanup <resourceName>` commande.

Pour plus d’informations sur les propriétés du cluster STIMULATEUR, consultez [configuration des ressources de Cluster](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

**Configurer la délimitation (STONITH)**

Fournisseurs de cluster STIMULATEUR nécessitent STONITH doit être activée et un appareil de délimitation configuré pour une installation de clusters prises en charge. Lorsque le Gestionnaire de ressources de cluster ne peut pas déterminer l’état d’un nœud ou d’une ressource sur un nœud, délimitation est utilisée pour remettre le cluster à un état connu.
Délimitation de niveau de ressources permet de garantir principalement aucune altération des données en cas de panne en configurant une ressource. Vous pouvez utiliser la délimitation au niveau de la ressource, par exemple, avec DRBD (Distributed répliquées bloc Device) pour marquer le disque sur un nœud comme obsolètes lorsque la liaison de communication s’arrête.




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>2. &nbsp;[Notes de publication pour 2017 du serveur SQL sur Linux](sql-server-linux-release-notes.md)

*Updated: 2017-06-20* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 156.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 684da20f7834000886d7a93f83563c55dc3cf9a6 8597bcde7e5754bb7f38de1ec980027245dac6e5  (PR=2115  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=424a23fd98876db808b91f017e7acbcb5b4daa45) -->



**SQL Server Integration Services (SSIS)**

Vous pouvez exécuter des packages SSIS sur Linux. Pour plus d’informations, consultez la [annonce de billet de blog SSIS prise en charge de Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Veuillez noter les problèmes connus suivants avec cette version.

- Le **mssql server est** package est uniquement pris en charge sur Ubuntu pour l’instant.

- Les fonctionnalités suivantes ne sont pas prises en charge lors de l’exécution des packages SSIS sur Linux :
  - Catalogue SSIS DB
  - Planifier l’exécution de Packages par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Pilotes ODBC de tiers
  - Gestionnaire de connexions ODBC, Source et Destination (pris en charge avec SSIS lors de l’actualisation de Linux CTP 2.1)
  - Capture de données modifiées (CDC)
  - Montée en puissance parallèle
  - Feature Pack Azure
  - Hadoop et HDFS Support
  - Microsoft Connector pour SAP BW

SSIS lors de l’actualisation de Linux CTP 2.1, vos packages SSIS permet les connexions ODBC sur Linux. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Articles similaires

Cette section répertorie les articles très similaires pour les articles récemment mis à jour dans d’autres zones de sujet, dans le même référentiel GitHub.com : [MicrosoftDocs /**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet qui ont des articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (4 + 4) : **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (2 + 0) : **Analysis Services pour SQL** documents](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (1 + 2) : **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (6 + 0) : **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (13 + 2) : **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (1 + 0) : **Master Data Services (MDS) pour SQL** documents](../master-data-services/new-updated-master-data-services.md)
- [Nouveau + mis à jour (1 + 0) : **ODBC (Open Database Connectivity) pour SQL** documents](../odbc/new-updated-odbc.md)
- [Nouveau + mis à jour (8 + 4) : **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (2 + 2) : **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (1 + 0) : **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)
- [Nouveau + mis à jour (1 + 0) : **Tools pour SQL** documents](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet qui ne présentent aucuns articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (0 0 +) : **ActiveX Data Objects (ADO) pour SQL** documents](../ado/new-updated-ado.md)
- [Nouveau + mis à jour (0 0 +) : **Data Quality Services pour SQL** documents](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveau + mis à jour (0 0 +) : **Extensions DMX (Data Mining) pour SQL** documents](../dmx/new-updated-dmx.md)
- [Nouveau + mis à jour (0 0 +) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (0 0 +) : **MDX (Multidimensional Expressions) pour SQL** documents](../mdx/new-updated-mdx.md)
- [Nouveau + mis à jour (0 0 +) : **PowerShell pour SQL** documents](../powershell/new-updated-powershell.md)
- [Nouveau + mis à jour (0 0 +) : **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (0 0 +) : **exemples pour SQL** documents](../sample/new-updated-sample.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveau + mis à jour (0 0 +) : **XQuery pour SQL** documents](../xquery/new-updated-xquery.md)


&nbsp;


