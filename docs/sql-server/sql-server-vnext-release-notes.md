---
title: "Notes de publication de SQL Server VNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/12/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: "craigg-msft"
ms.author: "craigg"
manager: "jhubbard"
caps.handback.revision: 39
---
# Notes de publication de SQL Server VNext
Cette rubrique décrit les limitations et les problèmes de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

- Pour connaître les nouveautés dans cette version, consultez [Nouveautés de SQL Server vNext](../sql-server/what-s-new-in-sql-server-vnext.md).
- Les [Notes de publication de SQL Server sur Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes) sont publiées sur notre nouvelle plateforme de documentation.
- Des [Notes de publication de SQL Server Reporting Services](../reporting-services/notes-de-publication-sur-reporting-services.md) sont publiées dans la section Reporting Services.

 **Essayez-le :**    
   -   [![Télécharger à partir du Centre d’évaluation](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) Télécharger [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] à partir du **[Centre d’évaluation](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="sql-server-vnext-ctp-13-february--2017"></a>SQL Server vNext CTP 1.3 (février 2017)
### <a name="supported-installation-scenarios-ctp-13"></a>Scénarios d’installation pris en charge (CTP 1.3)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est destiné à une version d’évaluation uniquement.  Les déploiements de production ne sont pas pris en charge. Nous vous recommandons d’installer et de tester [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] sur une machine virtuelle.

### <a name="documentation-ctp-13"></a>Documentation (CTP 1.3)
- **Problème et impact sur le client :** la documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-integration-services-ssis-ctp-13"></a>SQL Server Integration Services (SSIS) (CTP 1.3)
#### <a name="cdc-components-not-supported-in-this-ctp-release"></a>Composants CDC non pris en charge dans cette version CTP
-   **Problème et impact sur le client** : la tâche de contrôle CDC, la source CDC et le séparateur CDC ne sont pas pris en charge dans cette version CTP.
-   **Solution de contournement :** Il n’existe aucune solution de contournement.


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-12-january--2017"></a>SQL Server vNext CTP 1.2 (janvier 2017)
### <a name="supported-installation-scenarios-ctp-12"></a>Scénarios d’installation pris en charge (CTP 1.2)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est destiné à une version d’évaluation uniquement.  Les déploiements de production ne sont pas pris en charge. Nous vous recommandons d’installer et de tester [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] sur une machine virtuelle.

### <a name="sql-server-database-engine-ctp-12"></a>Moteur de base de données SQL Server (CTP 1.2)
- **Problème et impact sur le client :** dans certains cas, le service MSSQLSERVER se bloque à l’état « Démarrage ».
- **Solution de contournement :** pour contourner ce problème :
  -  Créez une dépendance entre le service `mssqlserver` et le service `keyiso`. Pour ce faire, vous pouvez exécuter la commande suivante à partir d’une invite de commandes avec élévation de privilèges : `sc config mssqlserver depend= keyiso`
  - Redémarrez l'ordinateur.

### <a name="documentation-ctp-12"></a>Documentation (CTP 1.2)
- **Problème et impact sur le client :** La documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à :**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
 
### <a name="sql-server-integration-services-ssis-ctp-12"></a>SQL Server Integration Services (SSIS) (CTP 1.2)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>La suppression de catalogue SSIS peut échouer quand SSIS Scale Out est installé
**Problème et impact sur le client :** quand la fonctionnalité SSIS Scale Out est installée sur un ordinateur, la suppression de la base de données du catalogue SSISDB peut échouer avec l’erreur suivante : « Impossible de supprimer la connexion *“connexion”*, tant que l’utilisateur est connecté.
   
**Solution de contournement** :
-   Sur les ordinateurs Scale Out Master, exécutez la commande « services.msc » pour ouvrir la fenêtre Services. Arrêtez le service SQL Server Integration Services Cluster Master.
-   Sur les ordinateurs Scale Out Worker, qui se connectent au maître, exécutez la commande « services.msc » pour ouvrir la fenêtre Services. Arrêtez le service SQL Server Integration Services Cluster Worker.

Vous pouvez à présent supprimer la base de données de catalogue SSISDB.

### <a name="sql-server-master-data-services-ctp-12"></a>SQL Server Master Data Services (CTP 1.2)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Une transaction peut échouer quand le type de journal de transactions d’entités a la valeur Attribut
**Problème et impact sur le client :** Quand le type de journal de transactions d’entités a la valeur **Attribut** dans [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (la valeur par défaut est **Membre**), les scénarios suivants échouent :

* Les transactions liées aux changements d’entités ne sont pas affichées dans le site web.
* Impossible d’ouvrir la page **Transactions** dans le site web et d’inverser une transaction.
* Impossible de mettre à jour une entité avec une annotation de transaction dans le site web.

**Solution de contournement :** Il n’existe aucune solution de contournement.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>L’action Copier la version peut ne pas fonctionner quand **Copier uniquement les versions activées** a la valeur False
-  **Problème et impact sur le client :** Quand le paramètre **Copier uniquement les versions activées** a la valeur **Non** (la valeur par défaut est **Oui**), l’opération de copie de version peut échouer. Aucun message d’erreur n’est affiché.
-  **Solution de contournement :** Il n’existe aucune solution de contournement.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-11-december--2016"></a>SQL Server vNext CTP 1.1 (décembre 2016)
### <a name="supported-installation-scenarios-ctp-11"></a>Scénarios d’installation pris en charge (CTP 1.1)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est destiné à une version d’évaluation uniquement.  Les déploiements de production ne sont pas pris en charge. Nous vous recommandons d’installer et de tester [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] sur une machine virtuelle.

Même si les scénarios suivants peuvent fonctionner pour vous, ils n’ont pas été testés rigoureusement et ne sont **pas** pris en charge dans [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] :
- Désinstallation de CTP 1.1.
- Installation côte à côte avec d’autres versions de SQL Server.
- Mise à niveau à partir des versions précédentes de SQL Server.
- Aucun composant de Feature Pack SQL Server n’est disponible dans le cadre de l’installation de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="documentation-ctp-11"></a>Documentation (CTP 1.1)
- **Problème et impact sur le client :** la documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à :**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-master-data-services-ctp-11"></a>SQL Server Master Data Services (CTP 1.1)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Une transaction peut échouer quand le type de journal de transactions d’entités a la valeur Attribut
**Problème et impact sur le client :** Quand le type de journal de transactions d’entités a la valeur **Attribut** dans [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (la valeur par défaut est **Membre**), les scénarios suivants échouent :

* Les transactions liées aux changements d’entités ne sont pas affichées dans le site web.
* Impossible d’ouvrir la page **Transactions** dans le site web et d’inverser une transaction.
* Impossible de mettre à jour une entité avec une annotation de transaction dans le site web.

**Solution de contournement :** Il n’existe aucune solution de contournement.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>L’action Copier la version peut ne pas fonctionner quand **Copier uniquement les versions activées** a la valeur False
-  **Problème et impact sur le client :** Quand le paramètre **Copier uniquement les versions activées** a la valeur **Non** (la valeur par défaut est **Oui**), l’opération de copie de version peut échouer. Aucun message d’erreur n’est affiché.
-  **Solution de contournement :** Il n’existe aucune solution de contournement.

### <a name="sql-server-integration-services-ssis-ctp-11"></a>SQL Server Integration Services (SSIS) (CTP 1.1)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>La suppression de catalogue SSIS peut échouer quand SSIS Scale Out est installé
**Problème et impact sur le client :** quand la fonctionnalité SSIS Scale Out est installée sur un ordinateur, la suppression de la base de données du catalogue SSISDB peut échouer avec l’erreur suivante : « Impossible de supprimer la connexion *“connexion”*, tant que l’utilisateur est connecté.
   
**Solution de contournement** :
-   Sur les ordinateurs Scale Out Master, exécutez la commande « services.msc » pour ouvrir la fenêtre Services. Arrêtez le service SQL Server Integration Services Cluster Master.
-   Sur les ordinateurs Scale Out Worker, qui se connectent au maître, exécutez la commande « services.msc » pour ouvrir la fenêtre Services. Arrêtez le service SQL Server Integration Services Cluster Worker.

Vous pouvez à présent supprimer la base de données de catalogue SSISDB.

#### <a name="odbc-components-are-not-supported-in-this-ctp-release"></a>Les composants ODBC ne sont pas pris en charge dans cette version CTP
**Problème et impact sur le client** : le Gestionnaire de connexions ODBC, la source et la destination ne sont pas pris en charge dans cette version CTP.

**Solution de contournement :** Il n’existe aucune solution de contournement.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-10-november-2016"></a>SQL Server vNext CTP 1.0 (novembre 2016)
### <a name="supported-installation-scenarios-ctp10"></a>Scénarios d’installation pris en charge (CTP1.0)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est destiné à une version d’évaluation uniquement.  Les déploiements de production ne sont pas pris en charge. Nous vous recommandons d’installer et de tester [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] sur une machine virtuelle.

Même si les scénarios suivants peuvent fonctionner pour vous, ils n’ont pas été testés rigoureusement et ne sont **pas** pris en charge dans [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] :
- Désinstallation de CTP 1.0.
- Installation côte à côte avec d’autres versions de SQL Server.
- Mise à niveau à partir des versions précédentes de SQL Server.
- Aucun composant de Feature Pack SQL Server n’est disponible dans le cadre de l’installation de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="documentation-ctp-10"></a>Documentation (CTP 1.0)
- **Problème et impact sur le client :** La documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)].  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à : **. 
- **Problème et impact sur le client :** Aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-database-engine-ctp-10"></a>Moteur de base de données SQL Server (CTP 1.0)
-  **Problème et impact sur le client :** La fonction `STRING_AGG` dans CTP1 retourne le type LOB comme résultat (par exemple, `NVARCHAR(MAX)`). Dans une version CTP ultérieure, ce comportement pourra changer et `STRING_AGG` pourra retourner `NVARCHAR(4000)` si les valeurs d’entrée ne sont pas des types LOB. Une erreur de dépassement peut être levée si les résultats concaténés ne rentrent pas dans `NVARCHAR(4000)`.

-  **Problème et impact sur le client :** Évitez d’utiliser des mots-clés non réservés (tels que `WITHIN`) comme alias pour les expressions `STRING_AGG`. (Par exemple `SELECT Company.Name, STRING_AGG(Product.Name, ',') AS WITHIN FROM TableA;`.) Dans une version CTP ultérieure, le jeton `WITHIN` après l’appel `STRING_AGG` pourra être utilisé dans le cadre de la fonction `STRING_AGG`.

-  **Solution de contournement :** Évitez d’utiliser des alias `WITHIN` ou ajoutez `AS WITHIN` comme spécification d’alias pour éviter les collisions avec les modifications ultérieures qui pourraient être ajoutées dans la fonction `STRING_AGG`.


### <a name="sql-server-integration-services-ctp-10"></a>SQL Server Integration Services (CTP 1.0)
#### <a name="stop-operation-in-ssis-catalog-may-fail"></a>L’action Arrêter l’opération dans le catalogue SSIS peut échouer
**Problème et impact sur le client :** L’arrêt d’une opération dans [!INCLUDE[ssIS_md](../includes/ssis-md.md)] à l’aide de [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)] ou de la procédure stockée catalog.stop_operation peut échouer avec l’erreur suivante : « Une erreur .NET Framework s’est produite au cours de l’exécution de la routine ou de la fonction d’agrégation définie par l’utilisateur ’stop_operation_internal’ ».

-  **Solution de contournement :** Ouvrez le Gestionnaire des tâches Windows. Sous l’onglet **Processus**, recherchez le processus nommé **ISServerExec** et cliquez sur **Fin de tâche** pour l’arrêter.

#### <a name="create-dump-of-ssis-pacakge-execution-may-fail"></a>La création de fichier de vidage d’exécution de package SSIS peut échouer
**Problème et impact sur le client :** La création d’un vidage pour l’exécution d’un package à l’aide de la procédure stockée catalog.create_execution_dump peut échouer avec l’erreur suivante : « Une erreur .NET Framework s’est produite au cours de l’exécution de la routine ou de la fonction d’agrégation définie par l’utilisateur ’create_execution_dump_internal’ ».

-  **Solution de contournement :** Ouvrez le Gestionnaire des tâches Windows. Sous l’onglet **Processus**, recherchez le processus nommé **ISServerExec**, cliquez dessus avec le bouton droit, puis cliquez sur **Créer un fichier de vidage**.

#### <a name="get-perf-counter-of-ssis-package-execution-may-fail"></a>L’obtention de compteur de performances d’exécution de package SSIS peut échouer
**Problème et impact sur le client :** L’interrogation des compteurs de performances [!INCLUDE[ssIS_md](../includes/ssis-md.md)] à l’aide de la fonction table catalog.dm_execution_performance_counters peut échouer avec l’erreur suivante : « Une erreur .NET Framework s’est produite au cours de l’exécution de la routine ou de la fonction d’agrégation ’get_execution_perf_counters’ ».

-  **Solution de contournement** : Utilisez l’Analyseur de performances Windows pour analyser directement les valeurs des compteurs de performances. Il n’existe aucune solution de contournement pour les compteurs de performances pour une exécution de package spécifique.

#### <a name="deleting-catalog-may-fail-when-ssis-scale-out-master-is-installed"></a>La suppression de catalogue peut échouer quand SSIS Scale Out Master est installé
**Problème et impact sur le client :** Quand la fonctionnalité [!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out est installée sur un ordinateur, la suppression du catalogue **SSISDB** peut échouer avec l’erreur suivante : « Impossible de supprimer la connexion « … », car l’utilisateur est actuellement connecté. 

**Solution de contournement** : 
* Sur un ordinateur Scale Out Master, exécutez la commande « services.msc » pour ouvrir la fenêtre **Services** et arrêtez le service **SQL Server Integration Services Cluster Master**. 

* Sur les ordinateurs Scale Out Worker, qui se connectent au maître, exécutez la commande « services.msc » pour ouvrir la fenêtre **Services**. Arrêtez le service **SQL Server Integration Services Cluster Worker**. 

Vous devriez maintenant pouvoir supprimer le catalogue **SSISDB**.

#### <a name="odbc-connector-in-ssis-is-not-supported"></a>Le connecteur ODBC dans SSIS n’est pas pris en charge
-  **Problème et impact sur le client :** Le connecteur ODCB dans [!INCLUDE[ssIS_md](../includes/ssis-md.md)] n’est pas pris en charge.
-  **Solution de contournement :** Il n’existe aucune solution de contournement.

### <a name="sql-server-reporting-services-ctp-10"></a>SQL Server Reporting Services (CTP 1.0)

[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ne contient aucune nouvelle fonctionnalité pour SQL Server Reporting Services.

### <a name="sql-server-master-data-services-ctp-10"></a>SQL Server Master Data Services (CTP 1.0)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Une transaction peut échouer quand le type de journal de transactions d’entités a la valeur Attribut
**Problème et impact sur le client :** Quand le type de journal de transactions d’entités a la valeur **Attribut** dans [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (la valeur par défaut est **Membre**), les scénarios suivants échouent :

* Les transactions liées aux changements d’entités ne sont pas affichées dans le site web.
* Impossible d’ouvrir la page **Transactions** dans le site web et d’inverser une transaction.
* Impossible de mettre à jour une entité avec une annotation de transaction dans le site web.

**Solution de contournement :** Il n’existe aucune solution de contournement.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>L’action Copier la version peut ne pas fonctionner quand **Copier uniquement les versions activées** a la valeur False
**Problème et impact sur le client :** Quand le paramètre **Copier uniquement les versions activées** a la valeur **Non** (la valeur par défaut est **Oui**), l’opération de copie de version peut échouer. Aucun message d’erreur n’est affiché.

**Solution de contournement :** Il n’existe aucune solution de contournement.
 
### <a name="sql-server-management-studio-ssms-ctp-10"></a>SQL Server Management Studio (SSMS) (CTP 1.0)
SQL Server Management Studio est un téléchargement distinct.  Pour plus d’informations, consultez [SQL Server Management Studio - Notes de publication](https://msdn.microsoft.com/library/mt238486.aspx).

##  <a name="infotipimageshiproominfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Contacter l’équipe d’ingénierie de SQL Server 
- [Dépassement de la capacité de la pile (balise sql-server) : poser des questions techniques](http://stackoverflow.com/questions/tagged/sql-server)
- [Forums MSDN : poser des questions techniques](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect : signaler des bogues et demander des fonctionnalités](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit : discussion générale sur R](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
